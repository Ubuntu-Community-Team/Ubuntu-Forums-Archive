---
title: "Power savings won't stick?"
date: 2010-02-07
forum: Hardware
---

### Post by kaffemonster on 2010-02-07
Just purchased a new laptop, the HP Probook 5310m. With a P9300 cpu and 7200rpm drive, I can use Powertop to bring it down to 8-10w of power usage with bluetooth and wireless active. But to do that, I need to start Powertop at every boot, press S for sata power save etc. Where do I type in the suggestions Powertop gives me, to have them activated whenever the laptop is running on battery power?

The stuff I need to have run when on battery is:
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
usbcore.autosuspend=1

Another thing I've noticed is when I connect my usb 2 hard drive, a 320gig iOmega ego, power consumption almost doubles! Wonder if I should swap the internal drive for an ssd...

---

### Post by IcarusR on 2010-02-07
> echo min_power > /sys/class/scsi_host/host0/link_power_management_policy

In the above command 'echo' writes 'min_power' to the file /sys/class/scsi_host/host0/link_power_management_policy

On my box this file does not exist & going by its location in the command one would need to be sudo to run the command anyway.

> adding usbcore.autosuspend=1 to the kernel command line in the grub config

As it says above 'usbcore.autosuspend=1' has to be added as a kernel command line. Add to kernel line in /boot/grub/menu.lst (yes .lst).

Arguably if you do not understand what powertop is saying then you should not be doing those things.

> I connect my usb 2 hard drive, a 320gig iOmega ego, power consumption almost doubles!

Hardly surprising as any thing with motors in it will consume a lot of power. HDDs have numerous platters that spin at 5400 or 7200 rpm. They start & stop all using power.
Yes you could replace all HDDs with SSDs, but large good quality ones are very expensive & have a finite amount of writes before they fail.

To save power you are better off reading & doing some of the suggestions in these pages

[http://www.linuxjournal.com/article/7539]("http://www.linuxjournal.com/article/7539")

[http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption]("http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption")

[http://www.lesswatts.org/]("http://www.lesswatts.org/")

---

### Post by kaffemonster on 2010-02-07
Thanks for your reply :)

I'd love to maximise battery life when running on battery and slow down my drive - but not while on AC. And I do know how hard drives work (IT pro for 7 years and counting...) I'm sure theres a way to trigger a script when on battery, and another when plugged in. 

I know menu.lst, I've been running Ubuntu since '06, but in 9.10 it is no longer used, GRUB is enterily different, that is why I asked.

Lesswatts.org is the reason I wanted to save as much power as possible, so I'm here to learn. I work in IT, but as a systems administrator in a windows environment. I run Ubuntu at home, 'cause after a long day at work I want an OS that just WORKS without me having to worry. I am fully aware that I might very well screw everything up when tinkering with this stuff, but I absolutely love that Ubuntu (and OS software in general) lets me tinker if I want to.

Thanks again for your advice, I'll look into those other links you posted :)

---

### Post by kaffemonster on 2010-02-08
I buckled up and dived in for the challenge.

min_power is written to /sys/class/scsi_host/host0/link_power_management_policy but does nothing - PowerTop still suggests adding it to that file or pressing S. Dammit.

usbcore.autosuspend has been added to my kernel command line - I think. Looks like this:

```
menuentry "Ubuntu 9.10 64 Bit" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set cb9b18de-d69f-432f-8e9a-04573804e302
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=cb9b18de-d69f-432f-8e9a-04573804e302 ro   quiet splash 
	initrd	/boot/initrd.img-2.6.31-19-generic usbcore.autosuspend=1
	}
```

Alas, no change when running powertop again. 

Another thing: I know from reading the laptop-mode documentation that I can make stuff happen depending on whether or not the machine is running on battery power. Is there a way to have bluetooth disabled by default when booting on battery power, and enabled by default when booting on AC?

---

