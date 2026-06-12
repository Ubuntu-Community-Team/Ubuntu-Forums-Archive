---
title: "Intel NUC failure (twice), Intel blames Ubuntu's sleep state management"
date: 2015-02-14
forum: Hardware
---

### Post by Choucroute on 2015-02-14
Hi, I am looking for some advice one the following issue.

I bought a NUC (model D34010WYK) last November to use as a media centre. I installed Ubuntu Desktop and it was working fine for a month, then one day I wasn't able to wake it up from standby. I unplugged the power cable, then tried to boot it but the NUC appeared dead.

Intel sent me a new one, I transferred RAM and SSD from the old one, and it was working fine until 2 weeks ago where the exact same problem occurred... Came back to Intel tech support, they escalated it, then yesterday they came back to me with the following reply:

> [TABLE]
[TR]
[TD]It is believed that the memory you are using in conjunction with the[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD]Linux Ubuntu operating system is causing the issue you are having. It[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD]could also be the operating system not working well with the sleep state[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD]as well.[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD]With this we suggest that you either for the replacement NUC either to[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD]not use Linux Ubuntu, that specific memory or sleep state to prevent the[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD]issue from happening again.
[/TD]
[/TR]
[/TABLE]


So they imply that Ubuntu could have caused the hardware failure.

Is that even possible or are they talking nonsense?

---

### Post by oldfred on 2015-02-14
What RAM are you using?
Spec says this:
> Two SO-DIMM slots supporting up to 16 GB of 1600/1333 MHz 1.35V [DDR3L memory]("http://www.intel.com/support/motherboards/desktop/sb/CS-034475.htm") (Note: 1.5V DDR3 memory is not supported)

There have been other posts on sleep/standby type issues, but I have not followed them.

---

### Post by Choucroute on 2015-02-14
I am using two Crucial 4GB 1.35V DDR3L CT51264BF160BJ, which are listed as compatible on the Intel support website (here: [http://www.intel.com/support/motherboards/desktop/sb/CS-034586.htm](http://www.intel.com/support/motherboards/desktop/sb/CS-034586.htm) )

I found that multiple people had the same issue on the Intel support website (all on Linux)
See: [https://communities.intel.com/message/277645#277645](https://communities.intel.com/message/277645#277645)

Edit: I have managed to bring the NUC back to life by removing the CMOS battery for two minute before putting it back in. I will just need to avoid putting the unit in standby from now on!

---

### Post by kerry_s on 2015-02-14
i was just shopping nuc's over at amazon, guess i'll look at the gigabyte versions instead. 
thanks for the heads up.

---

### Post by wolfv6 on 2015-07-04
I had the same problem with my NUC.
There is a bug in the NUC BIOS, and somehow Linux suspend triggers this bug.
The fix is to not suspend NUC from Linux until the NUC BIOS is patched.
Here are the details: [https://communities.intel.com/thread/76708](https://communities.intel.com/thread/76708)


I would not have purchased an Intel NUC if I was aware to the bug, I regret buying it:mad:


After I told Intel Support that "My NUC D54250WYK won’t boot", Intel Support told me, "We can't speak on the reliability of Linux distros in the NUC since we have only focused on Windows to this point, though we don't expect major issues on it."

---

### Post by Yellow Pasque on 2015-07-04
It's not just NUC's. My system (AMD Phenom II, RadeonHD 4550 with open-source radeon driver) also hates suspend and I have to reset the BIOS. There are tons of "suspend/resume failure" bug reports on Launchpad. In fact, I don't think I ever got a system running Linux to successfully suspend.

---

### Post by wolfv6 on 2015-07-05
> **Temüjin said:**
> It's not just NUC's. My system (AMD Phenom II, RadeonHD 4550 with open-source radeon driver) also hates suspend and I have to reset the BIOS. There are tons of "suspend/resume failure" bug reports on Launchpad. In fact, I don't think I ever got a system running Linux to successfully suspend.

I understand suspend not working on many BIOS.  But to brick on suspend?
The NUC will not boot to BIOS after suspend.
To reset the NUC BIOS after suspend, it is necessary to open the case and disconnect the CMOS battery.

---

### Post by Yellow Pasque on 2015-07-05
There's no CMOS reset button (or at least a jumper)?

---

### Post by Yellow Pasque on 2015-07-05
Okay, I just looked at the Intel NUC manual, and it gives this procedure:
```
1. When the Intel® NUC is off, press and hold the power button for approximately 3 seconds and then release it. The Power Button menu should appear.
2. Press F2 to enter Intel Visual Bios.
3. Press F9 to restore BIOS factory default values.
4. Press F10 to save and exit Visual BIOS.
```
[http://www.intel.com/support/motherboards/desktop/sb/CS-034634.htm](http://www.intel.com/support/motherboards/desktop/sb/CS-034634.htm)

---

### Post by wolfv6 on 2015-07-06
That's how NUC normally works, but after suspend, the power button is unresponsive.
This doesn't happen with every suspend, but once the power button is unresponsive, the only way to unbrick the NUC is to unplug the CMOS battery.
Intel support told me to unplug the CMOS battery.
NUC has no CMOS reset button.  The CMOS jumper only resets some settings.

---

### Post by NaneK on 2015-07-06
> **Temüjin said:**
> It's not just NUC's. My system (AMD Phenom II, RadeonHD 4550 with open-source radeon driver) also hates suspend and I have to reset the BIOS. There are tons of "suspend/resume failure" bug reports on Launchpad. In fact, I don't think I ever got a system running Linux to successfully suspend.

It seems that this is more related to the Radeon. I had laptop with Radeon graphics card and it had problems with suspending laptop.
Later I replaced laptop (this time Intel/Nvidia graphics) and no more problems with suspend.

---

### Post by imwithid on 2015-10-30
Getting back to the essential question, is there anyone out there who can clarify whether this is a hardware issue (Intel and their UEFI BIOS) or is this a Linux issue (how the kernel handles power management / suspend)?

---

### Post by dalinian on 2016-01-16
**Hi Linuxistas,**

There are  at least fourteen threads in the Intel forums which address Intel's 'Linux  Suspend > Dead NUC' intermittent defect, dating back to August 2014. 

The  good news is that a workaround exists which means you can at least  avoid getting your NUC bricked by this defect, and it involves using  methods other than a short press on the Power button to wake a sleeping  NUC &#8211; ie: wake-on-USB and/or wake-on-LAN. 

For full details, see the '[COLOR=#008000]**Workaround Alert**[/COLOR]' above the my OP in the 'NUC5i5RYH Bricked by Ubuntu Suspend for Fifth Time' thread » [https://communities.intel.com/message/359708#359708](https://communities.intel.com/message/359708#359708)

---

### Post by tokyobadger on 2016-01-16
> **wolfv6 said:**
>  After I told Intel Support that "My NUC D54250WYK won’t boot", Intel Support told me, "We can't speak on the reliability of Linux distros in the NUC since we have only focused on Windows to this point, though we don't expect major issues on it."
I wonder what would happen if you told them you were running [Clear Linux](https://clearlinux.org/) ...

---

