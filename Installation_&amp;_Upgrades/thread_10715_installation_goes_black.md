---
title: "installation goes black"
date: 2005-01-10
forum: Installation &amp; Upgrades
---

### Post by waz on 2005-01-10
Tryed to install the warty here, but right after the "boot ubuntu" a few lines show before the screen goes black. Have tryed with both the 64 and 32 bit versions, but same thing happens, is there some kind of hardware incompatibility?

Seems strange because the live-cd loads just fine, what can be the problem?

my system is an acer ferrari 3200 notebook with ati 9700 video card

thanks

---

### Post by Kareema on 2005-01-11
I bet when the screen goes black you can see the text shimmering through if you turn the brightness fully on (sorry I don't know how to express myself here; lacking the right English words). I had the same problems with my Acer Ferrari 3400 during install. I could complete the setup looking hard enough at my screen ;-) 

After updating all available packages everything was OK (Warty AMD64).

Some days ago, this bug was reitroduced in Hoary in another fashion: The system is running perfectly until I log out of Gnome and go into console mode/reboot/shutdown. Then the screen turns black with the above mentioned symptoms.

Didn't have the time to report the bug in bugzilla ([https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)). Perhaps you or somebody else could do it?

---

### Post by waz on 2005-01-12
Can't manage to see nothing no matter how much i try to change the settings of the screen.. :(

You had the same problem during install of hoary?
Maybe I could try hoary instead, but where can I download, could not find it on the site..

---

### Post by Kareema on 2005-01-13
I never installed Hoary from CD, but there are several versions available for installation: The more stable array release [http://cdimage.ubuntu.com/releases/hoary/array-2/](http://cdimage.ubuntu.com/releases/hoary/array-2/) or the daily snaptshot [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/). A live CD is available at
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/).

I found another thread about this (or a similar) problem: Look at [http://www.ubuntuforums.org/showthread.php?t=5711](http://www.ubuntuforums.org/showthread.php?t=5711), perhaps that works for you when testing the live CD.

Please report it here if you find a solution to the problem.

---

### Post by brockmasterflex on 2005-01-13
I just started the same thread about this..... any one find a solution to this problem, its quite vexing!

---

### Post by waz on 2005-01-14
[QUOTE=brockmasterflex]I just started the same thread about this..... any one find a solution to this problem, its quite vexing![/QUOTE]
 Unfortunately the  command     linux noapic nolapic doesn't work either

---

### Post by callahan on 2005-01-18
I have the same machine, acer ferrari.  I get the same blackscreen with both the warty 32 and 64 bit builds.  The live CD works fine for me and it would have been great if it supported a network install as then I could get somewhere.  Incidentally I get the exact same thing with the 32 bit Fedora Core 3 install cd and have to use the "nofb" option there to make it work.  The fix is to boot with the vga=771 option, ie "linux vga=771".

  Michael

---

### Post by waz on 2005-01-19
[QUOTE=callahan]I have the same machine, acer ferrari.  I get the same blackscreen with both the warty 32 and 64 bit builds.  The live CD works fine for me and it would have been great if it supported a network install as then I could get somewhere.  Incidentally I get the exact same thing with the 32 bit Fedora Core 3 install cd and have to use the "nofb" option there to make it work.  The fix is to boot with the vga=771 option, ie "linux vga=771".

  Michael[/QUOTE]
 yea, the "linux vga=771" worked smoothly, installation seemed to go without problems.

Unfortunately there was another problem just waiting to show up, first the x-server did not want to start, so I was left with the command line, which was bad enough for a noob like me. In addition the GRUB forgot to leave windows as an option to start up.
With some help I managed to fix the grub so I can start windows, but still I have no clue what is wrong with the x-server.

---

