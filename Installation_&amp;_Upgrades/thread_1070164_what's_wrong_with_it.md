---
title: "what's wrong with it?"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by sharethl on 2009-02-14
&#27491;&#22312;&#35835;&#21462;&#36719;&#20214;&#21253;&#21015;&#34920;... &#23436;&#25104;
&#27491;&#22312;&#20998;&#26512;&#36719;&#20214;&#21253;&#30340;&#20381;&#36182;&#20851;&#31995;&#26641;
&#35835;&#21462;&#29366;&#24577;&#20449;&#24687;... &#23436;&#25104;
&#19979;&#21015;&#30340;&#36719;&#20214;&#21253;&#23558;&#34987;&#21319;&#32423;&#65306;
linux-image-2.6.24-23-generic
&#20849;&#21319;&#32423;&#20102; 1 &#20010;&#36719;&#20214;&#21253;&#65292;&#26032;&#23433;&#35013;&#20102; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#35201;&#21368;&#36733; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26377; 0 &#20010;&#36719;&#20214;&#26410;&#34987;&#21319;&#32423;&#12290;
&#38656;&#35201;&#19979;&#36733; 0B/18.4MB &#30340;&#36719;&#20214;&#21253;&#12290;
&#25805;&#20316;&#23436;&#25104;&#21518;&#65292;&#20250;&#28040;&#32791;&#25481; 0B &#30340;&#39069;&#22806;&#30913;&#30424;&#31354;&#38388;&#12290;
&#24744;&#24076;&#26395;&#32487;&#32493;&#25191;&#34892;&#21527;&#65311;[Y/n]y
(&#27491;&#22312;&#35835;&#21462;&#25968;&#25454;&#24211; ... &#31995;&#32479;&#24403;&#21069;&#24635;&#20849;&#23433;&#35013;&#26377; 128869 &#20010;&#25991;&#20214;&#21644;&#30446;&#24405;&#12290;)
&#27491;&#39044;&#22791;&#26367;&#25442; linux-image-2.6.24-23-generic 2.6.24-23.46 (&#20351;&#29992; .../linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb) ...
Done.
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; linux-image-2.6.24-23-generic ...
dpkg&#65306;&#22788;&#29702; /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb (--unpack)&#26102;&#20986;&#38169;&#65306;
&#26080;&#27861;&#22312;&#23433;&#35013;&#26032;&#30340;&#29256;&#26412;&#21069;&#65292;&#20026;“./boot/vmlinuz-2.6.24-23-generic”&#20570;&#19968;&#20010;&#31526;&#21495;&#38142;&#25509;&#22791;&#20221;: &#25805;&#20316;&#19981;&#20801;&#35768;
dpkg-deb: &#23376;&#36827;&#31243; paste &#34987;&#20449;&#21495;(Broken pipe)&#32456;&#27490;&#20102;
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

&#22312;&#22788;&#29702;&#26102;&#26377;&#38169;&#35823;&#21457;&#29983;&#65306;
/var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by hansdown on 2009-02-14
Hi sharethl.

Which forum are you normally on?

I see your posts, but can't tell the location of that forum.

---

### Post by sharethl on 2009-02-14
I normally on this forum
[http://forum.ubuntu.org.cn](http://forum.ubuntu.org.cn)
I have post it there but nobody reply it, So I came to here for help.

---

### Post by hansdown on 2009-02-14
I found something that may help, but I don't know if the language will work.

I found this thread.

[http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)

It says to enter```
 apt-get -f install
```

I'm not sure if that is what you need, but maybe it will work?

---

### Post by bapoumba on 2009-02-15
@ sharethl: could you please translate your error messages so that we can give appropriate input? Thanks.

---

### Post by sharethl on 2009-02-18
root@sharethl-laptop:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.24-23-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.4MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 128581 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-23-generic 2.6.24-23.46 (using .../linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-23-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.24-23-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@sharethl-laptop:~#

---

### Post by bapoumba on 2009-02-18
Please post you sources.list
```
cat /etc/apt/sources.list

```
And the output to
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by sharethl on 2009-02-19
sharethl@sharethl-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy main restricted
deb-src [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy-updates main restricted
deb-src [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy universe
deb-src [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy universe
deb [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy-updates universe
deb-src [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy multiverse
deb-src [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy multiverse
deb [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy-updates multiverse
deb-src [http://debian.nctu.edu.tw/ubuntu/](http://debian.nctu.edu.tw/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

# deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy main restricted universe multiverse
# deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-security main restricted universe multiverse
# deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-updates main restricted universe multiverse
# deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-proposed main restricted universe multiverse
# deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy main restricted universe multiverse
# deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-security main restricted universe multiverse
# deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-updates main restricted universe multiverse
# deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-proposed main restricted universe multiverse
# deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-backports main restricted universe multiverse
deb [http://archive.ubuntu.org.cn/ubuntu-cn/](http://archive.ubuntu.org.cn/ubuntu-cn/) hardy main restricted universe multiverse
# deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

---

### Post by bapoumba on 2009-02-19
Please enable the hardy-security repositories :)

---

### Post by sharethl on 2009-02-21
It didn't work,

---

### Post by bapoumba on 2009-02-23
Hmm, may be try to use the main repos just to check. May be the repos you are using are not synced properly.. I got that kernel up and running.

---

### Post by ugm6hr on 2009-02-23
Post output from:
```
df -m
```

---

