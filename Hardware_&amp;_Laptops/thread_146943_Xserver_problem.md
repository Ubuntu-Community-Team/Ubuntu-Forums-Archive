---
title: "Xserver problem"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by lingon on 2006-03-19
Hi folks, bare with me on this one, I realise you proboably get a ton of these questions from ATI users ;) Anyway, I am totally new to linux but a quite experienced computer user so I should learn kinda quick. So, I'm trying to use the Live CD to get a taste of Ubuntu and all goes well and it loads nicely and all but then I get a blue box where it says that my Xserver has some kind of problem and if I want to view a report of it. I guess this is all about the video drivers and I've searched the forums and didn't really find anything that helped:( . Is there any easy way of solving this problem? Plz help.
/lingon

---

### Post by fimbulvetr on 2006-03-19
It's a pain, I know, but we're gonna need to see your /var/log/Xorg.0.log so we can see there errors.

If your internet connection works in the live cd, you can email yourself a copy by doing ```
cat /var/log/Xorg.0.log | mail (your email address)
``` on the command line.

If you send it to a gmail account, it might show up under a spam folder. The email will also have no subject.

---

### Post by lingon on 2006-03-19
Hmm....turns out I dont have a internet connection during live and the info rolled across the screen in like 100km/h so what do I do now? Anyway of printing it or so? Or get that info using other methods?

---

### Post by christhemonkey on 2006-03-19
try doing a
```
cat /var/log/Xorg.0.log | less 
```
then you can chose when to scroll down.
The lines starting with [EE] (or something like that!) are the errors, so just note them down and post them here.

---

### Post by lingon on 2006-03-19
I tried doing the | less thing and that gave me some kind of summary where info like what screen and graphics card I have and the build number of the Ubuntu in use, but thats bout it. No lines begining with (EE) although it did say that (EE) = error. I also tried configuring the Xserver using the sudo dpkg-reconfigure xserver-xorg line without succes.

---

### Post by lingon on 2006-03-19
Looks like I finally worked it out, so thanks for taking time and caring.
/lingon

---

### Post by hstokholm on 2006-03-21
How did you work it out....? I have the same problem, and I can't figure out what to do.... I only had Ubuntu for 2 days...

edit: nevermind I figured it out....

---

