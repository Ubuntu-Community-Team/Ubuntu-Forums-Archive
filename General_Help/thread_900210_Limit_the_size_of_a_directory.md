---
title: "Limit the size of a directory"
date: 2008-08-25
forum: General Help
---

### Post by agasamapetilon on 2008-08-25
Is there any way to set a limit size to a directory using the shell? I guess the are some applications that can do so, but I prefer a command line if possible.

i.e.: I would like to limit the /$HOME/example up to 10MB.

Thanks,

---

### Post by forger on 2008-08-25
I think you can set quotas per mount points, per devices or per user/group:
```
sudo apt-get install quota quotatool
man quotatool
```

[http://articles.techrepublic.com.com/5100-10878_11-6070392.html](http://articles.techrepublic.com.com/5100-10878_11-6070392.html)
[http://www.debian-administration.org/articles/47](http://www.debian-administration.org/articles/47)

---

### Post by agasamapetilon on 2008-08-25
I appreciate a lot the quick answer and for providing some links as a reference. I read a bit of the documentation and its possible to add quotas to users and groups, which make the a sysadmin life a lot more easier.

Thanks once more!

---

