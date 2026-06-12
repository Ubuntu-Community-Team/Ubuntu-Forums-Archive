---
title: "AspireOne D150 goes on standby"
date: 2009-11-06
forum: Hardware
---

### Post by Nonno Bassotto on 2009-11-06
I have an Acer Aspire One D150 and I've installed yesterday UNR Karmic. It was a clean install over a previous UNR Jaunty, which used to work fine.

My problem is the following. Whenever I attach or detach the power cable, the netbook goes in standby. Or at least I believe so, it only takes a couple of seconds. After that I can wake it up with the power button as usual.

Apart from the obvious annoyance, I am a bit worried that there is something faulty in the power management in Karmic that could possibly to ruin the hardware.

---

### Post by TheTilde on 2009-11-06
gnome-power-preferences should be checked, maybe.

---

### Post by Nonno Bassotto on 2009-11-06
The power preferences are reasonable. Moreover I don't know of any setting that sends the PC to stanby when you plug in the power cord...

---

### Post by Elektrisk on 2009-11-06
I have exactly the same problem with my Medion WIM 2030. I did not have this problem with Ubuntu 9.4.
I also lose the wireless network when going to standby. NetworkManager 0.7.996 doesn't restart when I wake the machine again.

---

### Post by Nonno Bassotto on 2009-11-07
I didn't change anything, but now the computer only suspends when I unplug the cord, and not when I plug it in.

Is there any acpi or pm guru who can suggest where to look to start having a clue? Otherwise I fear I will have to go back to 9.04 :-(

---

### Post by ridinvintage on 2009-12-13
Im having the same problem on my d150. it goes into standby every time I plug in or unplug.

---

### Post by Nonno Bassotto on 2009-12-15
It seems that mine was a problem with faulty packages on the downloaded image. I just reinstalled every package with the word "power" in it, and now everything is working :D

---

### Post by anglican on 2009-12-18
> **Nonno Bassotto said:**
> I have an Acer Aspire One D150 and I've installed yesterday UNR Karmic. It was a clean install over a previous UNR Jaunty, which used to work fine.

My problem is the following. Whenever I attach or detach the power cable, the netbook goes in standby. Or at least I believe so, it only takes a couple of seconds. After that I can wake it up with the power button as usual.

Apart from the obvious annoyance, I am a bit worried that there is something faulty in the power management in Karmic that could possibly to ruin the hardware.

I found that a bios update cured this problem for me.

H

---

### Post by libssd on 2010-05-20
> **anglican said:**
> I found that a bios update cured this problem for me.

H

:KS I found this tidbit at: [https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

[LIST]
[*]Did not suspend/hibernate on lid close. Upgrading BIOS to 1.11 version helps.
[*]Un/plugging AC causes netbook to suspend. With BIOS ver 1.11 this was fixed.
[/LIST]

Since *"...a BIOS update cured this problem"* is a little terse, and there are huge risks (such as a bricked computer) if a BIOS update goes wrong, here is a more detailed description.

Acer BIOS updates are available at: [http://gd.panam.acer.com/home/]("http://gd.panam.acer.com/home/")

Two BIOS 1.11 update packages are available for the D150:

BIOS_Acer_1.11_A_A.zip 917.7 KB 2009/11/17
BIOS_Acer_1.11_A_AOD150.zip 2.3 MB 2009/09/21

The larger, earlier one is preferable if you have Windows, with Ubuntu installed in a partition, as you can run it live. There is a readme file:

> Windows flash: Please click "KAV10111.exe" to update bios.

Neither the readme nor KAV10111.exe are included in the later version.

I'm now at BIOS 1.11, and for the first time ever, the machine goes to sleep in Ubuntu 9.04 when I close the lid.  :P 

Boot time with BIOS 1.11 is about 5 seconds faster; not much, but every little bit helps.

I may even decide to give Ubuntu 9.10 another try. 10.4 still has far too many things that do not pass on the D150 compatibility chart.

Thanks to people here, at the [Acer Aspire One User Forum]("http://www.aspireoneuser.com"), and at the [macles*]("http://macles.blogspot.com/") site for sharing information about the pitfalls of BIOS upgrades.

---

