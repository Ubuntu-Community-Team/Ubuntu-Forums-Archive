---
title: "Ubuntu 10.04 on Lenovo Thinkpad  i5 X220"
date: 2011-08-26
forum: Hardware
---

### Post by umerlone on 2011-08-26
Hi All,
I installed Ubuntu 10.04 on a Thinkpad X220 i5.
Everything seems to work fine except I cannot get the resolution 1366x768.

Can any one suggest me a solution without upgrading to 11.04 which I do not like particularly as on my current machine I cannot anymore use dual monitor?

Thank you very much

Ugo

---

### Post by realzippy on 2011-08-31
show your

```
xrandr -q
```

---

### Post by umerlone on 2011-09-01
Here it is:

Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0*

Thanks!

Ugo

---

### Post by realzippy on 2011-09-01
Get a newer kernel since intel driver is part of it.

```
sudo add-apt-repository ppa:kernel-ppa/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install linux-headers-2.6.38-8-generic linux-image-2.6.38-8-generic
```
reboot

EDIT:
...in another thread we are facing problems with that ppa,so we may need to install kernel manually.

---

### Post by umerlone on 2011-09-01
I copied all the code
It says 
E: Couldn't find package linux-headers-2.6.38-8-generic

I tried also to get it from

[http://packages.ubuntu.com/natty/amd64/linux-headers-2.6.38-8-generic/download](http://packages.ubuntu.com/natty/amd64/linux-headers-2.6.38-8-generic/download)

but it said
Error: Dependency is not satisfiable: linux-headers-2.6.38-8

Any suggestion?
Thanks



Ugo

---

### Post by realzippy on 2011-09-01
32 or 64 bit?

---

### Post by realzippy on 2011-09-01
Since you tried to install 
[http://packages.ubuntu.com/natty/amd64/linux-headers-2.6.38-8-generic/download](http://packages.ubuntu.com/natty/amd64/linux-headers-2.6.38-8-generic/download)
I guess your system is 64bit.
So:
```
cd Downloads
```

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/linux-headers-2.6.38-02063808_2.6.38-02063808.201106040910_all.deb

```
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/linux-headers-2.6.38-02063808-generic_2.6.38-02063808.201106040910_amd64.deb
```
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/linux-image-2.6.38-02063808-generic_2.6.38-02063808.201106040910_amd64.deb
```
```
sudo dpkg -i linux-headers-2.6.38-02063808_2.6.38-02063808.201106040910_all.deb
```
```
sudo dpkg -i linux-headers-2.6.38-02063808-generic_2.6.38-02063808.201106040910_amd64.deb
```
```
sudo dpkg -i linux-image-2.6.38-02063808-generic_2.6.38-02063808.201106040910_amd64.deb
```

You also need fresher versions of libdrm,mesa,aso. !

Easy way to get them is adding xorgedgers ppa;since those guys don't
want giving instructions how to install without reading their page:
*** Please do not publish instructions for how to install from this archive without linking to this page! Anyone using packages from this archive is expected to read this page first and it is recommended to check back occasionally for notice on problems that may arise. ***

[visit them]("https://launchpad.net/~xorg-edgers/+archive/ppa"),read,then post and we go on.

**Edit:**
Back in 1 h..real life calling,sorry.

---

### Post by umerlone on 2011-09-01
Hi,
thanks for your help and patience!!
I visited them and I recall that two days ago on the link

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X220](http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X220)

I found some instructions, and I visited another link and added two repositories
sudo add-apt-repository ppa:kernel-ppa/ppa
sudo add-apt-repository ppa:glasen/intel-driver
sudo add-apt-repository hackenberger/x220-intel-mesa

I do know if they are similar or conflict

As you can guess I am a Beta version of Ubuntu user.

Ugo

---

### Post by realzippy on 2011-09-01
If you add glasen's and hackenberger's ppa,you do not need xorgedgers.
Remove xorgedgers then if you already added it.glasen and hack" are a little
more up to date,although xorgedgers would have worked also.
Kernel ppa we already tried,but it doesn't seem to work,so you might install -as described- kernel manually.

You know how to go on?

---

### Post by umerlone on 2011-09-01
Actually at the moment I have only

glasen and kernell-ppa/ppa/ubuntu

In fact with hack I got the message

Error: 'hackenberger/x220-intel-mesa' invalid

By the way now I have the graphic I expected as xrandr saysScreen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768        0.0* 

Thanks a lot!!

Ugo

PS. unless I do not get any other suggestion I will mark the thread as SOLVED

---

### Post by realzippy on 2011-09-01
So where did you got the kernel from?

---

### Post by umerlone on 2011-09-01
Originally, I got from Ubuntu the 
**[SIZE=1]Ubuntu 10.04.3 LTS (Lucid Lynx)[/SIZE]**

which I put on USB FAT32

then I tried to follow the thinkwiki, except I could not get the hackenberger

Then I followed your instructions.

Everything I did was done with little understanding of what I was doing...:confused:

---

