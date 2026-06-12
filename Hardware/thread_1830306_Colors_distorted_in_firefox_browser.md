---
title: "Colors distorted in firefox browser"
date: 2011-08-21
forum: Hardware
---

### Post by luvshines on 2011-08-21
Recently installed Ubuntu 10.10 on my Thinkpad W500 laptop.
Installed the graphics driver which were recommended with 
Faced an issue with no desktop on startup and changed the GPU mode as mentioed in following link:
[http://ubuntuforums.org/showthread.php?t=1622003](http://ubuntuforums.org/showthread.php?t=1622003)

That fixed the issue with desktop and everything worked smooth.

Now facing weird issue with the pictures in firefox browser.
Many times the colors of the pictures gets distorted, all covered up in green/pink tint

I am observing this only in the firefox browser display. If I download the same pic, it looks fine. Firefox version is the default one - 3.6.10

Any suggestions how to fix this ?

---

### Post by An Sanct on 2011-08-21
For starters, update your firefox to the last official version (I think it is something like 4.0 or 5.0 ... I Use the alpha - 9.0)

That should help.

---

### Post by luvshines on 2011-08-21
> **An Sanct said:**
> For starters, update your firefox to the last official version (I think it is something like 4.0 or 5.0 ... I Use the alpha - 9.0)

That should help.

Nope!! Switched to 5.0.1, still the same issue :(

---

### Post by lovinglinux on 2011-08-24
It is a color management issue. See the last item on [this list]("http://www.webgapps.org/tutorials/firefox/troubleshooting/rendering-issues-and-solutions").

---

### Post by luvshines on 2011-08-24
> **lovinglinux said:**
> It is a color management issue. See the last item on [this list]("http://www.webgapps.org/tutorials/firefox/troubleshooting/rendering-issues-and-solutions").

The default value for that parameter in the firefox was 2
Changed it to 0 and looks to be fixed :D

Thanx a tonne !!

BTW, what side effects may changing that value from 2 to 0 have ?

---

### Post by lovinglinux on 2011-08-24
> **luvshines said:**
> The default value for that parameter in the firefox was 2
Changed it to 0 and looks to be fixed :D

Thanx a tonne !!

BTW, what side effects may changing that value from 2 to 0 have ?

None that I am aware of.

---

