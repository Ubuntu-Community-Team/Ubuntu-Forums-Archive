---
title: "ESS Allegro not found with base ubuntu install"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by jamisnemo on 2007-04-24
I have a Gateway Solo 3350 that worked just fine under Gentoo linux. Last night I got sick of dealing with xorg's new issues under gentoo and decided to upgrade to ubuntu.

After changing the default windows manager from Gnome to Xfce, The laptop runs reasonably well.

The built in audio card isn't detected though. From my gentoo install I know that the module the card needs is snd-maestro3 which I added to /etc/modules and was also able to modprobe without any problems.

lspci shows the card, the module is loaded ok but alsamixer doesn't find it and aplay -l doesn't list the internal card (it does however see my usb device)

So what do I have to do to get my sound working? Where are alsa devices configured? Why isn't ubuntu picking up on this?

Any help would be really great! I can't wait to actually use the computer again.


EDIT: Here's some more information:
> 
$ aplay -l

aplay: device_list:222: no soundcards found...

$ more ~/.asoundrc
pcm.maestro3 {
        type hw
        card 0
}

ctl.maestro3 {
        type hw
        card 0
}

$ sudo lspci -v
00:09.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
        Subsystem: Gateway 2000 Unknown device 3350
        Flags: medium devsel, IRQ 3
        I/O ports at 1000 [size=256]
        Capabilities: [c0] Power Management version 2

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

$ tail /etc/modules 
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
snd-maestro3


Any help?

---

