---
title: "Problems with video cards in SONY VAIO VPCSB"
date: 2011-09-18
forum: Hardware
---

### Post by Daniao on 2011-09-18
Dear all,

I am running Natty 11.04 in a Sony Vaio VPCSB laptop, and when I just upgraded I had lots of problems with the Video cards (e.g. freeye on booting). Reading through the forums I found some helpful posts, and now my system is running more or less stable, although the battery life is still too short (<2h), therefore I would like to check with you if my current configuration is correct or if I could do anything to improve it.

My high level understanding of the problem is that the Vaio comes with two graphic cards, one from ATI with a radeon driver that is problematic, and an integrated Intel one. The solution seems to be to disable the ATI one and use only the Intel one, which also results in much less power.

This is my current setup:

1) Video cards:

:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]

2) As suggested in some posts I blacklisted radeon and edited /etc/rc.local in the following way:

/etc/modprobe.d/blacklist.conf: 
blacklist radeon

/etc/rc.local:
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch


3) The contents of /sys/kernel/debug/vgaswitcheroo/switch are:

:~$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

4) I still have some error when I boot:

dmesg -c
[Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.

4) These are the video modules that are loaded after booting:
radeon                925094  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  2 radeon,i915
drm                   184164  6 radeon,ttm,i915,drm_kms_helper
i2c_algo_bit           13184  2 radeon,i915


5) I am running X with the open source driver, I do not use any proprietary video driver, like fglrx.


So my questions are:

- Is it true that the ATI card is disabled in my system and I only use the Intel one?

- Battery life is still quite short, however I found people saying that their battery life had improved a lot when solving this problem, so I guess there is still something that I am doing wrong. Any idea what it is ?


Best Regards


Daniel

---

### Post by adm1968 on 2011-09-24
> **Daniao said:**
> Dear all,

I am running Natty 11.04 in a Sony Vaio VPCSB laptop, and when I just upgraded I had lots of problems with the Video cards (e.g. freeye on booting). Reading through the forums I found some helpful posts, and now my system is running more or less stable, although the battery life is still too short (<2h), therefore I would like to check with you if my current configuration is correct or if I could do anything to improve it.

My high level understanding of the problem is that the Vaio comes with two graphic cards, one from ATI with a radeon driver that is problematic, and an integrated Intel one. The solution seems to be to disable the ATI one and use only the Intel one, which also results in much less power.

This is my current setup:

1) Video cards:

:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]

2) As suggested in some posts I blacklisted radeon and edited /etc/rc.local in the following way:

/etc/modprobe.d/blacklist.conf: 
blacklist radeon

/etc/rc.local:
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch


3) The contents of /sys/kernel/debug/vgaswitcheroo/switch are:

:~$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

4) I still have some error when I boot:

dmesg -c
[Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.

4) These are the video modules that are loaded after booting:
radeon                925094  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  2 radeon,i915
drm                   184164  6 radeon,ttm,i915,drm_kms_helper
i2c_algo_bit           13184  2 radeon,i915


5) I am running X with the open source driver, I do not use any proprietary video driver, like fglrx.


So my questions are:

- Is it true that the ATI card is disabled in my system and I only use the Intel one?

- Battery life is still quite short, however I found people saying that their battery life had improved a lot when solving this problem, so I guess there is still something that I am doing wrong. Any idea what it is ?


Best Regards


Daniel

[FONT="Georgia"]Hi, Daniel
Take a look at this thread
[http://ubuntuforums.org/showthread.php?t=1731232&highlight=Sony+Vaio+13%2C3+VPCSB2S9E+Intel+Core+i5+2410M&page=11](http://ubuntuforums.org/showthread.php?t=1731232&highlight=Sony+Vaio+13%2C3+VPCSB2S9E+Intel+Core+i5+2410M&page=11)
I followed the instructions yesterday, and my battery life increased a lot, right away
Still getting problems with hibernate/resume, though :confused:[/FONT]

---

### Post by Daniao on 2011-09-30
Hi adm1968,

Thanks for the link, it work very well.

Regarding the suspend/hybernation functionality I think that you need two other things besides what is said in the post:

1- Give execution rights to the script
sudo chmod +x /etc/pm/sleep.d/10_disable_radeon

2- Add the following line to the end of /etc/modprobe.d/blacklist.conf:
blacklist radeon

Cheers

Daniel

---

