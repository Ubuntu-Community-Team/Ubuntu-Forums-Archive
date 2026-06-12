---
title: "Im new..."
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by CH3ST3R128 on 2009-10-14
Hello everyone....im new to ubuntu coming from windows and i have to say its pretty nice...but i have one question...im using a 15" screen and everything seems too bug. Is there a driver or something i can download to fix this? i already adjusted the resolution settings but to no avail. any help would be great...thanks!

---

### Post by MelDJ on 2009-10-14
welcome. what version of ubuntu are you using?

---

### Post by CH3ST3R128 on 2009-10-14
oh sorry!...that would be helpful info! 9.04(off the top of my head) i now its the latest one just downloaded no more that 2 hours ago

---

### Post by MelDJ on 2009-10-14
what is your graphic card? 
try installing it by going to system-administration- hardware drivers. see if there are drivers for it there. if there are, enable them

---

### Post by CH3ST3R128 on 2009-10-14
im using this pc
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037)

it says the video card is onboard video and is an Intel GMA 950

oh and i tried going to the hardware drivers but theres nothing there.

Thanks

---

### Post by MelDJ on 2009-10-14
edit. when you mean by the screen has bug? 
is it choppy? or the colors are not correct?

---

### Post by CH3ST3R128 on 2009-10-14
its blank

---

### Post by MelDJ on 2009-10-14
is the screen choppy or the colors out of sync?

---

### Post by CH3ST3R128 on 2009-10-14
no, just everything is bunched up.

---

### Post by MelDJ on 2009-10-14
could you send a screenshot of the screen?

---

### Post by theozzlives on 2009-10-14
Intel 950 should work out of the box (may have problems with Compiz). Did you do a MD5SUM and run "Check CD for errors"?

---

### Post by CH3ST3R128 on 2009-10-14
here you go. I'm just guessing but there has to be a way to make everything smaller right?

[IMG]http://i35.tinypic.com/w6txea.png[/IMG]

[IMG]http://i37.tinypic.com/10fc19k.png[/IMG]

---

### Post by theozzlives on 2009-10-14
I'm running 1280x800 with an Intel 965 w/64 MB RAM. Yours should be able to do 1024x768. Did you go to System > Preferences > Display?

---

### Post by CH3ST3R128 on 2009-10-14
heres another one if it helps?
[IMG]http://i37.tinypic.com/e9j96v.png[/IMG]

---

### Post by CH3ST3R128 on 2009-10-14
yup. the highest resolution i have is 832 x 624 (4:3)

---

### Post by theozzlives on 2009-10-14
try hitting Alt+F2, and in the box type```
gksu gedit /etc/X11/xorg.conf
```and hit run. replace where it says > driver intel to > driver vesasave, reboot and see what that does.

---

### Post by CH3ST3R128 on 2009-10-14
all i have is this...besides the comments of course


Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    832 624
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

---

### Post by theozzlives on 2009-10-14
try going to Applications > Accessories > Terminal and type:```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by CH3ST3R128 on 2009-10-14
im googling and going thru the forums and it seems that some people are installing intel 915gm...anybody think they could help me with this?

---

### Post by CH3ST3R128 on 2009-10-14
i get a sort of dos box saying:

The default keyboard layout selection for the Xorg server will be based   &#9474; 
 &#9474; on a combination of the language and the keyboard layout selected in the  &#9474; 
 &#9474; installer.                                                                &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Choose this option if you want the keyboard layout to be redetected.  Do  &#9474; 
 &#9474; not choose it if you want to keep your current layout.

its pretty much asking me to auto dectect my keyboard which im going to choose yes to haha

---

### Post by theozzlives on 2009-10-14
your device section should look something like this:
> Section "Device"
 Identifier "Configured Video Device"
 Driver "intel"
EndSection

---

### Post by CH3ST3R128 on 2009-10-14
woah sorry just realised i pressed the enter key at the first propmt. it asked me if i wanted to Use kernel framebuffer device interface?  i selected yes and then went thru all th ekeyboard layout info.

sorry i made a mistake.

---

### Post by CH3ST3R128 on 2009-10-14
no it just has 

> Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by theozzlives on 2009-10-14
The option is new, see if you can change your resolution now.

---

### Post by CH3ST3R128 on 2009-10-14
WOAH!...that is awesome i was able to change it to 1024 x 768...

Thanks alot!!...

so the fix was enabling  the "kernel framebuffer device interface?"

---

### Post by theozzlives on 2009-10-14
Jaunty has a hard time with Intel video, sometimes it needs a little coaxing. You're quite welcome... that's why we are here. :)

---

### Post by CH3ST3R128 on 2009-10-14
hey just some things i was trying out afterwards and maybe this will be helpfull to you in the future.

If i go to:

System>Adminitration>sypnatic

and in the search box i type in i915 and install "xserver-xorg-video-intel-dbg" it adds that intel field to the field you had me look at...make sense?

---

