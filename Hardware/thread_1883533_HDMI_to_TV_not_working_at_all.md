---
title: "HDMI to TV not working at all"
date: 2011-11-19
forum: Hardware
---

### Post by christia on 2011-11-19
Hi,

Ever since wiping off my windows from my Sony Vaio Z 540, i haven't been able to get the HDMI to work (i am trying to get my laptop connected to the TV). Seems most people who have HDMI problems is mainly sound related, so searching around has not given me many answers unfortunately. I am currently running Ubuntu 11.10

I have tried doing the following:

1) Installed NVidia driver - for some reason, doesn't work at all. I tried following the instruction in the below link, but didn't seem to help much
[http://answers.yahoo.com/question/index?qid=20111018014550AAuajuq](http://answers.yahoo.com/question/index?qid=20111018014550AAuajuq)

2) Followed the instructions in the below link - when i then try to open NVidia settings, i get an error saying my config file is not correct
[http://thecodecentral.com/2011/03/01/switch-to-external-monitor-connected-via-hdmivga-port-in-ubuntu](http://thecodecentral.com/2011/03/01/switch-to-external-monitor-connected-via-hdmivga-port-in-ubuntu)

3) i then try to fix my config following the below link, but that also doesn't seem to work (seems my "X" gets killed and then Ubuntu can't even boot and i need to reinstall)
[http://awesomelinux.blogspot.com/2009/11/ubuntu-910-karmic-nvidia-settings-parse.html](http://awesomelinux.blogspot.com/2009/11/ubuntu-910-karmic-nvidia-settings-parse.html)


Soooooo - i am completely on bare ground here. Does anyone have any idea as to how to do this?

---

### Post by pchongdo on 2011-11-19
Same problem here...when I attach my hdmi cable from my Acer Aspire Ubuntu 11.10 to my TCL HD TV the desktop wallpaper will show up and even the cursor if I move it right but my icons won't come up nor will any icons on my desktop.  Any suggestions are appreciated.  Thanks guys and gals.

---

### Post by papibe on 2011-11-19
Hi christia.

I check several Sony Vaio Z 540 specs pages, and there are models with Nvidia cards, and other with Intel integrated graphics.

Just to make sure you have the hardware, Could you post the result of this command?
```
lspci | grep -i vga
```

Now, in order to get details of your problem, Could you also paste the content of these two files:
```
/var/log/Xorg.0.log
/etc/X11/xorg.conf
```
Paste separately their content here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post the links to them.

Kind Regards.

---

### Post by christia on 2011-11-21
Sorry for the long wait - here are answers to what you asked for:

graphics stuff:

[http://paste.ubuntu.com/745132/](http://paste.ubuntu.com/745132/)

Var/... stuff:

[http://paste.ubuntu.com/745134/](http://paste.ubuntu.com/745134/)

Xll stuff:

[http://paste.ubuntu.com/745135/](http://paste.ubuntu.com/745135/)

Thanks a lot for the help and again sorry for the late reply, i sit in Hong Kong so a little bit time difference

---

### Post by papibe on 2011-11-21
christia:

you have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is. And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

I hope that helps,
Regards.

---

### Post by christia on 2011-11-21
Thanks. It seems like the best i could do would be to turn off my second graphics card but not to get the HDMI to work. Hopefully it will come in later editions.
 
It actually surprises me that even old versions of Windows could get everything to work flawlessly (even Windows versions older than my laptop) whereas for Linux i had problems with first volume and light control, then HDMI and a bunch of other stuff. Linux is far superior in many ways, but I think as long as things are this complicated to solve every time one changes, it will take a long time before it really gets widespread.

---

