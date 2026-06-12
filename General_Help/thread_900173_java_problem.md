---
title: "java problem"
date: 2008-08-25
forum: General Help
---

### Post by jingqi on 2008-08-25
I try to run jalview with java, but failed.

code: 
jqduan@jqduan-laptop:~/Desktop/software/jalview-1.7.5b$ java -jar jalview-1.7.5b.jar 
Failed to load Main-Class manifest attribute from
jalview-1.7.5b.jar

---

### Post by aloshbennett on 2008-08-25
The MANIFEST.MF present in the jar file doesnt contain Main class information.

You might have to add the jar to classpath and launch it as told in this url:
[http://www.jalview.org/version118/documentation.html#inputcommandline](http://www.jalview.org/version118/documentation.html#inputcommandline)

---

