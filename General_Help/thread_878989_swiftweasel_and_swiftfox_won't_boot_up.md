---
title: "swiftweasel and swiftfox won't boot up"
date: 2008-08-03
forum: General Help
---

### Post by jubilee0824 on 2008-08-03
Hi there,

I heard swiftweasel and/or swiftfox were faster than firefox3, which takes more than 30 sec. to load, and another 30 sec. to open the first website on my laptop.

So I downloaded the latest version of (3.0.2-pre2) of swiftfox-athlonxp, it won't boot. (Actually it opens another firefox window if I already have firefox opened)

Then I tried 3.0.1 of swiftweasel; the same. When run from terminal, the error I get is:
> 
:~$ swiftweasel3 
the settings directory exists
settings file check passed
Error: in guard: symbol required but got: Error: fatal: looped fatal error


I installed both using apt-get install, using their repositories. And firefox3.0.1 still works; so it's not likely due the known uim bug.

Any idea? Thanks.

---

### Post by jubilee0824 on 2008-08-05
It did turn out that this was due to UIM! I was a bit reluctant to remove UIM, as I also use asian languages, but SCIM just does the same job! Just to note that UIM can interfere with swift*3 while firefox may still be working.

---

