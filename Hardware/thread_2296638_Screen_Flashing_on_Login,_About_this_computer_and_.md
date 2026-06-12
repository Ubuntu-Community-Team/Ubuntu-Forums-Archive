---
title: "Screen Flashing on Login, About this computer and other sytem settings."
date: 2015-09-27
forum: Hardware
---

### Post by hey2 on 2015-09-27
Hi.

I just installed Ubuntu on my desktop and I'm having some problems.

When the computer starts, i see the screen flashing. This behavior is also present when i log in and every time i click on about this computer and some of the system settings.

It's not like a change in monitor refresh but more like a instant flash. It reminds me of an eye blinking.

It seems like there's some process behind, but instead of being hidden,  it comes to the foreground for a brief moment.

Does anybody seen something like this?

---

### Post by Bucky Ball on 2015-09-27
Is this a consequence of trying to fix [this]("http://ubuntuforums.org/showthread.php?t=2296636"), and if so, what did you do to fix it and cause the current situation?

---

### Post by hey2 on 2015-09-27
> **Bucky Ball said:**
> Is this a consequence of trying to fix [this]("http://ubuntuforums.org/showthread.php?t=2296636"), and if so, what did you do to fix it and cause the current situation?

Hi.

Thank you very much for your answer.

No. It's a fresh install and i didn't try anything to fix both of the problems. 

Before i installed, i tried the live USB and the flashing was also present.

Thank you once again.

---

### Post by Bucky Ball on 2015-09-27
Once you have logged in, does the system work fine?

---

### Post by hey2 on 2015-09-27
> **Bucky Ball said:**
> Once you have logged in, does the system work fine?

Hi.

Yes everything seems to be working fine.

No error, no crashes.

When i click about this computer and on some of the system settings (monitor, change desktop, etc...) it flashes but it doesn't cause any issue. At least that i see.

I just don't understand why in my desktop does this and on my laptop it doesn't.

---

### Post by Bucky Ball on 2015-09-27
Please open a terminal and:

```
sudo lshw -C video
```

Post the output here. Have you installed any drivers from 'Additional Drivers' or did you have 'Install third-party drivers' ticked when you installed Ubuntu?

---

### Post by hey2 on 2015-09-27
> **Bucky Ball said:**
> Please open a terminal and:

```
sudo lshw -C video
```

Post the output here. Have you installed any drivers from 'Additional Drivers' or did you have 'Install third-party drivers' ticked when you installed Ubuntu?

 *-display               
       description: VGA compatible controller
       product: RV620 LE [Radeon HD 3450 AGP]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:16 memory:e0000000-efffffff ioport:c000(size=256) memory:fe9f0000-fe9fffff memory:fe9c0000-fe9dffff

---

### Post by Bucky Ball on 2015-09-27
Do an update and then open 'Additional Drivers'. Do you see anything in there relating to Nvidia or graphics?

---

### Post by hey2 on 2015-09-27
Hi.

I just tried, but unfortunately everything is up to date and theres no additional drivers.

---

### Post by hey2 on 2015-09-30
Hi.

Just a bump and a quick update.

I was doing a clean install and i noticed this issue also happens on the install menu.

Does anybody know what could this be?

It only happens on the login screen, immediately after the login and every time i click about this computer, change desktop background and on monitor settings.

I don't see this happen when i open programs.

Thanks.

---

### Post by hey2 on 2015-10-01
We're making progress!

I tried to connect the monitor through the dvi port (vga to dvi adapter) and it doesn't show the flashes. It's completly normal.

I tried before with windows and i know it's not a hardware problem.

What could be making this happen?

---

