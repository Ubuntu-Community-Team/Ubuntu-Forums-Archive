---
title: "Asus Zenbook UX331UN - wake up from suspend only with external power supply"
date: 2018-02-28
forum: Hardware
---

### Post by ael-earlyup on 2018-02-28
Hey community,

_The laptop:_
I have an issue with my new **Asus Zenbook UX331UN 16GB/512GB**. (i7 Quad-Core 8te Gen., Nvidia MX150) and Ubuntu 17.10 with kernel: *Ubuntu 4.13.0-36.40-generic 4.13.13*

_The problem:_
 If the laptop goes into suspend (or hibernation), the laptop stops working, as it should. If I wake it up, the following happens, depending on the configuration:

**  1. External Power Supply, using "X.OrgXserver-Nouveau display driver":**
Laptop wakes up as it should. This means the login page shows up.

**  2. External Power Supply, using NVIDIA binary drier version 384.111(proprietary) or 387.35(open source) or 390.25(open source): **
Laptop starts working (fans start working, LED of power button turns on), display turns on but shows on a black screen the following message:
[I][    70.461081] rtc_cmos 00:01: Alarms can be up to one month in the future
[    74.522401] NVRM: Xid (PXI:0000:01:00): 32, Channel ID 00000000 intr 80040000[/I]
Can't switch to console (via Ctrl-Alt-F...). I have to cold boot.

**  3. Battery (no external supply), using "X.OrgXserver-Nouveau display driver":**
Laptop starts working (fans start working, LED of power button turns on), yet display stays completely black.
Can't switch to console (via Ctrl-Alt-F...). I have to cold boot.

**  4. Battery (no external supply), using NVIDIA binary drier version 384.111(proprietary) or 387.35(open source) or 390.25(open source): **
Same as before with Battery ... display stays completely black.


_What I tried:_
I already tried to solve this problem with the common solutions as using other drivers (as you see this doesn't work). I updated the BIOS to the newest available version, too. Changing to manual wakeup at BIOS (now I have to push the power button) does not work.

Adding "nomodeset" as boot option to grub with the NVIDIA drivers, the Laptop is not able to boot anymore, but in some kind of loop.
If I add it to the Nouveau driver, the display is in 800x600 (and can't be changed), but waking up from suspend without power supply works fine. However, this is not a satisfying workaround, because buying an expensive laptop and not using its graphics card is a waste of money.

All other workarounds for similar problems I found on the web did not work... or at least I was not able to implement them. Quite often the Ubuntu version was very different from the current 17.10.

Well ... and I tried Ubuntu 16.04 and Linux-Mint 18.3 in Live-Mode, too ... same problem.

_My guess:_
So, I guess the problem is the graphics card in general ... yet it's a pain in the ***, since it works as long as it is connected to external supply. I don't care about the NVIDIA drivers and I would be totally happy if it works with the Nouveau driver. 


Does anyone have an idea how to fix this? I'm not an expert, so if you have any solutions, plz. try to explain how to do it. 
... if I don't get it work within 5 days, I will hand the laptop back to the store to safe the money. Sorry if this problem was already posted ...
Thank you for your help in advance! =)

---

### Post by magsoft on 2018-03-01
I also recently bought an Asus Zenbook UX331U and I managed to have wake up working by upgrading to the development version of Ubuntu 18.04.
Now wake up works on battery and on external power with the Nouveau and the NVIDIA proprietary v390 drivers.

---

### Post by ael-earlyup on 2018-03-02
The NVIDIA driver make still problems, yet Nouveau driver works fine after update to 18.04 development version.

Worked for me. Thanks a lot.

---

### Post by foxy123 on 2018-03-10
Sorry for sort of highjacking the thread, but do you guys happy about UX331UN? I'm agonising between buying this one or Dell XPS 13.

---

### Post by gsteyn on 2018-04-06
Are you now happy with Ubuntu on the UX331UN, or are there also other problems? Would you recommend this laptop for Ubuntu?

---

