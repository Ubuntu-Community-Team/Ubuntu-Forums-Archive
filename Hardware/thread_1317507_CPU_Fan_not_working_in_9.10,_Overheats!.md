---
title: "CPU Fan not working in 9.10, Overheats!"
date: 2009-11-06
forum: Hardware
---

### Post by yaroto98 on 2009-11-06
I have an Acer Aspire 5315-2940

I've recently upgraded to 9.10.  However, the CPU fan doesn't spin up ever since I've upgraded from 9.04. Subsequently the CPU overheats and and the laptop shuts down.

What boggles my mind is that the cpu fan with the 9.10 live CD works perfectly. I took a look and when I 

cat /proc/acpi/thermal_zone/TZ01/cooling_mode

it says:

<setting not supported>

How to I get this working? Any Ideas?

---

### Post by ethos101 on 2009-11-08
I have the exact same problem.

Acer Aspire 5720z.

I might have found a fix:  [http://www.symbiosoft.net/?q=node/66](http://www.symbiosoft.net/?q=node/66)

The guy on that link has the exactt opposite problem (fan constantly spinning full-tilt rather than not at all) but when I applied his fix my fan seems to be spinning now, slowly.  I'm putting it through some paces now to see if it overheats.  I'll let you know if it crashes again.

In case the link disappears:
> 
So here is the recipe:

    * Open a terminal (Applications | Accessories | Terminal)
    * Type:

sudo nano /etc/default/grub

    * Find and Edit the following line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

    * Add acpi_osi=Linux to the end so it looks like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

    * Exit Nano editor with Ctrl+X.  Answer "yes" when asked to save the file
    * Update grub: 

sudo update-grub

    * Reboot to make changes effective


---

### Post by troyglover on 2009-11-09
Fan is also continuously running....

"sudo nano /etc/default/grub" yields no results in the nano display and searching using the navigation legend within nano provides nothing neither... any ideas?

-Troy-

---

### Post by ethos101 on 2009-11-10
> **troyglover said:**
> Fan is also continuously running....

"sudo nano /etc/default/grub" yields no results in the nano display and searching using the navigation legend within nano provides nothing neither... any ideas?

-Troy-

Are you sure you're using 9.10?  Sounds like you're not using GRUB 2.

For GRUB 1 try:
sudo nano /boot/grub/menu.lst

If you get your boot loader menu then just add "acpi_osi=Linux" on the same line right after "quiet splash"

---

### Post by yaroto98 on 2009-11-12
I tried this fix, and it didn't work for me. After doing a bit more troubleshooting i found out that the fan didn't spin up at all with the live cd. I was just hearing the cd spinning. I decided that if the live cd didn't work then that was that, and I reinstalled 9.04. I finally caved after not having a properly working laptop after a week.

---

### Post by ethos101 on 2009-11-14
It turns out it's not working for me either.  It was working at first.  I have no idea why.  My fan no longer spins at all and my computer is back to overheating and cutting off.  I checked and the acti line is still in the bootloader so it wasn't overwritten by an update.

I am stumped.  I have no choice but to either move back to 8.10 (9.04 has Intel video driver issues) or try the new openSUSE out.

---

### Post by superfresh_c on 2009-11-20
Has anyone found a solution. I am losing my mind with this. It seems somehow to overheat and shut down faster if I am using Firefox. I tried the fix here and it did not help. I am curious to find out how to get this working, so let me know. I will also try to solve it and let people know if I do. :]

c.

---

### Post by ethos101 on 2009-11-20
Yeah.  Windows 7.  :)  Sorry.  Maybe by the time I decide to come back to Linux (on my laptop) they will have sorted out the CPU fan issues.

---

### Post by quofan on 2009-11-21
> **superfresh_c said:**
> Has anyone found a solution. I am losing my mind with this. It seems somehow to overheat and shut down faster if I am using Firefox. I tried the fix here and it did not help. I am curious to find out how to get this working, so let me know. I will also try to solve it and let people know if I do. :]

c.

For what it's worth, my Aspire 7720 is having the same overheating problems in 9.10.   Tried the kernel patches as described but they had no effect for me.

Have returned to 9.04 for now and will watch for updates on this problem... which is about the extent of my ability to solve this unfortunately!

---

### Post by constable0802 on 2009-11-22
I have an Aspire 5315 and after the upgrade my CPU fan won't run if I boot to kernel 2.6.31-15 but it works fine if I boot to kernel 2.6.28-16. L am going nutz trying to figure it out. I am thinking of modifying the case with my sidearm. :evil:


 Quando Omni Flunkus Moritati.

---

### Post by Thomar on 2010-01-07
Edit: Wrong issue, see below post.

---

### Post by constable0802 on 2010-01-08
mine just shuts down after about 10 min. with no warning. It finely claimed my motherboard.

---

### Post by Thomar on 2010-01-08
For those of you using Aspires, do you use an external monitor?  I've found that keeping the laptop lid closed causes the CPU to spike to 100% due to a BIOS bug.  Installing the latest BIOS fixed the problem.

---

### Post by ethos101 on 2010-01-09
> **Thomar said:**
> For those of you using Aspires, do you use an external monitor?  I've found that keeping the laptop lid closed causes the CPU to spike to 100% due to a BIOS bug.  Installing the latest BIOS fixed the problem.

Nope.  I even keep the back edge lifted up for better airflow.  Ubuntu hasn't been stable on my Aspire 5720z since 8.10.  I went to win7 rather than go back to 8.10.  I sure wish this issue could be sorted out.  I've been waiting for a stable Ubuntu release ever since 9.04 AND 9.10 let me down.

---

### Post by maizuddin35 on 2010-01-09
hello.

my friend have the same problem too. his laptop is benq, processor 2.53 intel core 2 duo p8700
gpu 4650 ati radeon,ram 2 gigabyte..

when we install ubuntu, we can feel the fan does not working and the laptop is totally heating up. after installation, after 10 minutes time or more, the laptop suddenly shuts down.

any ideas?

---

### Post by derekmbarnes on 2010-01-09
A bug report has been filed for this issue:

[http://bugzilla.kernel.org/show_bug.cgi?id=14695](http://bugzilla.kernel.org/show_bug.cgi?id=14695)

Another user in a different thread said something about fan control being run through the graphics card.Can anyone confirm this?

---

### Post by joeganda on 2010-01-17
My problem with overheating the Aspire 5315 is gone after updating my bios from v1.29 to v 1.43. I kicked of Vista, but could update anyway with an iso described in msg 39 on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)
The fan runs every now and then, I hope it will be enough. Strangely it works, despite I turned off acpi in the boot and told grub to use the acpi of Linux.

---

### Post by Wilf999 on 2010-06-22
I had this problem with an Acer Aspire 7720 running 10.04, ethos101's fix worked.  Second time.  Forgot to type in the update-grub line first time.

Thanks man!

Wilf

Correction, it now *sometimes* works.  If I start it up hot (usually from Vista) the fan keeps running, never works from cold.

---

