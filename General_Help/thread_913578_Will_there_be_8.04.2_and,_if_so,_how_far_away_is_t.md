---
title: "Will there be 8.04.2 and, if so, how far away is that?"
date: 2008-09-07
forum: General Help
---

### Post by OzzyFrank on 2008-09-07
Hiya. Just wondering if there is going to be another major update to Hardy Heron 8.04, especially in the near future. I was going to start downloading 8.04.1 but realised that, with my luck, there could be another updated version coming out soon, so I'd rather wait and download 8.04.2 if that is coming out soon. Thanks in advance guys. Ozzman

---

### Post by tuxxy on 2008-09-07
Im not sure, Intrepids out in Oct! :popcorn:

---

### Post by Shazaam on 2008-09-07
As long as you keep up with the updates you will eventually have 8.04.2 :)

---

### Post by Eviltechie on 2008-09-07
How do you know if you are running 8.04.1?

---

### Post by damis648 on 2008-09-07
```
uname -r
```
or
```
uname -a
```

---

### Post by tuxxy on 2008-09-07
> **damis648 said:**
> ```
uname -r
```
or
```
uname -a
```

I think you mean

```
cat /etc/lsb-release
```

---

### Post by damis648 on 2008-09-07
Dang! I was like 80% sure one of those gave the Ubuntu Version. Oh well. Fail.

---

### Post by Shazaam on 2008-09-07
Or...
```
cat /etc/issue
```

---

### Post by tuxxy on 2008-09-07
> **damis648 said:**
> Dang! I was like 80% sure one of those gave the Ubuntu Version. Oh well. Fail.

Yes you were close, uname gives you machine/kernal details though, not OS details like version

---

### Post by kostkon on 2008-09-07
> **OzzyFrank said:**
> Hiya. Just wondering if there is going to be another major update to Hardy Heron 8.04, especially in the near future. I was going to start downloading 8.04.1 but realised that, with my luck, there could be another updated version coming out soon, so I'd rather wait and download 8.04.2 if that is coming out soon. Thanks in advance guys. Ozzman
There will be one, sometime around the start of 2009 and more will follow. Please, read [this post from Mark Shuttleworth's blog]("http://www.markshuttleworth.com/archives/146").
> **Eviltechie said:**
> How do you know if you are running 8.04.1?
you can open a terminal and give
```
lsb_release -a
```
or just open the *System Monitor* (*System -> Administration -> System Monitor*) and look in the *System* tab.

---

### Post by OzzyFrank on 2008-09-07
Hi, and thanks all. OK, I know 8.10 is out in a month or so, but 8.04 is an LTS release, which is why it's had an update. My reason for asking this in the first place is coz I hand out install discs and just want them to be the latest (for this LTS release). Since I will be downloading all flavours of Ubuntu in both 32- and 64-bit, I thought I may as well ask before doing so, in case 8.04.2 comes out next week or something, hehe.

As for how you find what version you're running, I think I saw my 8.04 go to 8.04.1 in Update Manager.

---

### Post by mb_webguy on 2008-09-07
> **kostkon said:**
> you can open a terminal and give
```
lsb_release -a
```
or just open the *System Monitor* (*System -> Administration -> System Monitor*) and look in the *System* tab.

The command "lsb_release -a" gives me the following output:> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy


System Monitor simply tells the general release (8.04) and not the point release (8.04.1).

---

### Post by chris4585 on 2008-09-07
I'm sure this is what you want: [http://www.ubuntu.com/products/ubuntu/release-cycle]("http://www.ubuntu.com/products/ubuntu/release-cycle")

---

