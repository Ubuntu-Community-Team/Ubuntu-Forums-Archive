---
title: "How can I speed up Ubuntu boot up"
date: 2008-10-14
forum: General Help
---

### Post by yinglcs2 on 2008-10-14
Hi,

I am using ubuntu 8.0.4. I have enable auto login and I have enabled the 'extra visual effects'.

But after ubuntu boots to a point where it shows a solid wheat background with a white cursor, it takes ~ 15 seconds before it shows my wallpaper, and then another 5 seconds before the whole desktop is finished boot up.

Can you please tell me what can I do to speed up ubuntu boot up?
Yes,I have google related article, but I am lookineg for ways to boot up after ubuntu shows a solid wheat background with a white cursor to the point of full completion.

Thank you.

---

### Post by phidia on 2008-10-14
You may need to disable unnecessary services. Open System > Admin > Services and uncheck anything there you aren't using.

---

### Post by OutOfReach on 2008-10-14
Get rid of unnecessary services, as phidia stated. You can also try out a lighter window manager (Openbox, Xfce, etc...).

---

### Post by stormtrooprdave on 2008-10-14
Which services are safe to disable?  If I am on a desktop and not a laptop do I need to be running CPU Frequency Manager (powernowd) and Power Management (acpid)?

---

### Post by kokkus on 2008-10-14
If you disable any unsafe services you can always use the 2nd kernel and enable the services again.

---

### Post by Vert on 2008-10-14
Generally on a desktop you do not need the power daemon (unless you have special needs, i.e. my family would never remember to turn off the monitor at night). Just get into good habits of doing things like turning off your monitor at night. Unplugging USB devices which you don't use often or just plug in USB devices only when you need them (USB devices such as mice and anything that charges via USB use power). Also, the lighter Window Manager will make a big difference if you don't dropping just a little eye candy (obviously that's subjective upon you). Also, depending on the video card keep your desktop on 2D and forget about all the 3D stuff. Or just keep it on 2D and turn on 3D only when you need it and it won't take so long to initialize. Go under Sessions in your preference tab and turn off any programs you don't use. For example, if your desktop doesn't use bluetooth, why would the bluetooth daemon/applet start? Don't print? Why use CUPS? Just try turning off simple things you know aren't "needed" to boot. Sometimes it helps a lot than you might think. Hope this helps ^^

---

### Post by oldos2er on 2008-10-14
Look into "CONCURRENCY=SHELL" if you have dual or Core2Duo processors (or greater).

---

