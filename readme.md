# Match System for Thrift Learning

在这个系统中，有三个节点（功能），它们是完全独立的，可以在同一个服务器上，也可以在不同的服务器上运行。每个节点就是一个进程，可以使用不同的编程语言来实现。

客户端可以通过调用匹配系统的服务接口函数来获取功能，实现跨语言、跨服务的工作。每个节点（功能）之间通过Thrift定义的服务接口进行连接，弧尾所在的节点创建客户端，弧头所在的节点创建服务器。

匹配系统节点实现服务端，包括一个匹配池，它不断接收玩家并删除玩家，同时根据一定规则为每个玩家安排一局游戏。匹配系统节点也实现客户端，通过调用数据存储节点的服务端来获取功能，实现跨语言、跨服务的工作。

数据存储节点实现服务端，其中包括服务接口功能：

- `add_user`: 向匹配池中添加玩家。
- `remove_user`: 从匹配池中删除玩家。
- `save_data`: 将匹配信息存储起来。

![Match System](https://github.com/xxdecade/Match_System/raw/master/img/img0.png)

****
In this system, there are three nodes (functions), which are completely independent and can run on the same server or on different servers. Each node is a process and can be implemented using different programming languages.

The client can obtain functions by calling the service interface function of the matching system to achieve cross-language and cross-service work. Each node (function) is connected through the service interface defined by Thrift. The node where the arc tail is located creates the client, and the node where the arc head is located creates the server.

The matching system node implements the server side, including a matching pool, which continuously receives and deletes players, and arranges a game for each player according to certain rules. The matching system node also implements the client, which obtains functions by calling the server of the data storage node to achieve cross-language and cross-service work.

The data storage node implements the server side, including service interface functions:

- `add_user`: Add a player to the matching pool.
- `remove_user`: Remove a player from the match pool.
- `save_data`: Store matching information.

****
`version--1.0:` 每2个用户进入，就将他们匹配在一起。

`version--2.0:` 按用户的分数排序，差距小于50的匹配在一起。

`version--3.0:` 实现了生产者的多线程。

`version--4.0:` 在2.0的基础上，剩余用户的匹配范围会按照每秒扩展+50的速度扩展进行匹配。
