---
title: "Dell Inspiron 6000d with ATI x300 128meg"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by Ainvar on 2005-04-25
I am trying to install ubuntu and kubuntu 5.04 onto my laptop and when it gets to loading the X part to start the install my lcd starts giving me flashbacks of a really bad lsd trip....

Is the ATI x300 on the Dell Insprion 6000 not supported in ubuntu? I am able to install mandriva 2005 and suse 9.3 with no issues but I prefre ubuntu since it is slick, up to date, and best of all no bloated footprint.

---

### Post by chrisubuntu on 2005-04-26
[QUOTE=Ainvar]Is the ATI x300 on the Dell Insprion 6000 not supported in ubuntu? I am able to install mandriva 2005 and suse 9.3 with no issues but I prefre ubuntu since it is slick, up to date, and best of all no bloated footprint.[/QUOTE]

Not sure how useful this info will be buuttttt:
I have installed  5.0.4 on my new Inspiron 9300 which also has an x300. The default installation allowed  KDE to display nicely, but did not include any hardware acceleration. After browsing the forums i found

 [http://ubuntuforums.org/archive/index.php/t-24557.html](http://ubuntuforums.org/archive/index.php/t-24557.html)

I followed the instructions and BAM! now I have hardware accelleration also.

---

### Post by Ainvar on 2005-04-26
Thanks for the reply but the thing is, I am not able to even get it installed since it craps out on the video framebuffer after it tried to detect my hardware on pre installation.

I appreicate the reply and I know if I can get it installed it would work wonderfully since Suse 9.3 and mandriva (lame name) 2005 limited installed with no issues.

---

### Post by Ainvar on 2005-04-27
So I guess Ubuntu will not run on a dell inspiron 6000d laptop with an ATI x300 128meg card that is pcie.

Mandriva (mandrake) and suse 9.3 has no issues what so ever loading up on the laptop but ubuntu does. I dont know how to make it work and it seems nobody on this forum does either.

I have tried searching with every search string I could think of to see if anyone has encountered this before.


So long unbuntu until it can work on my laptop......

---

### Post by nikolokolus on 2005-04-27
[QUOTE=Ainvar]So I guess Ubuntu will not run on a dell inspiron 6000d laptop with an ATI x300 128meg card that is pcie.

Mandriva (mandrake) and suse 9.3 has no issues what so ever loading up on the laptop but ubuntu does. I dont know how to make it work and it seems nobody on this forum does either.

I have tried searching with every search string I could think of to see if anyone has encountered this before.


So long unbuntu until it can work on my laptop......[/QUOTE]

you may want to try adding the option VGA=771 at boot time and see if that helps any . . . I don't remember what it does exactly (and I've never had to use it myself thankfully) but I seem to remember reading somewhere that this can alleviate some of the graphical corruption people sometimes experience at boot time.

Hope that helps a little

---

### Post by chrisubuntu on 2005-04-28
[QUOTE=Ainvar]So I guess Ubuntu will not run on a dell inspiron 6000d laptop with an ATI x300 128meg card that is pcie.

Mandriva (mandrake) and suse 9.3 has no issues what so ever loading up on the laptop but ubuntu does. I dont know how to make it work and it seems nobody on this forum does either.

I have tried searching with every search string I could think of to see if anyone has encountered this before.


So long unbuntu until it can work on my laptop......[/QUOTE]

I'll send you my /etc/X11/xorg.conf and what I did to get the fglrx driver kicking up some hardware accellerated action if you want to give that a go.. probably worth while. (when I get home from work) 

The difference between our laptop configs is no doubt the LCD monitor... the ATI card is most certainly supported by ubuntu and worked out of the box for me.

Chris.

---

### Post by Ainvar on 2005-04-28
That would be cool if I could see your configs, then is also assuming I can get the install to go. I will try the VGA-771 here now. Thanks for this bit of info. I also remember seeing this somewhere but I forgot where and what it was suppose to do.

Thanks again!!

---

### Post by Ainvar on 2005-04-29
wanted to say the vga=771 did the trick. I am know running kubuntu 5.04 on my Dell i6000d.

Now I will attempt the updated ATI drivers so I can get some 3d love!

Thanks again!

---

### Post by chrisubuntu on 2005-05-01
[QUOTE=Ainvar]wanted to say the vga=771 did the trick. I am know running kubuntu 5.04 on my Dell i6000d.

Now I will attempt the updated ATI drivers so I can get some 3d love!

Thanks again![/QUOTE]


Glad to hear it!


How did you go with the 3d action? =)

---

### Post by Ainvar on 2005-05-01
3d action is doing good, just having issues in gnome and kde where the fonts are very flakey and I get some blue and purple stripes through my kdm screen and some icons in the gui.

Working on that plus a few other things, things are going pretty smooth with almost all hardware I have.

Thanks again for the help!!

---

### Post by phatmaxx on 2005-06-04
Hi!

Yesterday i tried to bring 3d acceleration to my Dell i6000 with the fglrx driver but it didn't work^^

After activation at kernel and reboot all i had was a black screen, i don't know how to fix this.. Maybe the resolution is too high for the tft, although it worked without 3d acceleration at a resolution of 1680x1050  (display is 15,4" widescreen)..

How did you get this working on your i6000?

---

### Post by Strife on 2005-06-05
Add this option under the "Monitor" section of xorg.conf:

```
Option "MonitorLayout" "LVDS, NONE"
```

That should solve it. I had the exact same problem, and from some forum (which I know don't recall), I found this result.

---

### Post by Vorian on 2005-06-27
Helped me out too!
Thanks!

---

### Post by encinas on 2005-07-01
Hi,
 I had the same problem that you just reported about the screen  during install process. But the solution was to enter the bios setup and choose the option that resizes the image so that though your max resolution is for example 1680x1050 you can still see a 1024x768 without distorsion.

 Another problem I had with this computer was about the mouse. Scroll didn't work so I downloaded a vanilla kernel and patched it. Now everything is working moreless.

---

### Post by LodeRunner on 2005-07-25
Glad to hear you fixed it, but  I wanted to mention that I have the exact same laptop and video card and I had no problem with Ubuntu (Hoary.)  I haven't gotten acceleration to work, of course, but no LSD flashbacks or any other problems for that matter.

---

