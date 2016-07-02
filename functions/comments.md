#Comments()


> V1.1.1新增

模板中使用
```php
{:Comments("posts",$object_id)}
<!-- 评论文章表里的某个ID为$object_id的文章-->
```

允许/禁止评论的方法：

1.后台添加文章的模板中：根目录/admin/themes/simplebootx/Portal/AdminPost/add.html
在下面这段代码
```html
<tr>
	<td>
		<label class="radio"><input type="radio" name="post[recommended]" value="1">推荐</label>
		<label class="radio"><input type="radio" name="post[recommended]" value="0" checked>未推荐</label>
	</td>
</tr>
```
之后添加
```html
<tr>
	<td>
		<label class="radio"><input type="radio" name="post[comment_status]" value="1" checked>允许评论</label>
		<label class="radio"><input type="radio" name="post[comment_status]" value="0">禁止评论</label>
	</td>
</tr>
```

2.后台编辑文章的模板中：根目录/admin/themes/simplebootx/Portal/AdminPost/edit.html
(1)在下面这段代码
```php
$recommended_yes=$post['recommended']==1?"checked":"";
$recommended_no=$post['recommended']==0?"checked":"";
```
之后添加
```php
$comment_status_yes=$post['comment_status']==1?"checked":"";
$comment_status_no=$post['comment_status']==0?"checked":""; 
```
(2)在下面这段代码
```html
<tr>
	<td>
		<label class="radio"><input type="radio" name="post[recommended]" value="1" {$recommended_yes}>推荐</label>
		<label class="radio"><input type="radio" name="post[recommended]" value="0" {$recommended_no}>未推荐</label>
	</td>
</tr>
```
之后添加
```html
<tr>
	<td>
		<label class="radio"><input type="radio" name="post[comment_status]" value="1"{$comment_status_yes}>允许评论</label>
		<label class="radio"><input type="radio" name="post[comment_status]" value="0"{$comment_status_no}>禁止评论</label>
	</td>
</tr>
```

3.模板中使用
```php
<eq name="comment_status" value="1">{:Comments("posts",$object_id)}</eq>
<!-- 评论文章表里的某个ID为$object_id的文章-->
```
