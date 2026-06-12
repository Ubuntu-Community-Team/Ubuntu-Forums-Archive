---
title: "Max display resolution"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by davidself1001 on 2008-02-14
I have a GeForce 6200 AGP that has a max res of 2048X1536 and a 24" Acer monitor that can support up to 1900X1200 but my max resolution option in the preferences->Screen Resolution is only 1600X1200.  Do I have something set wrong or is there some limitation in Linux that I don't know about?

---

### Post by taurus on 2008-02-14
Have you installed a nvidia driver for your graphic card?

---

### Post by davidself1001 on 2008-02-14
Yes.  I loaded the latest version.

---

### Post by davidself1001 on 2008-02-14
Is there a max display resolution for Ubuntu?

---

### Post by davidself1001 on 2008-02-14
Bump for help!

---

### Post by stevejesus on 2008-02-14
Do this;
```
sudo dpkg-reconfigure xserver-xorg
```

This first steps will be obvious.  Later in this script, it will propmt you to select all the modes that your display is capable of.  Make sure and select 1900x1200 and you should be golden.

---

### Post by stevejesus on 2008-02-14
Alternatively, if you have installed the "nvidia-settings" package, you can use its GUI tool to redetect your display.

---

### Post by davidself1001 on 2008-02-14
Thank you sir.  I will give that a try when I get home tonight.

---

### Post by oldsoundguy on 2008-02-14
I have the same card on two of my Gutsy boxes.  I used the third party program ENVY  to install the drivers and related software on all three (third is running a 5500).  It even installed the rotational software (had to make a mod in the X11/xorg and add an option, but otherwise flawlessly.

---

### Post by ender20852 on 2008-02-15
Well I also have this card and learned something recently I never thought to look for.  The max resolution for the **digital side** is actually 1600x1200 which is far far lower  then the analog side.  So if you are hooking up your monitor digitally that may be your issue.  Try running on the analog side.

My setup is such that I am running my old 24" analog monitor on the digital side at 1600 x 1200 and my new 24" flat panel widescreen monitor on the analog side at 1680x1050.  Pretty stupid I know to have to use adapters to pick a side but there you have it.

I was very unpleased to learn this but then again was a cheap card and the system is up and running so I guess I can live with it.

---

