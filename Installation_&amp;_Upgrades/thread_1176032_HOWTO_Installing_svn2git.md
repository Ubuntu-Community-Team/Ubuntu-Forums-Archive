---
title: "HOWTO: Installing svn2git"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by LepeKaname on 2009-06-01
If you want to install svn2git (it is not at Ubuntu repositories):

```
sudo aptitude install rubygems

sudo gem install nirvdrum-svn2git --source http://gems.github.com

and the command will be located at:

/var/lib/gems/1.8/bin/svn2git
```

I posted this because I read several articles of how to use it but almost none on how to get it...

---

### Post by Chico25 on 2011-05-23
thanks, i was just looking for that.

---

### Post by qneill on 2012-05-08
If you're an [apt-get]("http://ubuntuforums.org/showthread.php?t=379804") kind of person, instead of

```
sudo aptitude install rubygems
```

of course you will run:

```
sudo apt-get install rubygems
```

-- 
Quentin

---

### Post by oldos2er on 2012-05-08
Old thread closed.

---

