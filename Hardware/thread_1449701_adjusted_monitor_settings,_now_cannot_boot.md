---
title: "adjusted monitor settings, now cannot boot"
date: 2010-04-08
forum: Hardware
---

### Post by gas.man on 2010-04-08
Help!

I'm running 9.10 on a vaio laptop, all working well for some time.

I am giving a presentation tomorrow and plugged in a second monitor to check settings. As part of this I adjusted the resolution of the laptop screen to 1280xsomething, and was asked to logout/login. The computer froze after logging out, with an "updating cups.." or similar message on the screen.

Powered down, and now unable to boot properly.

On power-up I get grub loading message, then the splash screen/logo. Then screen goes black apart from an underscore in the top left corner. I get a very quick flash of:

Ubuntu ****_laptop tty1

Login:

This happens about 5 times, then it's a black screen with the non-blinking underscore. Machine appears dead to all keypresses.

I am giving this presentation tomorrow and didn't back up to a memory stick yet - that was the next task :-(

HELP!!!!

---

### Post by gas.man on 2010-04-08
Update: not much help, but if I hit any F.. key during the boot, I get a flashed message of /dev/sda1 clean ...... then the tty1/login message. Then......nothing.

---

### Post by gas.man on 2010-04-08
[FONT=Arial]Managed to get to rescue mode by a miracle.

Errors running **xinit**, so decided this was problem. Solution if others have same problem:

Ran **X -configure** as root to create the configuration file **xorg.conf**.**new**, and copied to the default location /**etc**/**X11**/**xorg.conf**.

Re-boot. Hold breath. Everything fine :-)

[/FONT]

---

