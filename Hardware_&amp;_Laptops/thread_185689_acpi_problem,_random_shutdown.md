---
title: "acpi problem, random shutdown"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by barna on 2006-06-01
Hi
My Toshiba Satellite A60 keeps shutting down randomly. The /var/log/messages indicates to me that this might be a problem with acpi:

May 29 11:35:31 localhost kernel: [4301918.411000] ACPI-0284: *** Error: Thread 1B91 cannot release Mutex [MUT1] acquired by thread 1A9F
May 29 11:35:31 localhost kernel: [4301918.411000] ACPI-0508: *** Error: Method execution failed [\_SB_.RDEC] (Node dbfd6540), AE_AML_NOT_OWNER
May 29 11:35:31 localhost kernel: [4301918.411000] ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node dbfda460), AE_AML_NOT_OWNER
May 29 11:35:31 localhost shutdown[9459]: shutting down for system halt

I have got ubuntu 5.10, and both 2.6.12-9 and 2.6.12-10 kernels produced the same crash.
Is this a known problem, and does anybody know how to overcome it (without disabling acpi)?

(recently I have tried the system with the following options: acpi=off noapic nosmp, and it has been running for more than a day without crash. Previously it crashed about every 2 hours)

Originally I wanted to have the possibility to hibernate my laptop. After a long time of unsuccess I gave up, and was happy to have at least acpi (power button switches off the computer, and the ability of shutting down the laptop automatically if the battery runs out). Now I would even be happy to have a computer which does not shut down randomly, even if the price of it is to have no acpi. But disabling acpi resulted in losing the (usb)mouse for some reason (so I have now only the touchpad)
If a non-crashing acpi is beyond the horizont of reality, can anyone tell, how to have the mouse back at least with acpi=off?

thanks
Daniel

---

### Post by phitoo on 2006-06-02
I am having the same sort of problem with a Toshiba Tecra A4-S313. I am currently using Kubuntu Dapper, upgraded as of 31 May. It's been a problem since I first installed Dapper Flight 2. By now I've learned to set acpi=off on the kernel line in Grub.

Two things I've noticed:

- everything is fine when running on battery. Random shutdowns happen only when the laptop is plugged into AC.

- the klaptop power/battery indicator is somewhat unstable and will sometimes show the battery power icon even when on AC.

So the problem may with klaptop or with ACPI or it may just be a fluke with this particular machine.

---

### Post by isitututu on 2006-06-23
I have an A60 and had the same problem first with Linspire 4.5 then 5.0 also found that it was an acpi problem. I switch back to my old fav Mandrake and had the same problem. I have been running Ubuntu for the last six months without problems, but since installing the new kernel updates this issue is back again. ](*,) Anyone have any suggestions besides disabling acpi?

---

### Post by stafusa on 2006-06-25
[QUOTE=isitututu]I have an A60 and had the same problem first with Linspire 4.5 then 5.0 also found that it was an acpi problem. I switch back to my old fav Mandrake and had the same problem. I have been running Ubuntu for the last six months without problems, but since installing the new kernel updates this issue is back again. ](*,) Anyone have any suggestions besides disabling acpi?[/QUOTE]

I am also facing the same problem. I am not really sure, but although I have had lots of problems with acpi (as messing the graphic interface and entering randomly in standby mode) I think that shutdown thing was not happening before I made the upgrade from kernel 2.6.15-23-386 to 2.6.15-25-386.
By the way, the problem of random standby and graphical interface I could "solve" only by disabling all the acpi features but the performance profile :(  But my /var/log/messages is still flooded by error messages of that Mutex thing.
There is no doubt that the klaptop power/battery indicator is unstable, but for me its right most of the time.
I wonder if it is not be a problem with Toshiba, since I own one too - Satellite M45-359...

---

### Post by cus on 2006-06-27
I've got a Toshiba Satellite M40-200 and am getting an issue where it'll hibernate at seemingly random intervals. It hibernates fine so I don't lose any work but it can be a pain.

My laptop was OK through the Dapper test cycles. It seems to only have started happening since I reformatted my drive and installed the formal release.

If I've got time I'll try and do a kernel build from 2.6.17 and see whether it fixes the problem.

---

### Post by cus on 2006-06-27
I can confirm that 2.6.17.1 doesn't appear to exhibit the problem. 2.5 hours of uptime with amarok running and not a single spontaneous hibernate or shutdown.

I downloaded the source from kernel.org, performed a 'make oldconfig', taking the defaults for the new settings.

I then made the package through:
make-kpkg --initrd kernel_image

...and installed it. Painless and (so far) more stable.

---

### Post by isitututu on 2006-07-05
Can we get detailed instructions please?

---

### Post by barna on 2006-07-06
For some reason I started several threads about this problem (probably because I was quite upset, not being to work)
I found that these random shutdowns were due to sleepd, but posted this discovery to another thread only:
[http://ubuntuforums.org/showthread.php?t=185689](http://ubuntuforums.org/showthread.php?t=185689)

---

