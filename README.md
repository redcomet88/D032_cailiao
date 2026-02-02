# D032  材料科学文献知识图谱可视化分析系统（四种知识图谱可视化布局） | vue + flask + echarts + d3.js 实现

> 完整项目收费，可联系QQ: 81040295 微信: mmdsj186011 注明从github来的，谢谢！
也可以关注我的B站： 麦麦大数据 https://space.bilibili.com/1583208775
> 

**关注B站，有好处！
编号:  F032**

## 视频

[video(video-BV3vUa1r-1760775827075)(type-bilibili)(url-https://player.bilibili.com/player.html?aid=922503069)(image-https://i-blog.csdnimg.cn/img_convert/382ab406b8117741a3f3d6bc2d9937c8.jpeg)(title-neo4j 文献知识图谱可视化分析系统 | vue + flask + echarts + d3.js 实现)]

## 1 系统简介
系统简介：本系统是一个基于Vue+Flask构建的材料科学文献知识图谱可视化分析系统，其核心功能围绕文献数据的抓取、分析、可视化和用户管理展开。主要包括：主页模块，用于展示最新文献卡片，方便用户快速了解最新动态；文献搜索功能，支持用户通过关键词或其他条件快速检索文献；数据大屏模块，通过折线图、柱状图、饼图、环图等多种图表形式展示文献数据的统计与分析；关键词分析模块，利用TF-IDF和TextRank算法提取文献关键词并进行分析；词云分析模块，结合Jieba分词和WordCloud组件生成词云，直观呈现关键词分布；知识图谱模块，构建文献间的关系网络，支持搜索功能并通过D3.js进行可视化展示；数据分析模块，提供矩阵图、树形图和关系图三种高级图形，深入分析文献间的关联；以及用户管理模块，包含头像修改、个人信息维护、短信验证码修改密码等功能，确保系统的安全性和个性化体验。
## 2 功能设计
该系统采用典型的B/S（浏览器/服务器）架构模式。用户通过浏览器访问Vue前端界面，该前端由HTML、CSS、JavaScript以及Vue.js生态系统中的Vuex（用于状态管理）、Vue Router（用于路由导航）、ECharts（用于数据可视化）和D3.js（用于复杂图表绘制）等组件构建。前端通过API请求与Flask后端进行数据交互，Flask后端则负责业务逻辑处理，并利用Py2Neo（或类似工具）与Neo4j图数据库进行数据存储和查询。
系统还包含一个独立的爬虫模块，负责从外部来源抓取材料科学领域的文献数据，并通过自然语言处理技术提取文献关键词和关系信息，最终构建知识图谱并存储到Neo4j数据库，为整个系统提供数据支撑。此外，系统的可视化部分通过ECharts和D3.js实现数据的大屏展示和知识图谱的交互式可视化，满足用户对文献数据的多样化分析需求。。
### 2.1系统架构图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/17486666075145a9be250812259682c5.jpeg)
### 2.2 功能模块图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5c180d4b8dff4474952d5be03df39a02.jpeg)
## 3 功能展示
### 3.1 登录 & 注册
登录注册做的是一个可以切换的登录注册界面，点击去登录后者去注册可以切换，背景是一个视频，循环播放。
登录需要验证用户名和密码是否正确，如果**不正确会有错误提示**。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/83e9e902bece4e9a8d8edd1c2a53dd14.png)
注册需要**验证用户名是否存在**，如果错误会有提示。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/131ecb6049a24048936acf8291e33ddf.png)
### 3.2 主页
主页的布局采用了左侧是菜单，右侧是操作面板的布局方法，右侧的上方还有用户的头像和退出按钮，如果是新注册用户，没有头像，这边则不显示，需要在个人设置中上传了头像之后就会显示。

### 3.3 实体搜索 & 性能搜索
材料科学文献中有实体和性能的概念，系统支持从两个方面进行检索
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d5cbe4694f97435190f5152c983c45e4.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/551d871726574949b94ec03719d84267.png)
### 3.4 可视化分析
数据可视化分析方面，可以进行统计数据查看，材料类型发分析：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/f181e5f647a14bfbb243879d652724ed.png)
材料性能的排名分析：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/e1ebbbe3489c4e92979a900aa814b280.png)
### 3.5 文本分析 （关键词提取分析 & 词云分析）
针对文献文本，开发了关键词分析 和 词云分析
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/23d2021fddb2464da3957f43bb19536d.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/62e23b0005414aa6abe0e127b2abc42a.png)
### 3.6 知识图谱构造
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/3cb92301ed384d87819a2f319dfb9e40.png)
在neo4j中的展示：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/45862c9285a0494f9f5e116472b4081a.png)
### 3.7 知识图谱可视化 & 四种可视化布局
知识图谱支持检索，并且支持4种不同的可视化布局，在右侧上方通过按钮可以进行切换。
1.知识图谱网状布局：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/6722d947d6a74c558acfdbd6f608a70e.png)
2.知识图谱矩阵布局：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/3d3522db4c584128b61c73fadc752037.png)
3.知识图谱树状布局：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/164c6e8a0bc44d8eadc0e66fb2591fbf.png)
4.知识图谱关系布局：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/44b6e072b06f4b9097d720c71809c8d3.png)
### 3.6 个人设置
个人设置方面包含了用户信息修改、密码修改功能。
用户信息修改中可以上传头像，完成用户的头像个性化设置，也可以修改用户其他信息。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/54bd28fe88544c6097fa6c8fbc1ccf2a.png)

修改密码需要输入用户旧密码和新密码，验证旧密码成功后，就可以完成密码修改。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/46cdfc3d19bd4a9f80fe5b8bfed2c48e.png)

## 4程序代码
### 4.1 代码说明
代码介绍：以下是一个基于Vue.js和Neo4j实现材料学文献知识图谱可视化的案例。我们将通过Neo4j存储文献数据，并使用Vue.js前端框架进行可视化。
### 4.2 流程图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2c8dd7854eb24f109970e278efeca893.png)
### 4.3 代码实例
```python
<template>
  <div>
    <div id="graph-container"></div>
  </div>
</template>

<script>
import { Driver } from "neo4j-driver";
import { createGraph } from "vis-network/standalone";

export default {
  data() {
    return {
      driver: null,
      graph: null
    };
  },
  mounted() {
    this.initNeo4j();
    this.loadGraph();
  },
  methods: {
    async initNeo4j() {
      // 连接到Neo4j数据库
      this.driver = new Driver("bolt://localhost:7687", "neo4j", "password");
    },

    async loadGraph() {
      // 查询数据并构建图表
      const session = this.driver.session();
      try {
        const result = await session.run(
          "MATCH (p:Paper)-[r]->(n) RETURN p, r, n LIMIT 100"
        );

        const nodes = [];
        const edges = [];

        result.records.forEach(record => {
          const paper = record.get("p").properties;
          const node = record.get("n").properties;
          const relationship = record.get("r").type;

          nodes.push({
            id: paper.title,
            label: paper.title,
            group: "Paper"
          });

          edges.push({
            from: paper.title,
            to: node.name || node.title,
            label: relationship,
            color: relationship === "BELONGS_TO" ? "#2E2EFE" : "#FE2E2E"
          });
        });

        // 创建图表
        const container = document.getElementById("graph-container");
        const data = {
          nodes: nodes,
          edges: edges
        };
        const options = {
          nodes: {
            shape: "box",
            font: {
              size: 14
            }
          },
          edges: {
            font: {
              size: 10
            },
            smooth: {
              type: "continuous"
            }
          },
          physics: {
            stabilization: true,
            barnesHut: {
              gravitationalConstant: -2000
            }
          }
        };
        this.graph = createGraph(container, data, options);
      } finally {
        await session.close();
      }
    }
  }
};
</script>

<style>
#graph-container {
  width: 100%;
  height: 800px;
  border: 1px solid #ddd;
  margin: 20px;
}
</style>

```
