---
title: "Hibernate JPA MySQL problem"
date: 2008-11-28
forum: General Help
---

### Post by mortsahl on 2008-11-28
I haven't had windows on my personal machine since Ubuntu 6.0x ... but unless I can resolve the following problem, I'm going install XP again this weekend...

---------------------

I'm using Ubuntu 8.10 (same problem with 8.04), JPA with Hibernate as the provider and Spring 2.5.5. This problem does not exist when running the same code and same versions of software in windows. 

I've a junit 4 test ... 

```

  @RunWith(SpringJUnit4ClassRunner.class)
    @ContextConfiguration(locations = "classpath:applicationContext.xml")
    @Transactional
    public class ArticleServiceTest {
     
       private Article article;
     
       @Autowired
       private ArticleService articleService;
     
       /**
        * Create test article before each test is run. Because of the
        * @Transaction annotation at the class level, the transaction should be rolled back after each class is run.
        */
       @Before
       public void createArticle() {
         
          List<Article> articlesToCreate = new ArrayList<Article>();
         
          article = new Article();
          article.setAuthor("Author");
     
          articlesToCreate.add(article);
          assertTrue(articleService.create(articlesToCreate) == 1);
          assertNotNull(article.getId());
    }
     
       @Test
       public void create() {
          Article a = articleService.getArticleById(article);
          assertNotNull(article.getId());
          assertSame(article, a);
       }
    }

```

The problem is, in Ubuntu, the article is not rolled back ... it should be.

In Windows, after the test is run, the article is rolled back.

Any ideas why I'm getting this behavior in Ubuntu?

---

