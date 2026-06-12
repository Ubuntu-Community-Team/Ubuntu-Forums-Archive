---
title: "FireFox 3.5 released but no upgrade?"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by justin10ec on 2009-07-05
I noticed that FireFox 3.5 has been released but Ubuntu doesn't upgrade to it. Am I doing something wrong?

I'm doing this in the terminal:

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

But it doesn't affect FireFox.

---

### Post by wojox on 2009-07-05
Open your Terminal and run following command

```
echo ‘deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main’ >> /etc/apt/sources.list
```

Add the Launchpad PPA GPG key

```
sudo apt-key adv –keyserver keyserver.ubuntu.com –recv-keys 247510BE
```

Now run below command on your terminal

```
sudo apt-get update && sudo apt-get install firefox-3.5
```

---

### Post by ibutho on 2009-07-05
> **justin10ec said:**
> I noticed that FireFox 3.5 has been released but Ubuntu doesn't upgrade to it. Am I doing something wrong?

I'm doing this in the terminal:

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

But it doesn't affect FireFox.
You are not doing anything wrong. Ubuntu does not usually upgrade packages to major versions after an Ubuntu release. This  is mainly for stability reasons. There are many threads on this forum that can help you install firefox 3.5 on your existing Ubuntu installation.

---

