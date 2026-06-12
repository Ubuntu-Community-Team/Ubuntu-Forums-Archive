---
title: "Can't install ubuntu, only use live session."
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by lcollier93 on 2009-08-31
I just recently downloaded and burned ubuntu to a cd and it boots up just fine. I go through the installation instructions and it gets to the installing system window. At 5% (creating ext3 file system on some partition), it just goes to a black screen and loads the live session. Any ideas?

---

### Post by hockeytux on 2009-08-31
Have you checked the CD for errors?

---

### Post by lcollier93 on 2009-08-31
yes I did check the cd for errors and everything is fine. I also burned the cd at the slowest speed that I could (x3?) to make sure that it burned correctly.

---

### Post by lcollier93 on 2009-08-31
also, whenever the live session starts it says crash report detected.

---

### Post by lcollier93 on 2009-08-31
ok the problem is that the installer crashes. is there anything I can do to stop this?

---

### Post by raisen on 2009-08-31
How are you partitoning your disk?

---

### Post by anujpathania on 2009-08-31
Are u trying to dual boot or a clean Install?

A friend of mine faced such an issue when he was attempting to install ubuntu on his MAC.

---

### Post by lcollier93 on 2009-08-31
it's kind of a dual boot. I have two seperate hard drives on my computer. one is a 320GB Western Digital which I have windows 7 on and the other is a 60GB Samsung which I am trying to install ubuntu on.

---

### Post by presence1960 on 2009-08-31
what are your system specs?

---

### Post by lcollier93 on 2009-08-31
Umm....

Intel Pentium 4 Processor 1.8 Ghz
2 GB RAM
320GB Western Digital Harddrive (Windows 7)
60GB Samsung Harddrive (Potential ubuntu install)


Idk what else i should put. haha

---

### Post by jerrrys on 2009-08-31
when you install are you using the **use entire disk** option

---

### Post by lcollier93 on 2009-08-31
yes i am.

---

### Post by jerrrys on 2009-08-31
does it see both HDD?

---

### Post by lcollier93 on 2009-08-31
yes so I just choose the 60GB Samsung.

---

### Post by presence1960 on 2009-08-31
> **lcollier93 said:**
> Umm....

Intel Pentium 4 Processor 1.8 Ghz
2 GB RAM
320GB Western Digital Harddrive (Windows 7)
60GB Samsung Harddrive (Potential ubuntu install)


Idk what else i should put. haha

[boot options]("https://help.ubuntu.com/community/BootOptions") - you may want to try F6 options

If all else fails use the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")
which by the way is a more robust installer than the live CD. It is text based though and you can't run a live session, but it has way more install options and support compared to the Live Cd. it just isn't as pretty.

---

### Post by lcollier93 on 2009-08-31
ok i will try both of those. thank you.

---

### Post by lcollier93 on 2009-08-31
which boot options should i use?

---

### Post by jerrrys on 2009-08-31
nevermind

---

### Post by lcollier93 on 2009-08-31
oh well nevermind.

---

### Post by tal007 on 2009-08-31
I suspect it is the case of hard drive. You have a large hard drive does not mean that you can install Ubuntu on it. First, check to see if there is any partitions on it. If so, who owns it ( e.g Xp, Vista etc.. ). If there is any partition on it and currently not being by any OS, you have to free up drive space on that drive so that you can install Ubuntu on it. Otherwise, your installation will freeze during installation. Don't delete partitions from outside. Only do it from the OS that owns it to free up space. If you do it from outside, your existing OS may become inoperable.  

Alternately you can resize you drive using the Live Ubuntu CD to free up space, but don't delete partition if you don't know. The analogy I will draw here is - 

Your neighbor has a big yard, does not mean that you can go there and put stuffs on it. In our our human world you can get away by ruffling your neighbor's feathers, but in your Operating system world the OS may not not be that forgiving if you touch its territory without its knowledge.

---

### Post by presence1960 on 2009-08-31
> **tal007 said:**
>  If there is any partition on it and currently not being by any OS, you have to free up drive space on that drive so that you can install Ubuntu on it. Otherwise, your installation will freeze during installation.   

Alternately you can resize you drive using the Live Ubuntu CD to free up space, but don't delete partition if you don't know. The analogy I will draw here is - 



I would be careful with that advice. You can free up space from a windows partition to install Ubuntu onto by shrinking the windows partition. it does not have to be from a partition not "owned". 

If it is an XP partition you can shrink it by using gparted either from the gparted Live CD or the Ubuntu Live CD.

**If it is a Vista partition you are advised to shrink the Vista partition by using Vista's disk management utility.**

In either case you should defrag windows at least once or twice prior to resizing.

Tal not being smart or anything but you really need to learn about the Ubuntu installation process. This is the 3rd or 4th time you have given advice that you can't install using space from a windows partition whether shrunk manually or by the installing side by side option of the installer. So according to your theory someone who has windows on one big partition that takes up the entire hard disk can't install ubuntu because it will freeze?

---

### Post by lcollier93 on 2009-08-31
The hard drive I'm trying to install it on is completely clean. there's nothing on it at all. also I tried to install this on unallocated space on my 320GB harddrive and the same problem occurred.

---

### Post by lcollier93 on 2009-08-31
anyway. for now I'm just going to try to install using the textbased installer or using the F6 install options. the textbased one just finished donwloading so I'll try that.

---

### Post by presence1960 on 2009-08-31
> **lcollier93 said:**
> anyway. for now I'm just going to try to install using the textbased installer or using the F6 install options. the textbased one just finished donwloading so I'll try that.

Give that a shot. Good Luck!

---

### Post by lcollier93 on 2009-08-31
ok i ran the installation using the textbased installer and over halfway through it came up saying please insert the disk labeled Ubuntu 9.04 Jaunty Jackalope version i386. anyone have a link for the iso for this disk? however it does seem to have gone past the part where it crashed last time so I think this is working correctly.

---

### Post by hockeytux on 2009-09-01
> **lcollier93 said:**
> ok i ran the installation using the textbased installer and over halfway through it came up saying please insert the disk labeled Ubuntu 9.04 Jaunty Jackalope version i386. anyone have a link for the iso for this disk? 


Here it is: [Ubuntu 9.04 i386]("http://superdownloads.uol.com.br/linux/distribuicoes/distro208.html")

Click on the link in green - 'ISO 1 (Instalaçao) 699MB' to start the download.

---

### Post by jerrrys on 2009-09-01
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by lcollier93 on 2009-09-01
Ok so I get to 76% on the installation and it says insert disk labeled Ubuntu 9.04 Jaunty Jackalope version i386 into the drive /cdrom. So I insert the disk and click continue and nothing happens. Is there a way to get a full installation of this so I don't have to insert another disk?

---

### Post by lcollier93 on 2009-09-01
OK. I finally got it to work. thanks for all of the help!:D

---

### Post by presence1960 on 2009-09-01
Glad you got it working! Enjoy Ubuntu.

---

### Post by raisen on 2009-09-01
> **lcollier93 said:**
> OK. I finally got it to work. thanks for all of the help!:D
 
Glad you got it to work. As you had all these issues, you might think on submitting a bug report and report all the issues you went through.

---

