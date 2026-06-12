---
title: "Touchpad inactive"
date: 2019-03-09
forum: Hardware
---

### Post by asearle on 2019-03-09
Hallo Everyone,

I have just bought a new laptop (Wortmann Terra 1460p) and am having trouble with the touchpad ...

Directly after install (Lubuntu 18.04), I was extremely pleased because absolutely everything worked. Including the touchpad.

But when I installed all current updates and rebooted I found that the touchpad was out: I could only get the cursor to move by attaching an external mouse.

I had had this problem once before in the past and had fixed it by adjusting the settings in BIOS (I think UEFI/secure boot but am not absolutely sure). So I tried all kinds of permutations (also re-setting to factory settings) but nothing seems to work. I also tried booting from my original install media but, even under live-boot, the touchpad was not available.

All I can think is that the updates have made some kind of firmware update which has compromised the touchpad.

This is really irritating so I do hope that someone out there can help me and maybe point me towards a solution?

Many thanks,
Alan

---

### Post by asearle on 2019-03-10
Has no one got a tip for me on this point?

I am very bemused: The dealer was kind enough to let me try a live-boot on the laptop: Everything worked. And then directly after install everything worked (including the touchpad). But then, after updating (lubuntu 18.04) the touchpad stopped working and I haven't been able to get it back. Indeed, the touchpad doesn't even work on live-boot now.

Here, I think, the bigger issue is not so much that the touchpad is not working, but the fact that it worked under live-boot and it worked after installation but stopped after installing a first update. This has shaken my confidence as I believed that, whatever works on live-boot will work after install. But somehow this is not the case.

Any tips would be a great help.

Many thanks,
Alan

---

### Post by asearle on 2019-03-12
Hallo everyone,

This problem is driving me crazy ...

I ran ```
cat /proc/bus/input/devices
``` but could see no touchpad in the listing.

Can anyone help me with further diagnostics?

Many thanks,
Alan

---

### Post by asearle on 2019-03-16
Hallo Everyone,

I made some progress with this point but the whole thing is getting seriously weird ...

I decided to give up and to install Windows again. Arrgghh!

So I found a Windows 7 install DVD and started to install. But the Windows 7 install locked up:  I think the new laptop is configured to only accept Windows 10.

After the attempted/aborted install of Windows, I booted to Lubuntu (18.04) again and found "Wonder of wonders" that the touchpad was back. Yippee!!

I took a look at the settings and noted that the touchpad is a ...

```
ETPS/2 Elantech Touchpad
Bus: 0x11
Product: 0xe
Version: 0x0
Connected: isa0060/serio2/input0
```

Then I installed Ubuntu updates and, arrgghh, the touchpad disappeared again.

This is strange because I have a second, older laptop made by the same company, with exactly the same touchpad settings where the touchpad works fine.

So this makes me think that Windows is "messing around" with the BIOS. Or Ubuntu is unable to set something (in the BIOS) which Windows can/does set. 

I found this mention of the problem which sounds like Windows is really messing around with standards ...

[https://askubuntu.com/questions/1033033/elantech-touchpad-does-not-work-i2c-hid]("https://askubuntu.com/questions/1033033/elantech-touchpad-does-not-work-i2c-hidhttp://")

Anyway, I have tried multiple potential fixes but nothing seems to work: I think that the problem is on BIOS level but, although I have fished around in the BIOS settings a lot, I can't seem to clear the problem.

It would be great if someone could point me in the right direction as I am sure that I am not the only one with this problem.

Yours,
Alan

---

