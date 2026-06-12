---
title: "AMD FGLRX driver crashes window manager"
date: 2013-10-01
forum: Hardware
---

### Post by eric_r2 on 2013-10-01
I have a Lenovo Ideapad Y470 with a . Every time that I  install the  FGLRX driver through System Settings -> software Sources  ->  Additional Drivers, my window manager completely crashes after   rebooting, and I receive a blank desktop. I can open a terminal window   and load up applications if I want to, but no window manager. If I   switch to Gnome, I can also get around.

  I have also found that I have the exact same problem if I switch to   Linux Mint and try to use Cinnamon, so I know that the problem is not   Unity.

I've tried enable the nomodeset option in GRUB, but that does not seem to have an effect.

I tried a fresh install, first ran updates and installed  linux-headers-generic, and then attempted to install the beta driver  from AMD's website.

  After rebooting, I received an error about xorg not being configured,   and it asked me if I wanted to restore the default configuration, which   I did.

  Now, after reboot I just boot to the Ubuntu graphical login prompt followed by **black screen**. Not sure what to do...

Could this possibly have something to do with the hybrid Intel/AMD graphics that come with this laptop?

---

### Post by Yellow Pasque on 2013-10-01
> Could this possibly have something to do with the hybrid Intel/AMD graphics that come with this laptop? 
Yes. You need to get to a terminal and completely remove the AMD driver: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Removing_Catalyst.2Ffglrx)

Installing the AMD driver borks open-source drivers (like intel), hence no desktop when you install it. I don't know what the best solution for this hybrid nonsense is nowadays, but check: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by eric_r2 on 2013-10-01
I think I've made a little bit of progress using that guide.. After completing it, when I reboot, I come to a black screen that seems to last about 15 seconds, followed by a desktop where Unity is invisible. If I click in the locations where icons would be, the applictions open successfully, but the whole thing is invisible.

Additionally, if I run fglrxinfo, I get this series of errors:

Setting of real/effective user Id to 0/0 failed
libGL error: open uki failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: AMD Radeon HD 7670M

If I try running glxgears, I get extreme lag..

EDIT: New problem.. I was able to get glxgears running at normal speed and resolve the "Setting of real/effective user Id to 0/0 failed" by using this command:

sudo chmod -R 777 /proc/ati/

[B]However, this solution only works until I reboot (and doesn't make Unity visible). After reboot the problem is back, and Unity is still invisible.
[/B]

---

### Post by eric_r2 on 2013-10-03
I have now resolved this by adding:

chmod -R 777 /proc/ati/

to the /etc/rc.local file. Thanks to everyone that helped! The laptop still freezes to a black screen after suspend though...

---

### Post by Feby_Philip_Abraham on 2013-10-03
You could try this guide posted by Niccola ... [http://ubuntuforums.org/showthread.php?t=1930450&page=82&p=12755069#post12755069](http://ubuntuforums.org/showthread.php?t=1930450&page=82&p=12755069#post12755069)

It worked perfectly on my AMD/Intel hybrid GPU based HP notebook!

Mods: Could you please delete this post as it got repeated. Sorry for the inconvenience!

---

### Post by Feby_Philip_Abraham on 2013-10-03
You could try this guide posted by Niccola ... [http://ubuntuforums.org/showthread.php?t=1930450&page=82&p=12755069#post12755069](http://ubuntuforums.org/showthread.php?t=1930450&page=82&p=12755069#post12755069)

It worked perfectly on my AMD/Intel hybrid GPU based HP notebook running Quantal!

---

