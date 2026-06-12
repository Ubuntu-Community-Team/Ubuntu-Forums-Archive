---
title: "Resolution woes (1200 * 800)"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by JC Denton on 2007-04-11
Just installed 6.10 on my laptop (an Asus 6k series) and whatever I do I cannot switch to 1200 * 800 resolution.
Initially I tried setting the resolution using 
sudo dpkg-reconfigure xserver-xorg
and seeing as that failed (despite checking the 1200*800 box it did not show up in the select resolution dialog) I edited xorg.conf to support the mode and commented out the other resolutions. Now I am able to select 1200*768 and smaller but no 1200*800! 
Obviously things don't look right atm. Distorted text mainly.


Also, web pages scroll terribly in firefox. Very laggy. And the monitor has some white distorting lines flickering across occasionally.

Thank you for your help.

---

### Post by ramjet_1953 on 2007-04-12
Are you sure that it should be 1200 X 800?

That is an odd screen resolution! 

Usually on an LCD widescreen it is 1280 X 800.

That aside, what graphics chipset do you have?

You may need to download a driver.

Once we know what graphics chipset you have, we can suggest a fix.

Regards,
Roger :cool:

---

### Post by JC Denton on 2007-04-12
I have just found a fix for my problem:
[http://ubuntuforums.org/showthread.php?t=136183](http://ubuntuforums.org/showthread.php?t=136183)

The resolution in the post described above is also 1200*800.

Everything is looking nice n crisp now. Firefox too, is scrolling smoothly. (Only thing left is to get my backspace button to return me to the previous page instead of up. Same for right alt + arrow left/right. This usually works but not on this install)

Thank you for your efforts tho. :)

---

### Post by ramjet_1953 on 2007-04-12
Intersting!

If you have a look at dhm's xorg.conf file in the link you gave me, his resolution is set to 1280 X 800 not  1200 X 800!

Regards,
Roger 8-)

---

### Post by JC Denton on 2007-04-13
That is true but he also mentions his preferred resolution is 1200*800.

The preferred resolution dialog is now showing 1280*800 - exactly how we want it.

Thanks.

---

### Post by JC Denton on 2007-04-22
Upgraded to F.F. and when trying to enable desktop effects the entire screen blanks out - turns all white. Only when alt-tabbing are some edges visible. 

Are drivers for your gc automatically installed during installation if they are available?
How can I find out whether drivers are installed? According to xorg.conf I have sis drivers installed but that is because I copied the config from the page linked to in my previous post.
Where can I find the drivers for my m760gx / how are they installed?

thanks

---

### Post by carlossl on 2007-06-28
> **JC Denton said:**
> Upgraded to F.F. and when trying to enable desktop effects the entire screen blanks out - turns all white. Only when alt-tabbing are some edges visible. 

Are drivers for your gc automatically installed during installation if they are available?
How can I find out whether drivers are installed? According to xorg.conf I have sis drivers installed but that is because I copied the config from the page linked to in my previous post.
Where can I find the drivers for my m760gx / how are they installed?

thanks

Hey what's up JC Denton, I have the same graphics card, and as far as I know, you can't enable desktop effects... I have used Fedora Core 7 and Ubuntu Feisty 64, and none of them let me use desktop effects, BUT you can adjust your resolution in a very easy way (no need of modifying xorg.conf). Just follow the instructions on screen of this command:
```

sudo dpkg-reconfigure xserver-xorg

```
If there's something you don't understand, just leave it blank or with its default answer, and just be careful when you get to the part where you select the resolution, if you have an acer 5000 aspire like me, it is 1280x800.

Good luck!

---

