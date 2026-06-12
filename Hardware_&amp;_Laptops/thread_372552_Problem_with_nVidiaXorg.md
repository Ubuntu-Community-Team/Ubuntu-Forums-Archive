---
title: "Problem with nVidia/Xorg"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by open_coder on 2007-02-28
I have installed the nvidia drivers several times. After the first time, I rebooted my computer  and the xserver didnt start. I used the envy script to install the drivers and then use startx to get into gnome, but then as soon as i restarted, the same thing happened again. The error says that a problem with the xorg.conf exists. If i switch to the open source driver instead of the proprietary one it works again.

Has anybody had this problem before? Is there a way to fix it? I am running 6.10 with Nvidia Geforce FX 5200 128mb of video ram. 

Also, the error claims that there is no video display device to use. 

Thanks, 
--Alex

---

### Post by shotgunefx on 2007-02-28
I don't know what version of Nvidia you are using, but it sounds like a problem I had awhile back when I was running a debian testing (etch IIRC) distro.

There was some issue with how the drivers where installed and it kept unlinking them on restart, which of course, stopped them from being loaded.

I never did figure out where exactly the problem in the scripts where, I didn't bother, I just set the immutable flag on the drivers.

So note where it installs the driver, then see if they are still there after restart.

Hope that helps.

---

### Post by fabios on 2007-02-28
I have bought exactly the same video card this morning and I have exactly the same problem, with ubuntu 6.06.

I don't know a "clean" solution (and I would like to know it), anyway for the moment I solved this way:

- remove gdm (or kdm) from the services in the default run level
- add the following in /etc/rc.local

rmmod nvidia
modprobe nvidia
/etc/init.d/gdm start


Bye

Fabio

---

### Post by fabios on 2007-02-28
I think I solved it, more or less: just remove linux-restricted-modules*
Then, it should work. At least, my system did...  ;-)

Nevertheless, if you need some module from "restricted", my "patch" can be useful.

Bye

Fabio

---

### Post by open_coder on 2007-03-03
thank fabios. i used your "patch" it works now but the final line that starts gdm doesnt work. i think i might have missed something. but i copied it from your post directly... but its fine for right now.

---

