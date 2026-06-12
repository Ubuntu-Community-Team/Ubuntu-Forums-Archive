---
title: "Acer Aspire One Cloudbook (11&quot;) - Battery draining when powered off !"
date: 2016-07-03
forum: Hardware
---

### Post by martin-hochdekker on 2016-07-03
Hello,

I am using an Acer Aspire One Cloudbook (AO1-131-C58K) with the latest Ubuntu 16.04 MATE installed. Before that I used Lubuntu 16.04 with the same issue as follows:

[B][U]The problem:
[/U][/B]After I properly power-off (shutdown) the Notebook via the Ubuntu menu, the battery continues to drain power. It takes ~ 1 week to empty the battery from 100% -> 10%.


_**What I have done so far:**_
(1) I opened the case of the notebook to reach the wires of the battery pack, connected to the motherboard. I used a voltmeter to measure the voltage on the power-wires (black/red). It is about ~7,6 Volts in Ubuntu idle and the same voltage when the laptop is completely powered off !!

(2) I unplugged the battery pack from the motherboard once waiting 1 minute and another time leaving it over night unplugged ... then plugged it in again into the motherboard and the motherboard instantly consumed power from the battery, without me pressing any buttons !!

(2.1) I therefor think that the issue must be CPU, GPU, RAM or Motherboard related. I ruled out wlan as i physically disconnected it from motherboard. There must be something that constantly draws power and doesn't have a "start / shutdown button". Also I was kinda surprised that I didn't find any CMOS battery?!

(2.1.1) Consequently I think the problem is in BIOS / UEFI / Firmware - but not the operating system.

(3) I tried all different BIOS configurations with no success.

(4) Facing the problem with Lubuntu 16.04 already, I already installed all the latest Acer Firmware / BIOS from their website. Therefor I had to reinstall a Win10 copy to do the BIOS flashing.

(5) I read that the Intel Management Interface might be causing the drainage of the battery when powered off. But I am not sure if its the case here. Though I read some very disturbing facts about this "security feature"...


(6) The Notebook was shipped with Windows 10 Home 64bit preinstalled. Due to enormous RAM-consumption of Win10 (~1,5GB) it was not possible to use it in any productive environment. Therefor I installed Lubuntu and later Ubuntu Mate. I installed it with UEFI and Secure Boot, and everything works well. Except, that the battery is draining power while the notebook is completely shut down!! 



_**Specifications**_ (from #~ lshw)
Aspire one 1-131 (AO1-131_106C_1.10)
Insyde BIOS vers. 1.10 (28-12-2015)

CPU: Intel Celeron N3050
GPU: Intel HD Graphics 400 (Braswell)
Motherboard: Acer Caltech vers. 1.10


I decided to post this issue here, because I was told here are some high tech-savy persons. Even though it is probably not 100% an Ubuntu issue. If there is someone with the same machine model, PLEASE write your experience with it. I couldn't find anyone else using the same notebook. :(



Sincerely,
Martin

---

### Post by fuseblower1123 on 2016-08-02
I have this problem too. Similar drain rates (approx 15%/day). I'm on BIOS 1.10 too, but it occurred as well under 1.08. No solution from here yet; certainly not OS related though as it occured before I removed windows from the machine.

---

### Post by magiza83 on 2016-11-12
Hello,

I´ve also have an Acer Aspire One Couldbook 11'' but mine has Bios 1.05 and I´m also facing battery drain when it is shutdown. Do you know in which BIOS version the issue is solved?

---

### Post by MartyBuntu on 2016-11-12
Try disabling WOL (Wake On LAN) from the BIOS and from inside the operating system itself.

---

### Post by magiza83 on 2016-11-15
this laptop does not have WOL. Have to you tried it? There is no option from the BIOS and ethtool does not show wol either.

---

### Post by tomas678 on 2017-05-27
I have the same device and also the same problem.
The only work around I have found so far is to press the battery reset button underneath the computer after I turn it off.
There is a tiny hole with a symbol that look like disconnected battery underneath. It is possible to insert a needle and gently press to activate the reset.
I actually removed the cover to see what was going on and I can see that two lines that normally is 3.3V gets pulled to GND when the button is pressed. I suspect that it is SDA and SCL to the battery controller but it could also be something else.

I did an experiment and charged the computer to 100% and then turned it off and then pressed the reset button.
After exactly three days I booted up and the battery-indicator showed 93%, not great but at least acceptable.

I'm using Arch linux with XFCE but I guess that the behavior is the same for Ubuntu.

---

