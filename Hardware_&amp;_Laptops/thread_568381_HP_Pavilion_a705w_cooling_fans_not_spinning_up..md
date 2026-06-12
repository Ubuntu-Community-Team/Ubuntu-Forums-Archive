---
title: "HP Pavilion a705w cooling fans not spinning up."
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by digger95 on 2007-10-05
Hi all and thanks in advance.

My system specs:

HP Pavilion a705w desktop
MSI MS-6577 rev. 4.1 motherboard
Intel Celeron D 2.93Ghz processor
Phoenix AwardBIOS 6.00PG (HP Ver. 3.25 4/12/2005)
80GB Western Digital hd
512MB ram
Onboard sound (AC97)
Onboard video (Intel 82845G)
Onboard ethernet (Realtek)
Kworld PCI video capture card 2388x

Ubuntu 7.04 with acpi=off (otherwise the kernel wouldn't load).

All of the above hardware was recognized correctly right out of the box which I must say impressed me.  Unfortunately I think there's a deal-breaker with the cooling fans.  My cpu and rear case fan are not spinning up like they should under load.  They ARE running... about 1500 rpm each... which is normal.  They're just not kicking into high gear like they should when this Prescott gets above 60C or so.  I have been able to access and monitor the winbond sensors using mbmon in a terminal window.

I hate like heck to give up already after being a new Linux user for only three days, especially given how much I'm lovin Ubuntu, and the fact that everything is running perfectly except for the fans.  But it does appear from my exhaustive search that my HP may simply not be Linux-friendly.   The BIOS is dummied down and non-configurable for the most part, and the machine may well be designed to run with the OEM Windows XP that came bundled with it and nothing else.  

What seems odd is that after installing Ubuntu the fans don't even spin up when rebooting or when I'm in the BIOS, and they always did before with XP.  I'd always assumed that the BIOS controlled the fans and not the operating system.  At any rate I need a working system by monday but thought I'd give it another few days tinkering before re-installing XP.

Thanks much for any ideas!

Dig

---

### Post by dinub1 on 2007-10-05
Maybe that it is not using that much CPU power in order that fans start working. HAve you checked that your Prescott CPU is overheating?

Ubuntu latest version uses power in a very dynamic way. Make sure you check the issue.

---

### Post by digger95 on 2007-10-05
Hi dinub1,

Thanks so much for your response.  

I have in fact been monitoring the system temps through mbmon.  On several occasions now the cpu temp has exceeded 70C without the fans kicking on.  This would not be the case with Windows XP.  Just wondering if there are some variables with Ubuntu that I need to set?

Also, does it make a difference that i had to set acpi=off to get Ubuntu to load?  Do i need to download a third-party app perhaps that monitors and controls my fanspeeds without acpi?

Thanks again  :)

Dig

---

### Post by dinub1 on 2007-10-05
> **digger95 said:**
> Hi dinub1,

Thanks so much for your response.  

I have in fact been monitoring the system temps through mbmon.  On several occasions now the cpu temp has exceeded 70C without the fans kicking on.  This would not be the case with Windows XP.  Just wondering if there are some variables with Ubuntu that I need to set?

Also, does it make a difference that i had to set acpi=off to get Ubuntu to load?  Do i need to download a third-party app perhaps that monitors and controls my fanspeeds without acpi?

Thanks again  :)Dig

hi digger95,
You are very welcome.
Alright. Then your CPU is indeed overheating and at approx 70C your fan should be working and hard :)
Listen. Ubuntu 7.04 and 7.10 have both this issue. Sometimes CPU works at full power even if it is not needed. I had this problem on this laptop too, when I upgraded from 7.04 to 7.10 beta... the CPU cooling fan ran continuously without stops, and CPU temp reached like 65 C. I couldn't control it. Though one command can reduce the CPU frrequency to safe values but that will reduce the CPU power on computations.
Try typing:

$ sudo cpufreq-selector -g powersave

And see what the temperature reads. It should get lower, to safe values. And yes, fan should operate. If it does not, that is not good.

The only measure that helped was to erase my Linux partition (I have Windows XP on a different partition) and reinstall Ubuntu 7.10 beta from scratch. That fixed the overheating issue on my laptop. There is apparently a bug in the latest versions that cases the CPU control power to malfunction, causing CPU overheating, and possible damage to the CPU. I don't know what that is and how, but this is a known issue with latest version of Ubuntu. Be carefully with that. I know Windows XP does not display that malfunction and this is a luck. Generally on a well designed motherboard, BIOS should shut down the power when it detects a certain CPU temp and prevent damage to it. I am sorry that I couldn't help more.

---

### Post by dinub1 on 2007-10-05
*[COLOR="Navy"]All of the above hardware was recognized correctly right out of the box which I must say impressed me. Unfortunately I think there's a deal-breaker with the cooling fans. My cpu and rear case fan are not spinning up like they should under load. They ARE running... about 1500 rpm each... which is normal. They're just not kicking into high gear like they should when this Prescott gets above 60C or so. I have been able to access and monitor the winbond sensors using mbmon in a terminal window.[/COLOR]*

Hold a sec dig. Let me understand.. I was under the impression that the CPU fan isnt running at all. So it runs, but apparently it is thermo regulated and it does not run at higher speed in order to cool more efficiently the CPU. And the rear case fan..... is that thermo regulated as well? I never saw such a thing... 
The CPU fan can be auto regulated by the BIOS provided BIOS provides that. Apparently it does on your machine. But the rear fan? That thing I do not know how it is regulated... Maybe Ubuntu does not know about it... :)

But the CPU fan should work "normally" And it shouldn't let the CPU reach 70C which is quite a dangerous value.

---

### Post by digger95 on 2007-10-05
Hi dinub1 and thanks again for your help,

Normally (under Windows XP) both the rear case fan and the cpu fan would increase in speed to compensate for increased system temps.  They have always in the past kicked on together.  This is not happening in Ubuntu.  They just stay at the same constant low speed.  

To be honest, I am not interested in scaling back my cpu to compensate for the temperature increase, I would really just like my fans to kick in and provide the same type of increased cooling they did under Windows XP so I can perform the same tasks without worry.

If this is not possible I will reload XP and just chalk it up to a Linux error.  I'd just like to find a way to make my system run well under Ubuntu.  I do like it very much.

Thanks,

Dig

---

### Post by digger95 on 2007-10-05
Dinub1,

Just to be clear, we are talking about my two cooling fans here... the rear case fan and my cpu fan.  NOT the power supply fan which is obviously a different matter altogether and functions independently of everything else.  There is no problem there.  We're just talking about the cpu fan and exhaust fan, both of which formerly were controlled well under Windows XP.

Dig

---

### Post by dinub1 on 2007-10-05
> **digger95 said:**
> Hi dinub1 and thanks again for your help,

Normally (under Windows XP) both the rear case fan and the cpu fan would increase in speed to compensate for increased system temps.  They have always in the past kicked on together.  This is not happening in Ubuntu.  They just stay at the same constant low speed.  

To be honest, I am not interested in scaling back my cpu to compensate for the temperature increase, I would really just like my fans to kick in and provide the same type of increased cooling they did under Windows XP so I can perform the same tasks without worry.

If this is not possible I will reload XP and just chalk it up to a Linux error.  I'd just like to find a way to make my system run well under Ubuntu.  I do like it very much.

Thanks,

Dig

Question. Do you have a Ubuntu 7.04 or 7.10 Live CD? I assume that you do. When you load it and run from it, with acpi=on or off, can you repport the condition of  the fans? Try running Firefox or some other sort of application and let it run. Do the fan still run slow or they rev. at the correct speed? If the overheating does not happen, then there is a problem with the Ubuntu installation. Do not give up so quickly. This is a known issue that may be fixed when the 7.10 is stable and is released by this month.

---

### Post by digger95 on 2007-10-05
Dinub1,

I have an Ubuntu 7.04 alternate cd (text-based) which was necessary to install it on my system.  Are you saying that these issues were fixed in the upcoming version?  I need my computer working by monday.  Should I download a release candidate of 7.10 to see if this issue is fixed?

Thanks again so much.  You have been so kind.

Dig

---

### Post by digger95 on 2007-10-05
Dang,

I'm sorry to hear that there is no resolution to my problem.  To be honest, I have read many dozen posts now from other people with similar hardware and it seems this has been an issue for several years now without a resolution.  I guess I will reload Windows.  I hope that the Linux development team catches up with this.

Thanks to everyone for their help.

Dig

---

### Post by dinub1 on 2007-10-06
> **digger95 said:**
> Dinub1,

I have an Ubuntu 7.04 alternate cd (text-based) which was necessary to install it on my system.  Are you saying that these issues were fixed in the upcoming version?  I need my computer working by monday.  Should I download a release candidate of 7.10 to see if this issue is fixed?

Thanks again so much.  You have been so kind.

Dig

OK. I see now. You have an alternate installation CD. Try downloading the regular Ubuntu Live CD instad and run it as a Live CD. The alternate CD only allwow installation of Ubuntu but does not allow to run by itself.

However I say that hopefully these issues may be fixed in the released version. What I suggested was that you load the Live Ubuntu CD (You need to download and burn one, you apparently do not have it)  and with the Live CD running only, monitor the activity of the related fans. If they operate normally with the Live CD running, and they don't with the installed version, my claim was that something went wrong with the installed Ubuntu which may be fixed with a fresh reinstall. You are welcome and I am glad if I could assist you solving your issues.

---

### Post by digger95 on 2007-10-07
Hi Dinub1 and anyone else with insight into this problem...

Quick recap:

My cpu fan and rear case fan DO run under Ubuntu 7.04... about 1500 rpm each which is perfectly normal at idle.  They just don't INCREASE in speed like they should under heavy cpu load.  Ubuntu is allowing the cpu temp to exceed 70C without ever spinning my fans up for cooling.  Windows XP does this properly at 60C.

I downloaded a 7.10 Beta live cd per dinub1's request, and to my surprise it did startup and run properly without any input from me.  However the fans still aren't working properly and when I look at dmesg it still appears that acpi is disabled.  It's just that 7.10 does this automatically now where 7.04 required me to enter acpi=off at boot.  Same thing really.

Something in the linux kernel is disabling fan control.  I just don't know what.  I'm too new.

I'm very willing to accept that this is simply an issue of my HP not being linux-friendly.  Just thought I'd keep plugging at it in the meantime.  I REALLY would like to get linux running on this machine.  I want to learn it and use it.  But I can't afford to burn the poor thing up in the process.  :)

Any further ideas would be most welcome.

Dig

---

### Post by digger95 on 2007-10-07
Dinub1... yes, both the rear case fan AND the cpu fan are thermal regulated.  They both plug into the motherboard, and both spin up at the same time when the cpu and/or case temps heat up.  This is independent of the power supply fan which does it's own thing regardless.

---

### Post by digger95 on 2007-10-11
Hi,

Just wanted to close this thread...

After re-installing XP on my machine, I've tried several 'live' cd's of Ubuntu and other distros, and even those somehow manage to throw my cooling fans out of whack and I don't get them back until I re-install XP.  I thought the live cd's weren't supposed to permanently  influence your system in any way, but apparently that is not the case with my machine.

At this point I'm chalking it up to a machine-specific issue.  My HP has a dummied-down bios that prevents making the necessary changes to load any OS besides Windows.  I'm sure that if I spent the time I could find a way to force my cooling fans to work under Ubuntu, but I simply don't have the time or knowledge right now to do it.

Thanks for your help,

Dig

---

### Post by dinub1 on 2007-10-11
> **digger95 said:**
> Hi,

Just wanted to close this thread...

After re-installing XP on my machine, I've tried several 'live' cd's of Ubuntu and other distros, and even those somehow manage to throw my cooling fans out of whack and I don't get them back until I re-install XP.  I thought the live cd's weren't supposed to permanently  influence your system in any way, but apparently that is not the case with my machine.

At this point I'm chalking it up to a machine-specific issue.  My HP has a dummied-down bios that prevents making the necessary changes to load any OS besides Windows.  I'm sure that if I spent the time I could find a way to force my cooling fans to work under Ubuntu, but I simply don't have the time or knowledge right now to do it.

Thanks for your help,

Dig

Dig, that is not so... I am typing now on a HP made laptop (HP Pavilion ZE4145), running Ubuntu 7.10 beta, and after a new install, it has no problems with cooling issues or fans... And this is model 2002... A very strong a reliable machine.  Best of luck buddy.

---

### Post by Githlar on 2007-10-13
I have the same HP Pavilion a705w. I tried the cpufreq-selector command but I got this:

```
No cpufreq support
```

---

### Post by digger95 on 2007-11-06
Hi Githlar (and all)...

Just wanted to post an update.  

The latest Linux kernel (2.6.23.1) seems to have resolved a lot of acpi issues.  The machine you and I have (HP Pavilion a705w) now runs perfectly without having to turn acpi=off at boot.  

What's more, my cooling fans now work exactly as they should without the need to use lm_sensors and pwmconfig to generate a fancontrol script.  My fans now work out of the box exactly as they did under WinXP with the proper temperature threshholds.

I even have system standby again.

Seemingly this was an issue with acpi implementation in the Linux kernel, and has been resolved in 2.6.23.1

Dig

---

