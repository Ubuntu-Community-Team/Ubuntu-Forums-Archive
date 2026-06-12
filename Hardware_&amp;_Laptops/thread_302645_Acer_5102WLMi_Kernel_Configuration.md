---
title: "Acer 5102WLMi Kernel Configuration"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by pmaciver on 2006-11-18
Hi,

Last week I puerchased an Acer 5102WLMi.

And since then I have been trying to configure the kernel so that it contains only the drivers that I need for my system.

The thing is all my previous attepts to configure the kernel have resulted in a system that doesn't boot. It doesn't kernel panic, but it just hangs after the line "Loading system drivers". 

This machine has a 64 bit AMD Turion x2 dual core processor inside, but I have chosen to install the 32 bit verion of Ubuntu Dapper, is this okay? I have heard that getting the 64 bit verion to work can take some tweeking, and I just wanted a system that works for now.

Also is it work me putting on Edgy on there instead of dapper? I know people have had some issues with edgy, and I don't know what is the headace factor involed with installing edgy at the moment.

So I guess the first question is Dapper or Edgy, 64 bit or 32 bit version?

And then I would like to ask anyone that has got this or a similar model of laptop if they would share information on how to configure my kernel for this system.

It would be good if there was a guide on the various bits and pieces involved in getting this series of laptops working. There are bits and pieces scattered around but nothing of detail.

Anyway, thanks to all in advance.

---

### Post by cruiseraddict on 2006-11-21
I have the same laptop running Edgy 64bit. Loaded fine. The camera and sd card still do not work. I am looking for drivers. As far as the kernel. I am using the default kernel. 
uname -rv
2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006

---

### Post by pmaciver on 2006-11-22
Yes, I found the same to be true when I install Edgy yesterday, although I did also manually install the latest version of Alsa as well and now everything is working fine.

---

### Post by joe.turion64x2 on 2006-11-22
Hello, it appears this is a club for Acer users for I have a 5102WMLi too.

I am running Ubuntu 6.10 32 bits and everything is excellent except OpenOffice.org (but not the program itself, I think it is not fully integrated with the environment), have you had any problem with that suite?

Something else, did you keep all the partitions the hard disk came with? Do you see a strange screen (something related to the hard drive, with many numbers) while booting in Ubuntu?

---

### Post by pmaciver on 2006-11-22
Well I haven't really used the office suite on this machine yet. In fact I hardly have cause to use it, I am a software developer so I use more the developer type tools with this machine.

As for my hard disk I did not keep the same partitions that came with the disk, I partition up my disk quite extensively so that in the case that I have to reinstall my operating system I can be up and running very quickly.

FYI this is how my disk is partitioned (all ext3)

/dev/hda1             1.9G  134M  1.7G   8% /
/dev/hda8              89M   13M   72M  15% /boot
/dev/hda5             9.9G  2.8G  6.6G  30% /home
/dev/hda9             9.9G  175M  9.2G   2% /opt
/dev/hda7             9.9G  129M  9.3G   2% /tmp
/dev/hda6              20G  2.9G   16G  16% /usr
/dev/hda11            9.9G  544M  8.9G   6% /usr/local
/dev/hda13            9.9G  937M  8.5G  10% /var
/dev/hda14             10G  129M  9.3G   2% /vmware
/dev/hda10            9.9G  235M  9.2G   3% /www

Hope this helps

---

### Post by joe.turion64x2 on 2006-11-22
That is an impressive partition table, you really exploit your hard drive. In my case, since sometimes I am forced to use Windows, I had to preserve most of the original partitions (just resized the third one to make room for Ubuntu).
Do you know if Ubuntu can corrupt my FAT32 partitions (it's an odd idea from Acer to bundle the system with FAT32)?
Something else, Is your bootup process smooth?

---

### Post by joe.turion64x2 on 2006-11-25
I don't care any longer about of this since I am now installing Fedora Core 6 in my Aspire (I am writing this from my Sempron), Fedora 5 works fine and is very stable, I believe FC6 is fine too.
The fact that entirely drove my out of Ubuntu was that after some weeks using the system, it became unusually slow and, out of the sudden, it refused to work ("can not find tty" it said). Fortunately I was able to backup my files. According to several posts I read that unusual behavior was produced by the custom layout I kept for my partitions. Unfortunate though.
Cheers and good luck.

---

