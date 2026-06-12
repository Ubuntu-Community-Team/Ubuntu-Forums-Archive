---
title: "hibernation on hp nc4200 = no LCD ?"
date: 2009-12-16
forum: Hardware
---

### Post by gabona on 2009-12-16
Hi all,

At last week I tried the ubuntu 9.10 on my hp nc4200 notebook. I'm using 9.04, so I not upgraded to 9.10. Fresh, virgine HDD, install from original CD, update from net, and the 9.10 ready to start... but...
It seems like to work correctly, network, audio, and everything, but the first different between 9.04 and 9.10, when I close the notebook, the 9.10 will be hibernate my pc...
When I try to wake up from hibernation, the lcd didn't wake up. Power off... power on... no lcd backlight...
I try the followings:
- boot from 9.04 live cd
- boot from the old 9.04 hdd
- boot from 9.10 live cd
- boot from the installed 9.10 hdd
after lots of boots and restarts, the lcd didn't wake up...

What can I do to solve this problem? At this moment my notebook is unuseable. :(

I've meet the similar problem on my girfriend's hp nc6220 with 9.10, but that's machine can wake up after power off-on.
If I try to hibernate my old notebook (hp nc6120) with 9.10, I can wake up it without any problem.

---

### Post by gabona on 2009-12-19
No any idea from anybody? :confused:

---

### Post by gabona on 2009-12-19
I can solve my problem... Thanx for my friend at HP :)

I can't beleive it... Nobody have any idea or suggession about it from ubuntu community during 2 days in more than 3 forums...

Goodbye Ubuntu...

---

### Post by kruemel_simi on 2009-12-25
Hello,

my nc4200 has nearly the same problem. Since Karmic it stops responding when I open the lid. I have disabled the standby on lid closed -> just switching LCD off.
Often it doesn't start up after power on when running from battery. I just have to wait or reinsert the battery.



Sorry for my bad english.


Greets Simon and merry X-mas

---

### Post by segabor on 2011-01-05
Hi,

I have a HP nc6120 having Ubuntu Maverick on it and it's suffering from no LCD after suspended / hibernated state. The only workaround is to move the laptop to an external display and connect. Then Ubuntu will make it visible on that screen leaving the primary LCD totally dark (unlit? I can see something on it but it seems to me the backlight is off).

I suppose Intel graphics driver is buggy. It sometimes can't restore GPU state after waking up or it corrupts settings.

So after some reboots Ubuntu switches back to primary screen.

Anyone with a good explanation / better workaround?

---

