---
title: "Upgrading Gutsy laptop"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by gorcq on 2009-10-16
I have a Toshiba laptop running Gutsy. It recently came to my attention that Gutsy has been declared end-of-life when I had some trouble getting the latest version of OpenOffice because the version I have won't open certain Word files. (I guess that makes me sound a bit slow, doesn't it?)

OpenOffice is not the only program on my computer that doesn't really work right. That's why I've been trying to upgrade Ubuntu to a later version, one that still has repositories. I found an article about upgrading end-of-life distros which I'll post a link to at the bottom of this, which basically says to change the file [FONT="monospace"]/etc/apt/sources.list[/FONT] and then, while running [FONT="monospace"]kernel 2.6.22-14[/FONT], call a program called [FONT="monospace"]do-release-upgrade[/FONT].

I think I have followed these instructions correctly; but when I call the said program, I get the following message:```
Checking for a new ubuntu release
current dist not found in meta-release file
No new release found
```I must admit I'm not entirely sure what a meta-release file is, but it seems like my current distro should be there. Any help with this would be appreciated.

[https://help.ubuntu.com/community/EOLUpgrades/Gutsy]("https://help.ubuntu.com/community/EOLUpgrades/Gutsy")

---

### Post by stlsaint on 2009-10-16
i would recommend that you do a fresh install...backup all data/programs and do a fresh install of jaunty or karmic when its released. If you upgrade then you will have to go thru all versions from gutsy up to say jaunty one by one...a very long process.

---

### Post by raymondh on 2009-10-16
> **stlsaint said:**
> i would recommend that you do a fresh install...backup all data/programs and do a fresh install of jaunty or karmic when its released. If you upgrade then you will have to go thru all versions from gutsy up to say jaunty one by one...a very long process.

not to forget ... also update each version prior to upgrading to the next.

---

### Post by gorcq on 2009-10-17
You both make good points. On the other hand, my laptop doesn't have a CD drive. I originally attempted to install Ubuntu on it using a program called [Unetbootin]("http://unetbootin.sourceforge.net/"), which would have worked had I watched what I was doing and not installed a version of Hardy that was, at the time, under development. Then I f*cked up the system trying to fix that, and ultimately got gutsy installed in perhaps the most complicated manner possible: by using my Windows desktop as a semi-functional PXE server.

I have attempted to install a linux version of Unetbootin so that I could upgrade to Jaunty, but Unetbootin has various dependencies that I don't have and can't get because the repositories are missing.

The PXE server thingy might work again, but that was difficult to begin with: my desktop doesn't have a direct connection to the internet and the PXE server program insists upon also being a DHCP server, which means that after I got the Ubuntu install program running on my laptop, I had to quickly shut down the PXE server before the program attempted to connect to the repositories, because it would otherwise attempt to connect through my desktop, and that doesn't work. The whole thing was jury-rigged and only ever worked by luck.

Now you will hopefully understand me when I say that I question whether upgrading through Hardy and the other one is the more complicated method -- if I could get that to work properly.

---

### Post by slakkie on 2009-10-17
Hi, could you post the output of /etc/update-manager/release-upgrades 
It should say Prompt=normal. If you have Prompt=never, do-release upgrade will not find a suitable release to upgrade to.

---

### Post by gorcq on 2009-10-17
I don't appear to have that file. Is that bad?
```
gorcq@Otter:~$ ls /etc/update-manager
ls: /etc/update-manager: No such file or directory
gorcq@Otter:~$ /etc/update-manager/release-upgrades
bash: /etc/update-manager/release-upgrades: No such file or directory
gorcq@Otter:~$ cat /etc/update-manager/release-upgrades
cat: /etc/update-manager/release-upgrades: No such file or directory
gorcq@Otter:~$ sudo !!
sudo cat /etc/update-manager/release-upgrades
[sudo] password for gorcq:
cat: /etc/update-manager/release-upgrades: No such file or directory
```

---

### Post by slakkie on 2009-10-17
I couldn't find it either on my vm with gutsy.

That leaves very little, do you have one of the following files:

/etc/apt/preferences
/etc/apt/apt.conf

If you have one of them please post the output.

Could you also post the output of:

lsb_release -a

---

### Post by gorcq on 2009-10-17
```
gorcq@Otter:~$ cat /etc/apt/preferences
cat: /etc/apt/preferences: No such file or directory
gorcq@Otter:~$ cat /etc/apt/apt.conf
cat: /etc/apt/apt.conf: No such file or directory
gorcq@Otter:~$ ls /etc/apt
[COLOR="Blue"]apt.conf.d[/COLOR]    sources.list       sources.list.bak3  trustdb.gpg
cources.list  sources.list.bak   [COLOR="Blue"]sources.list.d[/COLOR]     trusted.gpg
secring.gpg   sources.list.bak2  sources.list.save  trusted.gpg~
gorcq@Otter:~$ ls /etc/apt/apt.conf.d
00trustcdrom  01ubuntu    10periodic  50unattended-upgrades  99update-notifier
01autoremove  05aptitude  20archive   70debconf
gorcq@Otter:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Debian
Description:    DebianEdu/Skolelinux (terra)
Release:        3.2
Codename:       etch
```

---

### Post by slakkie on 2009-10-17
> **gorcq said:**
> ```
gorcq@Otter:~$ cat /etc/apt/preferences
gorcq@Otter:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Debian
Description:    DebianEdu/Skolelinux (terra)
Release:        3.2
Codename:       etch
```

This is your problem. You are not running Ubuntu, but an educational Debian version. Have a look here [http://www.skolelinux.org](http://www.skolelinux.org)

---

### Post by gorcq on 2009-10-17
Huh. It definitely does say that. Which makes me wonder why the screen always says "Ubuntu" in large letters when I boot up. It is labeled Ubuntu in various other locations, too.

In any case, it's clear that something is weird about this installation, which makes me question the logic of upgrading. I think I will get out the PXE server program that I used before and see if I can make it work again. Thank you for helping.

---

