---
title: "Java can't find required classes (activation and mail)"
date: 2008-11-19
forum: General Help
---

### Post by felipesa on 2008-11-19
I am trying to use Axis together with Tomcat and I am following the userguide in:

[http://ws.apache.org/axis/java/user-guide.html]("http://ws.apache.org/axis/java/user-guide.html")

When I get to type for the first example:

```
fsa@mrgildo:~$ java samples.userguide.example1.TestClient
```

I get the following error message and my shell is blocked:

```
- Unable to find required classes (javax.activation.DataHandler and javax.mail.internet.MimeMultipart). Attachment support is disabled.
```

I have included /usr/share/java/activation.jar, /usr/share/java/ant-javamail.jar and /usr/share/java/gnumail.jar in CLASSPATH with no success.

Has anyone been able to do that?

---

