---
title: "ADS Tech DVD Xpress DX2 Installation/driver problems"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by tipdrinker on 2007-09-17
Hi i bought this dvdxpress yesterday and i don't seem to be able to make it work. I did a lot of googling and found this post on a blog
[linux-support-for-ads-dvd-xpress-dx2]("http://jeff.ourexchange.net/2007/07/22/linux-support-for-ads-dvd-xpress-dx2/")

I managed to install wis-go7007 after much effort and applied the patch but it still wasn't working so i tried to re-install it. However when i tried again i got this error...

kev@89-125-52-231:~$ cd ~Desktop
bash: cd: ~Desktop: No such file or directory
kev@89-125-52-231:~$ cd /home/kev/Desktop/wis-go7007-linux-0.9.8
kev@89-125-52-231:~/Desktop/wis-go7007-linux-0.9.8$ make

***** Using kernel source in /usr/src/linux-headers-2.6.20-16-lowlatency *****

make modules -C /usr/src/linux-headers-2.6.20-16-lowlatency M=/home/kev/Desktop/wis-go7007-linux-0.9.8/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-lowlatency'
  CC [M]  /home/kev/Desktop/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.o
/home/kev/Desktop/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:20:26: error: linux/config.h: No such file or directory
/home/kev/Desktop/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c: In function ‘go7007_do_ioctl’:
/home/kev/Desktop/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:942: error: ‘AUDC_SET_INPUT’ undeclared (first use in this function)
/home/kev/Desktop/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:942: error: (Each undeclared identifier is reported only once
/home/kev/Desktop/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:942: error: for each function it appears in.)
make[2]: *** [/home/kev/Desktop/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.o] Error 1
make[1]: *** [_module_/home/kev/Desktop/wis-go7007-linux-0.9.8/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-lowlatency'
make: *** [all] Error 2
kev@89-125-52-231:~/Desktop/wis-go7007-linux-0.9.8$ 

I'm confounded:(

---

### Post by tipdrinker on 2007-09-17
i searched regarding the error message 

error: linux/config.h: No such file or directory

and its something to do with the file no longer existing in the current linux kernel but im not sure what to do regards this

---

### Post by i_magic on 2007-09-23
Hey man,
Didja ever resolve your situation? If not, I might be able to help a brother out. I have a package for Gentoo, which was patched for 2.6.22 kernel. I had to manually apply the patch for ADS Tech DVD Xpress DX2 and it compiled fine. I plugged in the card and it looks like it got detected, I am gonna see if it actually works now. (Need to install MythTV, etc)

If you want I can send you my patched driver and you can try to install it.

Hit me up if you are interested.

DZ

---

### Post by i_magic on 2007-09-23
Du-u-u-de, it works! I just tried it with gorecord and it captured video in MPEG4. I didn't have anything plugged into audio, so I dunno if audio works, but it does identify audio channel (when you run gorecord without params), so I think we should be styling.

DZ

---

### Post by tipdrinker on 2007-09-24
that sounds great. thanks for the help

---

### Post by joecats on 2007-09-24
I have got almost the same message you related. Did you find a solution to the problem? Consider I am a dummy and couldn't get difficult explanation.

---

### Post by i_magic on 2007-09-24
tipdrinker: you've got mail. :popcorn:

joecats: I can send you patched wis-go7007 package, which you will need to compile and install.

DZ

---

### Post by spainjd on 2007-10-16
I'm having the same issue.

i_magic, is there any way you could attach the patched source to the forum, so everyone might benefit?

Thanks

---

### Post by i_magic on 2007-10-16
I didn't know you can do that. But now I do.
So here ya go. \\:D/

DZ

EDIT: To compile this package you need to install kernel source first

---

### Post by spainjd on 2007-10-16
Dude, you are awesome.  :) I was having trouble tracking down the right patches, and actually getting them to work together.  It works flawlessly, and the quality is SO much better than with any capture program I could get working in widoze.

I did have 2 problems though for anyone else having trouble:

1. When you install make sure you do "sudo make install USE_UDEV=y", otherwise it will try to use hotplug instead of udev and the install will fail, since ubuntu doesn't use hotplug.

2. I don't think this issue is necessarily related to this driver, but to alsa instead, but awhile back, I bought a new sound card and I had to compile and install the new alsa drivers.  However, I didn't uninstall the alsa packages for feisty, since so much depends on them.

If you get several lines in you're dmesg output that say

"snd_go7007: disagrees about version of symbol ..." and
"snd_go7007: Unknown symbol ..."

when you plug in the device or try to load the driver manually with modprobe, you may have to do

sudo modprobe -f go7007-usb              (-f for force)

to get it to work.

---

### Post by spainjd on 2007-10-16
Sorry for posting again so quickly, but I found a work-around for the alsa driver issue (#2 situation, I described above)

If you add the following 2 lines before the "exit 0" to /etc/rc.local

/sbin/modprobe -f go7007-usb
/etc/init.d/udev restart

then you're DVD Xpress DX2 will be completely plug and play as it should be without having to force load the driver every time you plug it in.

---

### Post by strfmstr on 2007-10-18
Great job, guys; got mine working tonite and using the README recorded my first 60 second avi. Has anyone gotten it to work with vlc? I've tried with /dev/video0 and /dev/dsp2 (as reported by gorecord) without any luck.

---

### Post by Stuart_1745 on 2007-11-14
hey I have one of these and I just installed mythbuntu 7.10 on a spare box. 

but every time I try to make it I get this.


make: execvp: ./checkfwdir: Permission denied
make modules_install INSTALL_MOD_PATH= \
                -C /lib/modules/2.6.22-14-generic/build M=/var/lib/mythtv/pictures/wis-go7007-linux-0.9.8/kernel
make: *** /lib/modules/2.6.22-14-generic/build: No such file or directory.  Stop.
make: *** [install] Error 2


any idea why. . . or how I can fix it?

edit:
[http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy)
this website helped me get it to work now all I have to do is get myth tv to play with it

---

### Post by nashjc on 2008-04-21
I found this thread very helpful to get things going -- my ADS DX2 won't work on Windows on the box I need to use. Sigh. However, I do now have video going with gorecord, but am getting no audio. There are msgs in dmesg saying "Error 71" and essentiallyh that the audio cannot be attached. 

Anyone else had these sorts of problems. I suspect I'll need to do some sort of manual attachment of the USB, but that's new territory for me.

JN

---

### Post by wimpzap on 2008-04-21
hey guys im running linux ubuntu gutsy im kinda new to this can someone tell me how to install these drivers with in depth details please all help will be  highly appreciated

---

### Post by nashjc on 2008-04-25
It is a bit defeatist, but I got hold (legally) of a WinXP SP2 install disk and the ADS Capwiz now works, though I have to ignore "your driver is outdated" on every launch. M$ tries to install one that doesn't work, while the one from ADS that came with the device does. And there is a workable video editor -> dvd solution. Not great, but workable.

So I'm able to do the capture I wanted, but must admit I'm still interested in doing so in Linux, though the pressure is off to absolutely get it working yesterday. If anyone has thoughts on the lack of audio, or where to look for a solution, please post.

JN

---

### Post by wolfmanyoda on 2008-05-15
> **wimpzap said:**
> hey guys im running linux ubuntu gutsy im kinda new to this can someone tell me how to install these drivers with in depth details please all help will be  highly appreciated
Hello, I'm also quite new to Ubuntu, with just a tiny bit of experience with Linux in other distros. I just installed Hardy Heron and would really appreciate it if someone could walk me through the process of getting my ADS Tech working. 
Thank you

---

### Post by nashjc on 2008-05-15
wolfman and others may want to try [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy)  as mentioned above. I got the video capture to work, but not the audio. I suspect the latter is due to particular issues with the audio circuitry on my system more than the s/w.

JN

---

### Post by wolfmanyoda on 2008-05-15
nashjc--thanks for that link, I'll see what I can do with it.

---

