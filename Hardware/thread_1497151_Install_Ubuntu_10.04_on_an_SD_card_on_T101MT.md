---
title: "Install Ubuntu 10.04 on an SD card on T101MT"
date: 2010-05-30
forum: Hardware
---

### Post by hanoc on 2010-05-30
Hi,

I've bought an asus eee pc T101MT and I decided I did not want to use a conventional hard drive as my main hard drive to save battery.
For this reason I decided to install ubuntu on an SD card.
So far I've used a regular kingston 4GB card but I'm planning on moving to a fast SD card once everything works.
As for this moment my system works correctly and quite fast and I keep my hard drive "powered down" most of the time.
I haven't noticed a big difference in battery usage but I did not try the regular hard drive for more than a couple of days before switching to the sd card.

What does not work is suspending the machine. More info latter on.

Most of what i have accomplished It's thanks to the general [T101MT](http://ubuntuforums.org/showthread.php?t=1468376) thread and as for the SD card instalation I've followed the instructions [here](http://foro.noticias3d.com/vbulletin/showthread.php?t=298091) (in spanish).

The steps are:
1. create a bootable usb with ubuntu. I choosed netbook remix. I really like the launcher but of course the instructions will work with any gnome based ubuntu (the optimitzation is not confirmed to be working in kde, sorry).
2. get an sd card. I guess a really fast card would help the overall performance. I'm planing on buying an [30MB/s card](http://www.sandisk.com/products/imaging/sandisk-extreme-sdhc-cards-). If anyone has a better idea please say so.
3. install ubuntu as normal selecting the sd card as your target. Remember to place both the bootloader and the / partition on the sd card. I decided not to create swap space and only use ram[1].
4. optimize ubuntu to work on T101MT following the instructions on this thread [TODO][2].
5. stop the hard drive from starting on boot:
```

gksudo gedit /etc/rc.local

```
add hdparm -Y /dev/sda before exit.
If you've done the T101MT optimitzation the file should be like:
```

#blah blah blah
hdparm -Y /dev/sda #spin down hard drives
setpci -s 00:02.0 f4.b=ff #set brightness to hardware max  
twofing --wait #start screen multitouch
exit 0

```

6. change the record of access times to something less stresful for the card than realtime.
```
gksudo gedit /etc/fstab
```
change
seartch for the row with / as the mount point and change realtime for noatime.
It shoud be something like that:
```
UUID=46fcfdb5-ead8-4cdc-971c-e9558ade2ac3 /               ext4    noatime 0       1
```
Until now I had errors=remount-ro as an option but I thing it made my system mount on read only after sleep. I'm trying errors=remount right now. I'll follow up with some conclusions once I've tested it.

don't close fstab yet...

7. make the logs write to ram.
in fstab change the tmpfs lines to that:
```
tmpfs /tmp tmpfs defaults 0 0
tmpfs /var/tmp tmpfs defaults 0 0
tmpfs /var/log tmpfs defaults 0 0
```


8. Change the hard disk access optimization from elevator to none.
Copied vervatim from [here](https://help.ubuntu.com/community/AA1/Using).

Edit /etc/default/grub using your favorite editor, and add "elevator=noop" to the list of GRUB_CMDLINE_LINUX_DEFAULT values. The corresponding line will then look like:

GRUB_CMDLINE_LINUX_DEFAULT="elevator=noop quiet splash"

Then rebuild GRUB2 configuration files:

$ sudo update-grub

9. Optimize other programs.
I use firefox without cache to avoid multiple writes to the sd card. To do this just write about:config

10. reboot!


Right now I'm having some problems sleeping and hibernating I guess it's mount options and t101mt drivers fault respectively. I'll follow up with solutions when i found them.

I would be very glad of any suggestion you think of and to answer any questions but I must say in advance that I did not came myself with anything wrote in this post. That I just wrote it all together (and it may contain errors of my own to).
i hope this steps are useful to someone and also to get new ideas on how to improve the T101MT on a SD card performance.


[1] My T101MT has 2GB ram and I think that being a netbook and not planing to do anything resource intensive on it It can go without swap. I don't want my SD card to get worn out with the multiples accesses the swap space would do. I think that in newer versions of ubuntu there is no problem in no having swap space at all. Please correct me if I'm wrong.
[2] right now I have working. Multitouch screen, multitouch trackpad, rotate screen, full birghtness, photo camera. I don't have hibernation or video recording working.

---

### Post by therightuser on 2010-05-30
I`ve installed the OS on a SD card on T101MT, the major problem i`m facing is when back from suspending mode, the touchscreen doen not respond, is there any tweak to correct this? Best regards

---

### Post by hanoc on 2010-05-30
Hi therightuser,

Did you try [this solution](http://ubuntuforums.org/showpost.php?p=9335669&postcount=65)

If you haven't I highly recommend that you read the thread. It's 11 pages long, but most of the important stuff is summarized in the first post.

I've tried to remove the option errors=remount-ro from /etc/fstab but the sd card gets read only after sleep.

Does anyone know why? What is the default behavior of errors?
I've tried to get the line to:
```
UUID=string / ext4 noatine,errors=remount 0 1
```
but it gave "errors=remount" unknown option
So right now my etc/fstab is:
```
UUID=string / ext4 noatine 0 1
```
wich produces the same results that 
```
UUID=string / ext4 noatine,errors=remount-ro 0 1
```

I am afraid maybe remount-ro is the default behavior but I haven't found documentation for the etc/fstab options.
Does anyone know where to look? I tried man and Google with no success. I'll try again after resting some hours, but in the meantime I'll be glad to take any suggestion.

---

### Post by hanoc on 2010-06-02
I've found the answer here:
[http://en.gentoo-wiki.com/wiki/Acer_Aspire_One_A110L#SD_Cards_and_suspend](http://en.gentoo-wiki.com/wiki/Acer_Aspire_One_A110L#SD_Cards_and_suspend)

I'll reply or edit this posts once I've confirmed it to work.

EDIT: Now I know that what will solve the problem is to get the kernel to accept the SAFE_UNMOUNT unfortunately my gentoo times of compiling the kernel manually are long gone and I don't know how to do it.
There is some (i guess only partial) info here:
[http://patchwork.ozlabs.org/patch/49333/](http://patchwork.ozlabs.org/patch/49333/)

---

### Post by ohssss on 2010-08-28
> **hanoc said:**
> Hi,

I've bought an asus eee pc T101MT and I decided I did not want to use a conventional hard drive as my main hard drive to save battery.
For this reason I decided to install ubuntu on an SD card.
So far I've used a regular kingston 4GB card but I'm planning on moving to a fast SD card once everything works.


I have just come across the idea of installing ubuntu on the SD card and see your sharing. I am curious about whether the booting time and application loading time, such as firefox, is faster for the SD card than the traditional harddisk. 

If it is really faster, then it seems that it worth to use an SD card as the main partition because you can now have both a fast response computer and a large data storage with almost no side effect. Have you tried the 30MB/s card you mentioned? What is the result.

---

### Post by hanoc on 2010-09-09
I did not try it with a 30Mb/s but the general speed of the system was not bad.
Whenever firefox tried to donwload a file the general speed of the system reduced a lot. I guess (hope) that this would be solved with a faster card.

I stoped running that system because I had problems with suspending. If you want to be able to suspend or resume you have to recompile your kernel disabling the unmount mediums on suspend.

I don't remember the name of the feature exactly but what it does is that, by default, when you suspend it unmounts all ejectable media.
In ubuntu you can only change that by recompiling the kernel and my days of thinkering with kernels are long gone so I just moved everything to the hard drive.

Of course I also had issues with space, I was using only 4gb.

If you could get a 8gb 30m/s sd card and solve the automatic unmount you should be good.

Let me know how it turns out!

---

