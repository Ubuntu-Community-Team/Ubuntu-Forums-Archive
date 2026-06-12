---
title: "Ati radeon hd 4850 compatibility"
date: 2008-07-04
forum: Hardware
---

### Post by mossman44 on 2008-07-04
I am interesting in purchasing the new radeon hd4850 graphics card and I was wondering if the fglrx drivers provided by the ubuntu restricted drivers manager are compatible with this card. If not, do the restricted drivers work with the hd3870?  I am currently using ubuntu 8.04.

---

### Post by Giannis_ on 2008-07-10
> **mossman44 said:**
> I am interesting in purchasing the new radeon hd4850 graphics card and I was wondering if the fglrx drivers provided by the ubuntu restricted drivers manager are compatible with this card.

+1

Me too.

---

### Post by cristo-father on 2008-07-11
> **mossman44 said:**
> I am interesting in purchasing the new radeon hd4850 graphics card and I was wondering if the fglrx drivers provided by the ubuntu restricted drivers manager are compatible with this card. If not, do the restricted drivers work with the hd3870?  I am currently using ubuntu 8.04.

You can always do it manually...go to method number 2.
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by leo11877 on 2008-07-12
I tried the above directions and it does work indeed !!! Thank You, I can now run Compiz effects :)

---

### Post by markbuntu on 2008-07-13
Please mark this thread as solved using the thread tools.

---

### Post by mossman44 on 2008-07-16
yes the manual method of installation worked. Now only if I could use the fan fix like I did in windows...

---

### Post by pedrogent on 2008-09-06
Thanks very much!

---

### Post by xpasi on 2008-09-06
Having some issues here with my ASUS EAH4850 (radeon HD4850) card.


I installed Hardy first with a Acer 19" widescreen monitor, where everything worked fine.

Then I removed the 19" monitor and plugged in a Benq 22" widescreen monitor (T221W)

in the 22" monitor the default settings make the image square, eg. not widescreen. There are about 6cm wide black bars on both edges of the screen.

I've tried to set the resolutions in xorg.conf which always results in the resolutions being ignored or with the display going black and reading "out of range".

Then I did a fresh install of Hardy with the 22" monitor attached from the beggining, but the problem persists.

Then I've tried all sorts of hints from the net (different ATI drivers etc.) but none of them work.

I have tried the instructions got from the link posted above... both manual and "the ubuntu way"... the ubuntu way end up with error stating that the card is not supported.

the manual way installed driver doesn't work either... I just get thrown into the low-resolution mode.

Now the point is, I don't need 3D, I don't need any fancy features. all I want is a full widescreen image on my screen, but so far this seems to be impossible to achieve!

The current black-bars non-widescreen mode is powered by Vesa drivers (resolutions detected automatically)

And remember.... it works in the 19" ACER widescreen PERFECTLY!

---

### Post by xpasi on 2008-09-06
Problem gone...

Manualy installed from source the "in developement" radeonhd driver and everything works like charmed :)

---

### Post by keypox on 2008-11-19
> **cristo-father said:**
> You can always do it manually...go to method number 2.
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

didnt work for me and i am now in 800 x 600 on a 24inch :(  Running mesa drivers.  How do i fix this im a noob

method 1 worked but had flickering video, method two gave me mesa drivers.  I tried some stuff on my own at this ponit and now ubuntu wont boot.

---

### Post by keypox on 2008-11-19
> **xpasi said:**
> Problem gone...

Manualy installed from source the "in developement" radeonhd driver and everything works like charmed :)

what does this mean? ^^^^

---

### Post by computerjunkie on 2009-01-26
I am having issues as well. I used the manual instructions and then rebooted. When ubuntu tried to start up it said "running local scripts" and then there was a black screen. nothing more, ever. The automatic instructions didn't work either. Nor did the instructions on the ati website. How did anyone get this to work? I followed the instructions to the "t". copy and pasted all of the commands. double checked everything, and it failed; epicly, I might add.

---

### Post by Yashiro on 2009-01-27
> **mossman44 said:**
> yes the manual method of installation worked. Now only if I could use the fan fix like I did in windows...
in a terminal:

aticonfig --pplib-cmd "set fanspeed 0 **60**"

---

### Post by mossman44 on 2009-01-30
First, the link to the manual instructions were for hardy. If you are using Intrepid use this link [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide). After you install the deb packages it is crucial that you open a terminal and type:
sudo /usr/bin/aticonfig --initial 
This will setup xorg.conf automatically for you and you must restart after that.  If you forget to use this command before restarting (like I did the first time) you will have issues.

---

