---
title: "Newbie: How to know the OS that are installed on my computer?"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by fredscripts on 2007-08-18
Hi There! I've just installed kubuntu 7.04 on a computer that has already installed windows xp. (was my first time installing any linux system).

When I rebooted I saw an interesting Grup message letting me chose where I wanted to boot (windows xp or kubuntu).

As I'm newbie and I'm interested in the linux world, I'm wondering what command could I use in linux in order to see how is my system organized, I mean, that tells me: ok you have a partitions with widows xp, another with kubuntu and another with ... you know.

Because I would like to manage my system in a good way, you know making differents partitions for /home and so on. Furthermore, I remember a friend installed an old linux system on that computer and I'd like to erase that and I don't know where it is.

To sum up, if someone could help me in this very newbie adventure learning how to have a good installed dual boot computer (xp/kubuntu) I'll be very grateful, because I think that computer is such a mess in terms of partitions (I've seen during installation hda10 :S), a pdf guide will be very useful because I'm going on vacation and no internet there!.

Sorry for my english I'm from Spain!!

Thank you very much!!!!

---

### Post by 1/0 on 2007-08-18
Well, I think its easier to read a guide written in a good way, rather than a poorly (?) made explanation by me.

[This page]("http://www3.telus.net/lordfoul/pics/useful%20ubuntu%20links/useful%20unbuntu%20links.html") has a lot of links to a lot of guides that will fill you in on most stuff you want to do. Look for gparted or fdisk when it comes to partitions but be careful using those tools. You can damage your system permanently.

---

### Post by fredscripts on 2007-08-18
oh Thanks!!!

A little question: if I run on my kubuntu 7.04 the command fdisk /dev/hda in order to see how is my hard drive organized (with all the operating systems and so on) it says to me "unable to found" or something like that. I would like to run a command to see how is my system organized (partitions, os...) maybe something like cat /etc/ someone told me but I don't remember. Could you help me? :)

Thank you very much!

---

### Post by 1/0 on 2007-08-18
Try:

```
sudo fdisk /dev/sda
```

You need root privileges to use fdisk. But you might, in comparison to me, prefer a GUI for this stuff. I just noticed you use Kubuntu and not Ubuntu. In Kubuntu there's a tool for that located under "System settings" - "Advanced" - "Disk & Filesystems".

---

### Post by fredscripts on 2007-08-18
Thanks again!! Here are the results of checking the HD:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        4026    22097407+   f  W95 Ext'd (LBA)
/dev/hda3            4027        4864     6731235   83  Linux
/dev/hda5            1276        2315     8353768+   7  HPFS/NTFS
/dev/hda6            3188        3310      987997   82  Linux swap / Solaris
/dev/hda7            3311        3981     5389776   83  Linux
/dev/hda8            2316        3143     6650878+  83  Linux
/dev/hda9            3144        3187      353398+  82  Linux swap / Solaris
/dev/hda10           3982        4026      361431   82  Linux swap / Solaris

Partition table entries are not in disk order
 


As you can see, my hard drive is such a mess hahaha, and as I'm newbie, I would like to have a simple dual boot windows xp /kubuntu 7.04 without that noise. Any suggestions? I'll be so grateful if you could help me with this newbie adventure :)

---

### Post by 1/0 on 2007-08-18
To get info such as that you could use:

```
df -h
```

I don't use windows but I guess I would first create one partition with NTFS for Windows, leaving the rest unpartitioned. Then I would install windows. After that Xubuntu/Ubuntu/Kubuntu. There are plenty of guides on this out there that explains this:

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

---

### Post by fredscripts on 2007-08-18
thank you very much for the guides! one last question, how can I know where is windows and when is linux?  I mean, I want to format all the HD that isn't windows xp and kubuntu 7.04 (I guess that among all that partitions I'll have to clean a little) some ideas to do it? (I'll read those guides as I'm going on vacation in a few hours, but some help will be nice :))

---

### Post by 1/0 on 2007-08-18
It looks as Windows uses hda1, hda2 and hda5. You can mount them if you have NTFS enabled in Kubuntu. Look under /media/hda1 aso in a file browser. 

Just a warning. If you partition or format you are going to loose everything so don't go wrong! and backup!!

---

### Post by fredj on 2007-08-19
Open a terminal and type cd /boot/grub. Then type gedit menu.lst. Scroll down past all
the commented out lines and you will see which OS are loaded on your PC and which 
hard disk partitions they are on.

---

### Post by fredscripts on 2007-08-25
Thank you very much. I've read a few guides (I must confess was a little hard for me to understand some things) but I have a little problem to start with all the good installation.

I don't want to re-install windows xp (I don't have the installation cd). In newbie terminology, I want to clean all the hard drive that don't have windows ( I suppose that means I want to free all the hard disk space except the NTFS partitions) and then install kubuntu 7.04(which I have the installation cd) on that free space. I've been all the week reading guides (which are great) but I have difficulties on this beginning.

I wish someone could help me with this first step: cleaning all the HD except ntfs partitions (which I don't    like to touch because I don't have a windows installation cd)  in order to  install kubuntu on the free space I'll have (If I feel encouraged I'll do a good installation with different partitions for /home and so on hehehe).

Thanks again for your help and patience!:)

---

### Post by liviubero on 2007-08-25
Don't know for KDE, but for Ubuntu there is gparted, a tool for editing partitions.
Anyway, if you plan to reinstall Kubuntu, you will be able to erase during the installation whatever partition you want - that is to make free space, as you seem to desire.

---

