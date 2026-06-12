---
title: "help a newbie hibernate"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by wwbdd on 2005-12-29
I tried to hibernate my laptop and it didn't work.  I tried looking at other threads but they only talked about different video drivers.  I dont understand why the video drivers have anything to do with hibernating.  I am running an ati driver i believe... or at least that's what it says in /etc/X11/xorg.conf.  What do i need to do to allow my laptop to hibernate?

I have a compaq v2404us with a turion 64 1.6ghz, ati 200m express, and 512 ram.

Any help would be greatly appreciated.

---

### Post by Luzbel on 2005-12-30
First of all, I must say I've not tried it but I've read about it.

Kernel 2.6.14 has the hability to suspend to disk (which is the same as hibernate), concretely it will copy the data into the swap partition. Next boot, if compiled with this option, it will recover the data from swap partition (or you can tell it by arguments to do a clean boot without the previous dara stored).

You also have the suspend to RAM functionality, which will put your computer in a low level consumption state, fan will stop and no processes will be running, but as soon as you wake it up by an event (pressing some keys, touching your synaptics, ...) it will recover to the same state it previously was. I've tested this both in my laptop and in my PC. For my laptop I don't have to do anything special but typing:

# echo -n "ram" > /sys/power/state

In my PC, if first have to stop X (# /etc/init.d/kdm stop) - gdm, xdm... - and unload nvidia drivers (mine is legacy, I don't know if it is also neccessary for more modern drivers. Anyhow, I'd never heard of needing to unload ATI dirvers before suspend to RAM. Btw, mate, if you try this and moving the mouse, synaptics, whatever, doesn't work; try the power button to bring it but.

To sum up, you may have to stop X before trying to suspend to disk, but before you should read about it and perhaps upgrade your kernel (it was 2.6.12-something the Breezy default, wasn't it?). I guess that if you have to stop X first it will not be very useful for you. Take into account this: **EVEN if you manage to suspend to disk, I recommend saving your documents until you are _SURE_ it's working OK**.

Hope that helped!

---

### Post by galileon on 2007-04-02
i recommend saving even when you are sure it is ok! :)

---

