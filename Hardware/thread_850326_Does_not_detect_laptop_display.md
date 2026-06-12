---
title: "Does not detect laptop display"
date: 2008-07-05
forum: Hardware
---

### Post by JPNinja on 2008-07-05
Hey everyone. I have a serious issue. I don't remember what I was doing at the time, although I'm sure I wasn't messing with the video or screen resolution settings, but I just rebooted and Ubuntu won't detect my laptop display. It's really weird. And the screen resolution is set **really really** low. I can't change it, and it seems to have no idea what kind of screen I'm using. I tried booting from all the kernels at the boot manager (I don't even know what those do), but I keep having the same issues.
I have to use my Vista partition until I figure this out, so a little help would be great.
Sorry, I'm kind of a noob, but take some time to help me out.
---UPDATE---
Sorry, I forgot my information. I'm using an HP Pavilion dv9700t (dv9000) with an nVIDIA 8600m GS card and a 17" screen.

---

### Post by prshah on 2008-07-05
> **JPNinja said:**
> 
although I'm sure I wasn't messing with the video or screen resolution settings, 
and it seems to have no idea what kind of screen I'm using.

I have to use my Vista partition until I figure this out, 


Boot to recovery mode, then give the command```
mv /etc/X11/xorg.conf ~
``` This will remove all settings for your graphics card and display, so that they will be reset to defaults on the next startup.

---

### Post by JPNinja on 2008-07-08
> **prshah said:**
> Boot to recovery mode, then give the command```
mv /etc/X11/xorg.conf ~
``` This will remove all settings for your graphics card and display, so that they will be reset to defaults on the next startup.

"xorg"? Doesn't that just apply to XFice or something like that? I'm using Ubuntu 8.04 LTS. Gnome.
It said that the directory didn't exist.

---

### Post by avtolle on 2008-07-08
No, that particular file has application to Gnome as well. The real question here is why you received the error message you did. Did you copy and paste the command exactly as given? Linux is case sensitive, so that if you typed "x11" rather than "X11", e.g., you would get that error.

---

### Post by JPNinja on 2008-07-21
Now I have another problem. When I got the command right, I rebooted, and to my delight, the screen resolution was fixed. But the settings and drivers are worse than when I installed 8.04. My Wi-Fi and sound were dysfunctional. So I used *sudo aptitude install linux-backports-modules-generic* but apparently I had the drivers (come to think of it I had already installed them) and this did nothing to fix my problem when I rebooted.
Help?

---

### Post by BiiPiiGii on 2009-10-05
Actually I'm having a problem where my screen wont even show up at all.  I tried to go under System>>Preferences>>Display, but it doesn't exists in my menu.  I'm not sure what to do about this.

---

