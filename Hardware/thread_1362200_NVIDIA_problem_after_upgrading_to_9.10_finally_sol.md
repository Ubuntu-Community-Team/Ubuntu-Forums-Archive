---
title: "NVIDIA problem after upgrading to 9.10 finally solved."
date: 2009-12-22
forum: Hardware
---

### Post by oliverthered on 2009-12-22
Hi,

I've been having random problems with the nvidia.ko driver under X since upgrading to 9.10.

after a bit of investigation I worked out that it was due to the console being in framebuffer mode.

The GUI splash screen that displays the boot progress kicks of framebuffer mode so I expected that was the culpret.

I could fine the init script in init.d but couldn't see where it was being started, but if I hit escape it seemed to be the thing before samba.

in the init.d directories dbus gets started just before samba.

then after pressing escape and ctrl+c loads of times during load of boots to try to find out exactly what dbus was doing upstart exected with an error code, the console didn't switch into framebuffer mode and X started beautyfully.

so a bit of googling for upstart and the 'init' scripts for it are in /etc/init

so I looked at the usplash.conf in there and it says it should stop on starting-dm

the kdm and gdm .conf files should be emiting starting-dm but they weren't, so I figured that kdm in my case must still be being started by init instead of upstart thus preventing kdm from starting via upstart inturn triggering the starting-dm even.

find /etc/rc* -iname '*kdm*'

yep there it was.

so to fix it I just did a :

sudo rm $(find /etc/rc* -iname '*kdm*' | grep -v '.svn')

and now my graphics drivers are working perfectly fine.

may also be an issue with people running gdm

Now all I have to do is find out why my soundcard is playing up, there are comments about pulseaudio, but I'm sure I killed it off and it didn't fix things. may well be another bad upgrade script from the ubuntu guys who appear to have forgotten to remove at least some of the old rc*.d scripts or disable the init.d scripts when the migrated things to upstart.

---

### Post by oliverthered on 2009-12-22
I was a little premature, the first reboot worked ok, the second not.

anyhow, usplash is definatly the problem as I removed splash from the kernel options before booting and everything worked ok.

putting nosplash in there didn't stop the splash screen like it should though.

currently modified /etc/init/usplash.conf so that the splash screen is only shown on shutdown, I believe that this means it should still be shown during the inital boot process though because I think there's a uspash in the init image.

put an echo in kdm.conf just after it emits starting-dm to see if it's running via upstart or not.

---

