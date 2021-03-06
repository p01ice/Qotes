# TODO

## 说明

由于备案是个人备案，所以目前的方案为注册即可编辑卡片，但是不能浏览别人的卡片，评论的功能从一开始就没打算做所以没有也是应该的。

- 卡片的层级关系
  - ~~卡片页面的侧边栏竖三栏显示父-子-同辈~~
  - ~~这样就有理由做成静态的，单击直接跳转~~
  - ~~不然交互不方便，单击会被展开子卡片功能占据~~
  - ~~通过拖动把卡片移入另一个卡片~~
  - ~~只要是有多个卡片出现的场景，就应该允许拖动~~
  - ~~多个卡片一起出现应该做成瀑布流的效果不然太丑~~
  - ~~只要是有多个卡片出现的场景，就应该是瀑布流~~
  - ~~瀑布流的分页和懒加载~~
  - 实际还是先用了简单的分页先不做懒加载

- 侧边栏目录(单独拿出来记一下，想到事情再补充)

- 卡片的显示问题
  - ~~自动生成标题和概览~~
  - ~~beautifulsoup改成lxml~~
  - ~~还是用了BS因为要改某些标签属性~~
  - 最好做成标签页，~~可以看完整内容~~
  - ~~也可以只看二级标题结构，兄弟卡片一起对比出现~~
  - ~~查看完整内容时候加入编辑功能~~
  - ~~最好是点击内容直接在页面上编辑~~
  - ~~因为要支持页面内编辑，所以卡片的内容包括h1标题~~
  - ~~既然这样卡片的标题栏应该做得不那么醒目~~
  - ~~代码高亮，至少得比简书强~~

- ~~卡片的修改问题~~
  - ~~文档修改时间记录(只记最近一次)~~
  - ~~simplemde修改模式待完成~~
  - ~~需要有快捷方式把卡片移到上一级目录或者删除~~
  - 修改的自动保存是否必要，不然或许需要一个临时缓存版本temp
  - ~~修改的权限问题，差点忘了~~
  - ~~只有作者有权限修改，所以浏览其他人的卡片不触发编辑~~
  - ~~卡片的内容长度限制(定在10000字符吧，不希望用户像我一样废话)~~

- 卡片的权限问题
  - 除了编辑以外，计划中应该有私密卡片private

- ~~快速新建卡片~~
  - ~~快捷编辑器~~，找到了一个markdownime
  - ~~及时转义~~
  - ~~安全性不足~~，找到了一篇博客限制粘贴功能
  - ~~而且每次生成卡片内容都会清洗html~~
  - 图片的问题，打算专门弄个数据库/服务器存图片
  - 直接支持外链不安全，目前先把功能打开不管那么多
  - ~~markdownime的原因造成会有多余的`\n`和`<br>`~~

- ~~功能完善的更友好的markdown编辑器~~
  - ~~flask_pagedown~~过于简洁放弃
  - ~~上面这个对代码不友好~~
  - ~~找到一个simplemde,简直完美~~
  - ~~jinja2传递字符串会自动转义很麻烦~~
  - ~~所以暂时不能用来修改卡片，但希望能完成这个功能~~
  - ~~等写完API再来处理这个问题吧，应该不难~~
  - 已经部分解决，API完成后希望有更优雅的解决方式

- 标签tags
  - 标签与卡片其实可以独立开来
  - 目前还在考虑要不要单独做一个标签collection
  - 自动将卡片的tag数关联到用户身上
  - tag的链接应该是该卡片作者的相同标签的所有卡片
  - 这样可以省不少事情，其他相关卡片可以放在页面下面

- 搜索
  - 主要通过导航栏搜索，包括扩展性的搜索
  - 直接搜索可以加入markdown语法
    - 比如说 `# title`就是搜索标题包含title的卡片
    - 比如说 `## gist`就是二级标题包含gist的卡片
    - 比如说 `* tag`就是有tag标签的卡片
  - 正则式匹配
  - 专门的搜索结果页面，侧边栏详细的搜索设置

- ~~一次性书签~~
  - ~~大概就是如果没存地址，点击一次存当前地址~~
  - ~~否则跳转到存了的地址(prompt提示)~~
  - ~~没有用弹框提示，用CSS格式用显目的颜色提示了~~

- ~~新手指引beginner~~
  - ~~用卡片来指引就行了~~
  - ~~大概就是使用技巧/使用规范/使用实例三张卡片吧~~
  - 可能需要各种链接

- ~~mongoengine改成pymongo~~(或者自己写一个，感觉都不是很好用)
  - ~~pymongo直接用挺方便的~~(也有逻辑不清晰的地方)
  - ~~哇，没有抽象层是真的难受。我想重新写一个了~~
  - ~~把Card的抽象层重新写了一遍，但又觉得用处不大~~
  - 试试看写API的时候是不是对这个的依赖性比较大
  - ~~否则就不改了，不然要改把User也一起改了~~
  - ~~已经改得差不多了，models文件已经太长了~~

- ~~bootstrap自定义表单格式/原生wtforms直接渲染~~

- 用户头像(又是图片的问题)

- ~~主页右上角直接登录不跳转~~
  - ~~登录后右上角变成个人主页的链接~~
  - 本来应该显示头像的，但是和图片相关的问题都搁置了
  - ~~除了主页以外其他页面必须跳转登录~~
  - ~~这么做主要是为了简化表单~~
  - 那么可能登录页面需要记录args from来302转回

- 关注用户

- 引用卡片quote
  - 每张卡片只能有一个父卡片
  - 可以通过引用的方式“复制”卡片，完成一张卡片多处使用
  - 卡片应该显示被引用次数
  - 被引用次数如果没有就隐藏吧，无关紧要的功能别占位置了
  - 要是被引用的卡片被删除了怎么办？
    - 一起删除引用它的卡片
    - 或者保留引用它的卡片
    - ~~还没想好用哪种，也不想让用户选~~
    - 还是让删除卡片的人选吧

- git/dropbox至少要有一个同步的方式
  - 估计要很久以后再做了，难度有点大
  - 目前设想为用git同步
  - 简单设想为除了`.md`文件全部ignore(图片怎么办呢)
  - 监视gitlog即可完成同步
  - 这带来一个问题，一旦错了就很难改过来，非常难受
  - 但是暂时想不出更好的方法

- 图片相关
  - 图片的自适应大小
  - ~~max-width 100%~~
  - 居中
  - CDN or local or 挖墙脚
