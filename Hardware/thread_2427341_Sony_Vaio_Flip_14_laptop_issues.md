---
title: "Sony Vaio Flip 14 laptop issues"
date: 2019-09-20
forum: Hardware
---

### Post by jb92 on 2019-09-20
Hi folks,

So im back again after having issues wtih the backlit keyboard. however ive noticed some new issues with Ubuntu Linux on this laptop.

 1.  battery icon is delayed it detects when the charger is unplugged straight away but when you connect it it is delayed.
2. battery seems to die after shutdown but only with Linux it is fine with Windows 10 tho.
3. CPU Fan is very loud but temperatures are not high.

These are the issues i have come across so far.
Everything else seems to be fine. 

Any ideas? 

Thanks.

---

### Post by CatKiller on 2019-09-20
> **jb92 said:**
> 3. CPU Fan is very loud but temperatures are not high.

You need *something* to control the fan speed. That would be either the motherboard itself or software. From your description, you likely have the motherboard's own ability to control the fan speed turned off in favour of software running in Windows. Obviously that software is of no use to you when you aren't running Windows.

The easy option is to go into your BIOS/UEFI configuration and let the motherboard control your fan's speed.

Alternatively, you can configure **fancontrol** to do it for you in Linux, which is reliant on being able to access sensor and fan speed information through **lm-sensors**. If the sensors that your motherboard uses are supported, it's not especially hard to do that, and you might be able to configure them to be quieter than your motherboard's fan profiles would set them.

---

### Post by jb92 on 2019-09-20
Thanks for your reply. 

I discovered that Wake on Lan was enabled i disabled it in Ubuntu no option in the BIOS.

lm-sensors does not show the speed of the fan so i guess it cant be controlled by lm-sensors it is a common problem.

Battery drain is still bad in Ubuntu. i cant test until i leave it with 100% battery before i go to bed.

---

