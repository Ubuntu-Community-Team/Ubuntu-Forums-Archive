---
title: "no sound or wireless on amilo pro laptop"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by nalle on 2007-10-27
I've upgraded my laptop to gutsy and the sound and wireless stopped working.
Computer Fujitsu Siemens Amilo Pro v3205. I've searched the forums and although I found some information on similar problems, none gave viable solutions and since my wireless isn't working, I have very limited access to the internet so I though I'd ask for help..


sound card info:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH Conexant softmodem SmartCP
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at dc240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

The card is supposed to be using alsa driver snd-hda-intel but modprobing I can't find it or anything that sounds similar. The sound card is found, but no driver no sound.. Do I have to compile alsa from source or is there some easier solution?

The wireless seems trickier
info:
01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1001
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at da000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

it's supposed to be using restricted driver ipw3945, but even though that is enabled, it's not in use. It can't be turned on by default in the bios as this thread suggested:
[http://ubuntuforums.org/showthread.php?p=3577954#post3577954](http://ubuntuforums.org/showthread.php?p=3577954#post3577954)


So any ideas? Or solutions?

t. v

---

### Post by bordaigorl on 2007-10-27
I have the same problem (same laptop of course!) with the sound card but my wireless works just fine.
I installed Kubuntu 7.4 and then upgraded to 7.10.

In fact I downloaded the alsa drivers provided by realtek ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3)) and I tried to install it but it didn't worked.
Well, actually I fiddled with some packages (libsounda) for a while and I managed to compile and install it AND IT WORKED PERFECTLY. Then I had to reinstall the system (sorry, I'm dummy :( ) and now I'm not able to reinstall properly the drivers.

More precisely, the installer halts after a while saying that it cannot find alsaconfig,
The first time I managed to install it but I had to uninstall libasound first (wich uninstalled all the dependent -and important!- packages -> that's why I reinstalled :mad:), maybe the installer isn't able to uninstall properly the previous driver?

Any suggestions?

---

### Post by bordaigorl on 2007-10-27
Ok I fixed it. The sound, I mean.
I recompiled the alsa drivers and added to the /etc/modprobe.d/alsa-base the following line

```
options snd-hda-intel model=fujitsu
```

It works with Realtek ALC861, of course.

I found this guide very useful:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I hope it can help you.

---

### Post by nalle on 2007-10-28
Thank you :)
Consequently, I just got both sound and wireless working by booting up with the generic kernel instead of the 386 kernel in GRUB

---

