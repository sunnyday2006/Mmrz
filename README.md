# Mmrz

-----

## 简介:
Mmrz 是 Memorize 的缩写. 主要就是为了帮助记忆**日语**单词, 当然英语法语西班牙语随便什么语单词也可以, 只是有可能不那么适用而已. 以前用有道单词本背英语单词的时候效率很高, 因为有道单词本根据艾宾浩斯遗忘曲线按时重复让你记忆单词. 后来想背日语单词却苦于没有类似的工具能达成类似的效果(反正试了一些都不太满意).

工欲善其事, 必先利其器. 趁着学习 Ruby 语法索性撸了一个小工具同样按照艾宾浩斯遗忘曲线进行复习. 不过因为没有词库, 所以所有单词需要自行手动输入. 但是其实即使有词库也需要手动查找再添加进入单词本, 手动输入无非是多练习输入了一下日语发音而已.

## 演示:
![demo](http://115.29.192.240/mmrz.gif)

## 使用:
`clone`仓库, 然后使用`ruby Mmrz.rb`运行程序. 

## 功能:
主要实现了以下几个功能:

**- add:** 进入`Add mode`, 添加模式. 手动按照`"单词 发音"`(以空格隔开)的格式添加单词到单词本.(发音部分也可以输入任何你想要记忆的东西, 比如单词意思)

**-delete:** 根据`list`功能显示出来的编号删除某个单词. 格式为`delete 3`

**-list:** 显示单词本中的所有单词.

**-mmrz:** 进入`Mmrz mode`, 记忆模式. Mmrz 会根据从单词本中取出所有提醒时间戳小于当前时间的单词, 用于背诵. 背诵过程中首先只显示单词, 隐藏发音或解释. 按[空格键]显示作为隐藏部分的发音或解释, 用户输入`yes`表示记住了, 背诵成功次数+1, 从当前背诵列表删除, 重新计算提醒时间戳, 更新数据库以待下次背诵. 输入`no`, 则不会从当前列表删除, 会在当次取出的单词全部背诵完毕后, 再次背诵, 直到用户选择`yes`, 此时重新计算提醒时间戳, 更新数据库, 不过背诵成功次数并不会+1. 输入`pass`则直接将背诵次数设置为8, 表示该单词已经非常熟悉, 绝对不需要再次背诵了(因为背诵次数不会超过8次).

## 注意:
- 需要使用`Ruby 2.0.0`以上版本.
- 可能需要手动安装`sqlite3`. 使用`gem install sqlite3`.
- 首次运行即会在当前目录下创建`wordbook.db`数据库. 此数据库非常重要, **不可删除**. 否则所有单词记录将完全丢失.



