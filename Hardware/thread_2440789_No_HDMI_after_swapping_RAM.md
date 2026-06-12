---
title: "No HDMI after swapping RAM"
date: 2020-04-15
forum: Hardware
---

### Post by Feasoron on 2020-04-15
I replaced my RAM because the sticks went bad. For now I put back in the 16gb sticks that came with my desktop, but I plan on going back to 32 once I can get the sticks in. The machine is a Dell Inspiron 5676 that I have been happily dual booting for over a year ( with Ubuntu as my primary OS for development, but using Windows for some gaming and software for the kids' toys) Once I got the new sticks in, Windows works perfectly. Ubuntu gets partway through the boot and then the monitor off HDMI, which is my primary display and sound, says "no input." Both monitors are plugged into the same Radeon card, and there is no on-board video. The card must work, since it works fro GRUB and Windows 10. If I try to add `nomodeset`, it won't even boot.

[https://paste.ubuntu.com/p/zjHvq9ZHqj/](https://paste.ubuntu.com/p/zjHvq9ZHqj/)

---

### Post by CelticWarrior on 2020-04-15
Congrats (not...), you just made a *post hoc ergo propter hoc* rationalization. This is a fallacy.
The RAM replacement is unrelated to Ubuntu not booting, it just happened after.

This seems to be the problem:
```
sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    **Mounting failed:   mount: /mnt/BootInfo/sdb1: unknown filesystem type ''.**

```

---

### Post by Feasoron on 2020-04-15
To be a little more precise - Ubuntu is booting and running perfectly smoothly. It's just not detecting anything on my HDMI port.

---

### Post by CelticWarrior on 2020-04-15
How do you know it's running?

---

### Post by Feasoron on 2020-04-15
Because it displays on the other monitor which is plugged into the same card. I can then log in and run everything as a normal system, I just only have the monitor plugged into the displayport out, the monitor/audio on HDMI out is not detected.

---

### Post by crip720 on 2020-04-15
Would check simple things first, some cables can look plugged in but a tiny touch can lead to bad/no connection.  Can also try unplugging cable when shutdown and then plugging cable back in after start up and see if ubuntu connects with HDMI.

---

### Post by Feasoron on 2020-04-15
I've checked that. The monitor actually works in grup and through the initial booting (I have quiet and splash off) but when it reaches a certain point the monitor drops off. If I boot it into Windows, the monitor works smoothly. This makes me fairly confident that it is an Ubuntu/configuration issue. If the hardware were bad it wouldn't work in POST or under a different OS.

---

### Post by CelticWarrior on 2020-04-15
Please check your screens settings. You may have either that one disabled or mirrored using an unsupported resolution or a few other details. Hard to believe you haven't checked that already. If you did you didn't mention it like you didn't mention the second monitor. Please ALWAYS post all the relevant information and avoid the fallacies that only mislead people trying to help.

---

### Post by Feasoron on 2020-04-15
I did mention both monitors with calling it the "primary display" and [COLOR=#000000] Both monitors are plugged into the same Radeon card[/COLOR] , but yes, I checked and screen settings doesn't even show the second monitor. (It should actually be the primary, but I don't think that matters since it's not detected)

---

### Post by crip720 on 2020-04-15
Are you able to switch cables on your monitors(can displayport monitor use HDMI and vice=versa).  Should tell if GPU ubuntu settings or something else.

---

### Post by Feasoron on 2020-04-15
Unfortunately the monitor that is working under Ubuntu has DVI in and is running with a Displayport to DVI cable and the other monitor only has HDMI and is running with an HDMI cable. I have ordered some new cables that would allow me to connect them in a different fashion, but with everything going on right now that is not going to get here quickly.

---

### Post by Feasoron on 2020-04-15
<double post>

---

### Post by Feasoron on 2020-04-16
I found an old adapter and ran displayport -> dvi -> hdmi (far from ideal) and Ubuntu sees the monitor properly though it doesn't give me the full range of resolutions, and caps out far below the 4k the panel supports.

---

### Post by Feasoron on 2020-04-17
When I swapped the RAM it changed some of the BIOS options (legacy boot, tpm etc) which disabled the HDMI drivers. Video is working fine now. The audio isn't working now, but it's not the normal HDMI Ubuntu issue where the device doesn't show up. The device shows, is configurable, but doesn't actually push sound over the cable.

---

