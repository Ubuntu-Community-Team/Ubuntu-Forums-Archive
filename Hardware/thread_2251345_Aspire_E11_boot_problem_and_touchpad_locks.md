---
title: "Aspire E11 boot problem and touchpad locks"
date: 2014-11-03
forum: Hardware
---

### Post by bomtempo2 on 2014-11-03
Hey my Aspire E11 has had a rough ride with Ubuntu so far. I bought it a month ago and have had problems both with 14.04 and 14.10.

The biggest problems so far is the computer freeze on reboot.
 
The mouse often gets locked after suspend. The problem with touchpad locking it self even happend running a live Ubuntu 14.10 from USB.

A problem that seems connected is that sometimes the mouse / pointer goes wild and all over the place. Locking it manually with keyboard shortcut and then unlocking makes it normal.

I have tried editing in grub. But it seems to no success. Trying things like quiet splash and acpi=off has not given effect or given unwanted effects. 
I even tried some blacklisting of blacklist i2c_hid but then my touchpad didn't work at all.

Anyone else having experiences with the Acer Aspire E11?

---

### Post by noob2014 on 2014-12-16
Hey there! Similar issues for me, 14.04 was horrid mission during the boot. So far 14.10 has been good to me wihich is nice. However, similar to you, when I switch up computer on after a 'suspend' nothing works. Can't move my mouse and the icons in the top right are going nuts. Thankfully though, shutdowns and restarts are working fine so I at least have a usable machine. But it is quite frustrating that I can't just 'suspend' my notebook and quick start it.

---

### Post by bomtempo2 on 2015-01-08
Maybe you can try to do an Fn+F7 combination to get the mouse moving after suspend. Often it works for me after the mouse have gone crazy. I block it and deblock the mouse and it gets fine again. But it doesn't work after suspend on my computer.

I realised my reboots always get stuck, so i can never do a restart. Did you do anything to get it working?

I now got a problem with the function key to get brightness go up. It kind of got stuck and blocked the system. It contunied after closing down the computer and starting again. And it even continued when i i started from a live-USB. One time i think it stopped out of it self. And second time I got it to stop through doing a restart of gdm in the terminal. The third time it seems it stoped when i tried to login to a recovery session. I don't realy get why it stops.

---

### Post by Thomas_S. on 2015-11-04
Just found the solution for my aspire E11 ES1 mouse touchpad goes wild goes crazy jumps around under linux: 
It is a synaptics touchpad. To verify, look into /var/log/Xorg.0.log

So you will have a program "synclient".
With "synclient -l" you can see many settings, and the solution is to reduce sensivity of the touchpad:

      synclient PressureMotionMinZ=90

So now have a nice time with your fanless :) acer notebook!!!

PS: The other anoying problem for me is that it freezes during power off. 
If you have a solution for that, please share.

---

### Post by bomtempo2 on 2015-11-10
Ohh i was really happy to see your advice, but I changed the value to 90 even 110, and stil my mouse go loco. I now i saw recomendations for changing some other touch pad setting sometime and i tried that once it didnt work either... :( 
But I am happy for you that it works on your computer...

About the other problem I don't really now I haven't experienced that.... It do freeze under reboot though, so I can only power off and then start it... :(

---

### Post by Thomas_S. on 2016-03-13
Sorry for follow up so late. The SW trick did not work out for me too. It was only a temprary improvement, probably by chance.

What really works is to make a better ground connection to the touchpad, as suggested at various places. However, I did not solder it, as the heat damages the touch pad. Instead, I attached a wire to the touchpad by adding a flexible layer between that and the battery, so the wire is pressed against the touchpad. Since then it really works perfect!

---

