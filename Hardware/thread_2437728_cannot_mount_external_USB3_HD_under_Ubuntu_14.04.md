---
title: "cannot mount external USB3 HD under Ubuntu 14.04"
date: 2020-02-28
forum: Hardware
---

### Post by dieter-erich on 2020-02-28
Hi, 
   I cannot mount a 16 TB USB3 HD (xfs formatted) under Ubuntu-14.04. Upon plugging it into a USB3 port gparted, lsusb, and fdisk get stuck and I cannot interrupt with <ctrl c> but rather must close the terminal. 
lsblk reports:   
sdg      8:96   0  14.6T  0 disk 
|-sdg1   8:97   0    16M  0 part 
`-sdg2   8:98   0  14.6T  0 part 
among the other disks of the system. I can access this HD from my laptop running Ubuntu-18.04. What might be wrong? The above system works flawlessly otherwise.
Thanks for hints, H-D

---

### Post by CelticWarrior on 2020-02-28
14.04 is now EoL, end of life and shouldn't be used. 

Please upgrade to a supported release. This is likely to solve your problem too.

---

### Post by yancek on 2020-02-28
> I cannot mount a 16 TB USB3 HD 

The first 16TB drive marketed was in June, 2019 which was AFTER support for 14.04 ended and 14.04 is EOL and there will be no changes so the suggestion in post 2 is the likeliest solution.

---

### Post by guiverc on 2020-02-28
Ubuntu 14.04 LTS is EOL ([http://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/](http://fridge.ubuntu.com/2019/05/02/ubuntu-14-04-trusty-tahr-reached-end-of-life-on-april-25-2019-esm-available/))  as already suggested.  Ubuntu 14.04 LTS can be converted to 14.04 ESM ([https://ubuntu.com/esm](https://ubuntu.com/esm)) which allows extended security maintenance (*a subscription service*).

I do vaguely recall a number of issues being reported in 14.04's last month, which weren't fixed (why fix something in it's last days, inc. security issues with specific usage cases though some of these were scheduled for fix via ESM) but they just seemed encouragement to upgrade to me.  I second CelticWarrior's point.

---

### Post by dieter-erich on 2020-02-28
Thanks for the hints! I am aware of this and I am planning to upgrade but when Ubuntu-16.04 was already available it was impossible to install the two GTX-1070 GPUs on it, whereas it finally worked well on 14.04. I had also tried to update 14.04 to 16.04 but again no way to get the GPUs to work. I believe that 20.04 will be the best choice as soon as it is out but I would have liked to use this HD for backup right now. Can anybody suggest a workaround?

---

### Post by CelticWarrior on 2020-02-28
Yes, 20.04 is a very good candidate.

The GPUs must work the same or better with newer releases, I'm not sure what the problem was with 16.04.
Actually, Nvidia recommended driver version 440 for that card. I don't think you can have that in 14.04. Are you using the open-source driver or an older Nvidia driver? 

For 16.04 or 18.04 I would add the additional graphics drivers PPA to get the 440. Other than that, one or two GTX1070 should work fine with any current Ubuntu release plus Nvidia drivers (and Secure Boot disabled in UEFI machines).

Maybe you are using the open-source *nouveau* that came with 14.04 and that sort of worked but the newer version in 16.04 didn't? Sometimes regressions happen. Anyway, worst case scenario, you would have to boot with the 'nomodeset' parameter to run the live session, install and boot before installing the Nvidia drivers.

---

