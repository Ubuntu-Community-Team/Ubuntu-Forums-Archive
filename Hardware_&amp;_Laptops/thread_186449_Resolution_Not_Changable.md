---
title: "Resolution Not Changable"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by Koskun on 2006-06-02
I have a Dell Inspiron 1100 with onboard Intel graphics.  Both the boot of the Live and after a complete install the resolution is stuck at 640x480.

Needless to say it is very annoying to only be using half the screen.

Where can I get, and install, a working driver, or is there a file somewhere I have to change to enable me to change the resolution.

I have virtually no experience with linux, and any hand holding help would be appreciated.

---

### Post by nalmeth on 2006-06-02
You can hand edit the /etc/X11/xorg.conf file, but for a wizard type reconfiguration, open a terminal

applications - accessories - terminal

```
sudo dpkg-reconfigure xserver-xorg
```

pick default's everywhere unless you know better, and when you get to screen resolution's pick the extra ones you need.

---

### Post by boxubi on 2006-06-02
i had this problem using my video card's DVI port. Using the standard video connection I can use all my monitor's resolutions.

---

### Post by hardawayd on 2006-06-02
i have a dell latitude 800 and can not change resolution after installing the nvidia driver.  There is not place that i can find where you pick what monitor you have.  Does anyone know where monitor info is stored.  This release is lacking some vital functionality with regard to screens.

---

### Post by fast1 on 2006-06-02
I solved a similar problem with 915resolution. However, it did not work with the external monitor.

---

### Post by evilregis on 2006-06-02
[QUOTE=nalmeth]You can hand edit the /etc/X11/xorg.conf file, but for a wizard type reconfiguration, open a terminal

applications - accessories - terminal

```
sudo dpkg-reconfigure xserver-xorg
```

pick default's everywhere unless you know better, and when you get to screen resolution's pick the extra ones you need.[/QUOTE]

This worked perfectly for me on an HP dc7600 with onboard video.

There seemed to have been a glitch at first, though.  When I got to the autodetect monitor page and clicked OK the screen went blank and brought me to TTY1.  I hit CTRL-ALT-F7 and it brought me to the login page, still at 640x480.

I tried it again, and the second time everything went smoothly.  So if yours borks on the autodetection the first time, give it another shot and see if you're luckier the second time around.

---

### Post by wbmj on 2006-06-02
I've install Ubuntu to an 1100 in the past. The first thing you need to do is make sure you have the most recent BIOS install. The 1100 uses shared memory for its video. The original BIOS doesn't allow for this. Once you have upgrade the BIOS from Dell you will be able to use sudo dpkg-reconfigure xserver-xorg

---

### Post by joe_lace on 2006-06-21
With mine all I had to do was upgrade the bios to A32 and then the new resolutions were already there without configuring anything.

---

