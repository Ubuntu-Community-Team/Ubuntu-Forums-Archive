---
title: "Disk full"
date: 2008-09-02
forum: General Help
---

### Post by Hairyloon on 2008-09-02
I've finally managed to get Ubuntu installed and connected to the internet. 
I haven't done much else beyond the install, however, it seems that my hard disk is now full (6.6GB).

Presumably there is a load of stuff gone on in the install that I don't actually need, but what is the best way to find it?

I'm also having trouble with firefox: it's not saving bookmarks and it's marking virtually everything I type as a spelling error.

---

### Post by Sycron on 2008-09-02
Try```
sudo apt-get clean
```
and install localepurge ```
sudo apt-get install localepurge
```then run it ```
localepurge
```

---

### Post by Luke771 on 2008-09-02
also start a file browser as root with sudo nautilus, delete everything form /tmp, delete everything except the folder 'partial' from /var/cache/apt/archives 
This should get you some space back.

---

### Post by monkeyking on 2008-09-02
you can check the size of a folder with du

```
du -skh 
```

---

### Post by Hairyloon on 2008-09-06
Thanks folks.

---

### Post by KrakensDen on 2008-09-06
Try using Baobob, `baobob' from the command line, 'Disk Usage Analyzer' from the menu. Comes with Ubuntu by default, IIRC. Tell it to scan your home directory, it will give you a very useful visualization of where your space is going...

And if you're anything like me, all your disk usage happens in your home directory.

---

