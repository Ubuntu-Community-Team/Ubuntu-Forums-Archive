---
title: "compaq v2311us - logon hangs"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by atrus325 on 2005-06-29
Hi all,

I adore Ubuntu, but unfortunately I'm now experiencing my very first problem.  It happens on a new Compaq 2311us laptop, with an AMD Turion processor.  Everything seems to install correctly.  I arrive at the logon screen, enter my username and password, but then logon simply hangs.  I sometimes hear that pleasant logon music (which is oddly distorted), and then nothing.  Anyone else experiened this, and if so, what did you do to fix it?

Thanks!

J.

---

### Post by atrus325 on 2005-06-29
Oh,

And Mandrake works fine.  I just don't like Mandrake much.

J.

---

### Post by atrus325 on 2005-07-01
Fixed this issue.  It was, of course, video.  I simply entered xorg.conf and changed ati to vesa.  I'll have to try and ndiswrapper the windows ati video driver later (if it works that way - still a newb here).

But now!  Ubuntu is sooo slow.  Not only that, but it doesn't seem to know what to do with my processor.  I have the cpu monitor enabled, but I get no results.

I'm going to try a different kernel and see if this fixes this.  Good idea?  Has anyone else had similar problems with Turion chips?

J.

---

### Post by arohl74 on 2005-07-06
How did you changed the driver from ati to vesa?  I'm a newbie too and I am trying to figure this out.

---

### Post by varunus on 2005-07-06
atrus:

ndiswrapper only works for network card windows drivers.  However, there is a proprietary ATI driver for linux which I highly recommend you install.  There's a howto on it in the "Hoary Tips and Tricks" section of the forums.

I have never heard of a Turion (is it a new AMD mobile chip?).  However, Ubuntu can seem slow with the vesa driver, as it is very very bad.  The ATI driver will improve speed.  Also, I would recommend installing cpufreqd from synaptic.  Ubuntu includes a CPU scaler called powernowd that drops your CPU's speed based only on CPU load; however, it doesn't always speed up when it needs to.  cpufreqd will let you control it better, and will keep the speed at max when you're plugged in, which I prefer.

arohl:
To change the driver to vesa, open up the file /etc/X11/xorg.conf while in recovery mode:
```
nano /etc/X11/xorg.conf
``` 
Under the device section, change the driver to "vesa" from whatever it is (probably radeon or nv or something like that).

Once you do change the driver to vesa, follow the howto on how to install the ATI driver in "Hoary Tips and Tricks."

Good luck.

---

### Post by Zanidor on 2005-07-11
I'm running into the exact same problems with a Compaq Presario V2000. Using vesa allowed me to sucessfully boot, but the ATI webpage does not have drivers available for notebook video devices...

I looked around on the tips and tricks forum for anything useful, but couldn't find anything. Any more ideas on how to get around the issue, or should I try my luck with a different distro?

---

### Post by Zanidor on 2005-07-11
[QUOTE=varunus]I have never heard of a Turion (is it a new AMD mobile chip?)[/QUOTE]

Yes, it's AMD's new 64 bit mobile processor. From what I understand, it's essentially an Athlon 64 modified for lower power consumption, etc.

---

### Post by atrus325 on 2005-07-11
So far, I'm really enjoying my Turion processor.  The previous poster is correct.  It's basically just AMD's 64 bit answer to Centrino, and since it's both 64 bit and AMD, I'm immediately a fan.  


I'll take a look at those above posted suggestions and give Ubuntu another go :-)

J.

---

### Post by maxdubin on 2005-07-21
I too use this laptop....gentoo not ubuntu...it seems to work great, need to set flages  for the 64 bit. The only thing left to do is the WiFi if anyone has a solution send me a email at   max[dot]dubin[at]gmail[dot]com

Thanks
Max

---

### Post by s_p_a_r_k_y on 2005-07-22
[QUOTE=Zanidor]I'm running into the exact same problems with a Compaq Presario V2000. Using vesa allowed me to sucessfully boot, but the ATI webpage does not have drivers available for notebook video devices...

I looked around on the tips and tricks forum for anything useful, but couldn't find anything. Any more ideas on how to get around the issue, or should I try my luck with a different distro?[/QUOTE]
One thing that one should learn quickly with a debian based distro is not to resort to downloading files from websites unless its not in apt. Ati drivers are in apt, you can use synaptic or apt-cache search packagename to look for a package. Always do that before looking at the website, its a common rookie windows/mac/redhat/suse mistake. The wonderful world of debian is never having to download and install things manually, but things in apt just work (98% of the time)! If you cant find it in hoary, you might be able to get it from backports search google for ubuntu backports....i recommend getting beagle...mmm desktop search (and no one tell me I should store my files better! I do, but its for e-mails and IMs I forget where I told someone something)

---

### Post by Dr_Willis on 2005-07-23
Also got one of these nice laptops the other day, and my research of the net from this and other sites imply that the following are curently true.

Note that these problems may go away with new releases of kernel/drivers and other things.

The x200 is not curently supported by the ATI's official flgrx drivers. So one must use vesa.   (ive been having problems even with vesa, no screens found problem)

The wireless card needs to use the ndiswrappers (I hear, not tried it yet)

My Personal experience, if i do not use noapci (or apci=off) as a kernel boot option the machine is very very slow. ie: 30 min to just boot.

I have not had any problems with the default X.org config ubuntu made and the widescreen. Many other disrtos and sites mention needingto tweak their config files.  

Perhaps we need to make an new thread for more detailed support information on this laptop.  Or a Wiki page. The forums  always seem to get very cluttered at times with the history of new hardware.  

Good luck - off to test it some more.

---

### Post by lcharly on 2005-07-28
i have a compaq presario v2312us with amd turion and works soo fast in ubuntu amd 64 how i fix it?

just change the repositors to breezy and update the kernel to 2.6.12-5 for amd generic and its works very fine good luck

---

