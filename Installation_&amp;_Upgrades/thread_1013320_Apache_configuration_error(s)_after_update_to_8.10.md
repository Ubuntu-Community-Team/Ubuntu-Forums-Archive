---
title: "Apache configuration error(s) after update to 8.10"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by Master Chief on 2008-12-16
I finally gave 8.10 a go one of my computers to 8.10 but I wish I did because it started with video card/driver problems, which I fixed.

Then my canon lbp500 printer wouldn't work anymore, and now my local web server can't be reached. Great update strategy, but not really, but I should not have done this because I was doing something else at the same time.

My webserver/ip combo is still in /etc/hosts
I also checked my configuration files in /etc/apache2/ 
and they appear to be fine, but I still can't load any of my pages. I feel stupid, and a bit lazy, but my work has to be finished before Christmas or there won't be a bonus after all so all help will be greatly appreciated ;)

---

### Post by joff13 on 2008-12-17
> **Master Chief said:**
> 
My webserver/ip combo is still in /etc/hosts
I also checked my configuration files in /etc/apache2/ 
and they appear to be fine, but I still can't load any of my pages. I feel stupid, and a bit lazy, but my work has to be finished before Christmas or there won't be a bonus after all so all help will be greatly appreciated ;)

Hi,
you upgrade before a short dead-line ?!
anyway,

```

sudo /etc/init.d/apache stop
sudo /etc/init.d/apache start

```

and post the error
an also
```
apache -t
```
to check the config file

Good luck

---

### Post by Master Chief on 2008-12-18
Thanks, but there is no /etc/init.d/apache
but /etc/init.d/apache2 and there are no errors whatsoever.

Apache is running fine, and the problem was that the upgrade script replaced some of my configuration files, probably because I clicked yes when I should have clicked no/cancel, but isn't it just plain stupid to even ask people to replace good working configuration files?  Especially when someone upgrades?

p.s. VirtualBox was also broken, and this was also just an easy fix, and it could as well have been part of the upgrade procedure/scripts, but no sir, and thus; if this Ubuntu version is for humans, then I must either be a weird animal or this upgrade script really sucks.

---

