---
title: "JDBC drivers"
date: 2008-10-23
forum: General Help
---

### Post by tashe on 2008-10-23
If I try to connect to Oracle database 10g with Java in NetBeans or JDeveloper, do I need to install drivers like i do in Windows xp?
thanks

---

### Post by jespdj on 2008-10-23
You need to have a JDBC driver to connect to your database from Java - this is independent of the operating system that you're using.

The JDBC driver is just a JAR file, which you'll have to add to your project.

[Download page for Oracle JDBC drivers](http://www.oracle.com/technology/software/tech/java/sqlj_jdbc/index.html)

---

### Post by tashe on 2008-10-23
where should I add the driver? Is it like windows in system variable or somewhere else?
thanks

---

### Post by Nepherte on 2008-10-23
Add them as external archives in your build path.

---

