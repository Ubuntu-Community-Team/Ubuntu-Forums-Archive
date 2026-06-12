---
title: "Reverting back to open source AMD graphics driver"
date: 2011-10-23
forum: Hardware
---

### Post by Beryllium on 2011-10-23
(I think)

I've literally spent hours searching for an up to date solution.

In Ubuntu 11.10, I was offered to install the proprietary AMD graphics driver for my 5xxxM GPU. I know the dangers of doing this as I have had problems before but I went and did it anyway (clicked 'activate' in 'additional drivers'. Suprise, suprise, I rebooted and now I'm greeted with a black screen. If I press the power button, some funky terminal stuff comes up and I seem to get the normal shutdown procedure (the ubuntu logo and progress bar). If that matters. More importantly I can boot to the recovery console.

So as the title says I want to go back to the open source driver, which worked fine.

Normally I'd just reinstall but now it's not really an option.

---

### Post by mastablasta on 2011-10-24
try this: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by Beryllium on 2011-10-27
Thanks, that worked perfectly.

---

