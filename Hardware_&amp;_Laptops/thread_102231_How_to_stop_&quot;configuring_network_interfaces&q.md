---
title: "How to stop &quot;configuring network interfaces&quot; at boot?"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by Zyzzyva100 on 2005-12-11
I have tried a number of things, including trying to remove this directly from the terminal, using boot up manager, and using the perl gui rc-configuration editor.  Nothing seems to work.  If I disable hotplug it goes through this without waiting for a minute, but then my sound and network cards don't work.

If I control-c as soon as this comes up it obviously skips it, and networking works just fine.  So is there anyway to make it so that this doesn't happen?  I have boot time down to about a minute (from power on to using programs), which I consider pretty good on an ultra portable laptop.  I would like it to be able to do this without my intervention though.

So, how can I fix this?  I use network manager to control my wifi/wired ethernet, and it works beautifully.  I just wish that the configuring network interfaces didn't hang up the boot process, especially since it doesn't actually seem to do anything.

---

### Post by Corvillus on 2005-12-11
What I did to get around that problem was disable all the network interfaces in System - Administration - Networking. This didn't affect network-manager or wifi-radar at all for me, but it did greatly speed up my boot time.

---

### Post by Zyzzyva100 on 2005-12-11
Nope, that didn't do it for me.  It still hangs on configuring network interfaces for me.  I have it 20 seconds or so to see what was going on, but it didn't seem to make a difference.

I just wish I could make it automatically stop doing this.  If I control-c immeadiately when it comes up, everything still works fine.  Thats what is so annoying, its not needed, and it doubles my boot time, literally, from 1 minute to 2 minutes.

---

### Post by anil_robo on 2005-12-11
install Boot-up Manager (bum) and see if you can disable networking at startup from the third tab. Alternatively, you can see the startup scripts in /etc/init.d folder. I haven't played around with those scripts, so can't tell you what the output may be, but be prepared for a disaster (with live cd in one hand and a screwdriver in the other) if you plan to edit those.

---

### Post by NMUrugbysteve on 2005-12-11
what you need to disable is hotplug-net, not regular hotplug. Have you tried the howto on editing the speed of booting ubuntu? If not I'd highly recommend it.

---

### Post by Zyzzyva100 on 2005-12-11
Hotplug-net is indeed disabled.  I read the howto and installed sysv-rc-conf, and the only thing that is still enabled is hotplug (regular) as S runlevel.  

Hotplug-net is also disabled in boot up manager, which is why I can't figure out why it still tries to run at boot.  Another option someone listed above was disabling networking in the 3rd tab in boot up manager, but it won't let me.  It says that editing in run level S is not allowed.  Anyway to get around this?

---

### Post by Zyzzyva100 on 2005-12-11
Ok, I figured it out.  Using sysv-rc-conf I disabled networking.  That did it, since network manager brings up wireless and ethernet interfaces itself.  Granted it takes maybe an extra second or two compared with if the devices are already starting when it starts to run, but i would rather deal with that little delay than wait it on boot up.

---

### Post by Sammi on 2006-03-23
Jup that solved it for me to.

First you have to disable all the network interfaces in applications->systen->netwoking. This stops the "configuring network interfaces" hang in boot. Then you need to install Network Manager and put nm-applet in the autorun folder, because it will take over network management and make everything work without any work and hazzle :D

---

