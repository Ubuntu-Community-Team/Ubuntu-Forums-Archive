---
title: "ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by cccc on 2007-12-02
hi

I have gutsy installed.
knows someone howto solve this problem ?
```

ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
```

---

### Post by tgalati4 on 2007-12-03
Here's a weak answer:

I'm troubleshooting my suspend-to-ram and I have the same error.  Some searching shows that it is related to laptop-screen dimming during sleep/battery operation.

---

### Post by cccc on 2007-12-03
> **tgalati4 said:**
> Here's a weak answer:

I'm troubleshooting my suspend-to-ram and I have the same error.  Some searching shows that it is related to laptop-screen dimming during sleep/battery operation.

thanks, but I'm using a normal desktop computer.

---

### Post by sylecn on 2007-12-04
I have this error in my /var/log/kern.log.
I'm using thinkpad x41t.

I just want to know if it is harmful.
Battery is working without problem.

---

### Post by 3ntity on 2007-12-08
have this same 'issue' under Gutsy... /DSDT.aml not found when i type `dmesg | grep /DSDT.aml`. Ubuntu wasn't booting, after about the 10th reboot it finally did... Hope i don't get the same again :S

Forgot to mention: desktop PC

---

### Post by swejuggalo on 2007-12-13
Same problem here. Desktop, i815 based motherboard. The strange thing is that when I use kernel 2.6.20-16 (from before the upgrade from ubuntu 7.04) ACPI works!!

So to be able to boot 2.6.22 I have to use the boot option acpi=off . But that isn't a very fun thing to do...

---

### Post by theBatman on 2007-12-17
> **swejuggalo said:**
> Same problem here. Desktop, i815 based motherboard. The strange thing is that when I use kernel 2.6.20-16 (from before the upgrade from ubuntu 7.04) ACPI works!!

So to be able to boot 2.6.22 I have to use the boot option acpi=off . But that isn't a very fun thing to do...

How do I do this? I can't get into Ubuntu AT ALL. How would I turn this off?:confused:

---

### Post by swejuggalo on 2007-12-22
> **theBatman said:**
> How do I do this? I can't get into Ubuntu AT ALL. How would I turn this off?:confused:


When you get to the boot options press E on the kernel you wish to use. On the second row (if I remember it right) press E again. You should now see "quiet splash"... Replace everything with acpi=off. Boot by B or something. Should be described what to press there...
This is only tempoary. Will be lost the next boot. Will post the permanent solution when found...

......

in a terminal, sudo gedit /boot/grub/menu.lst , You should now replace as before... Replace "quiet splash" with "acpi=off". Save and the setting is permanent.

example:

title       Ubuntu 7.10, kernel 2.6.22-14-generic
root      (hd0,0)
kernel  /vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root ro **quiet splash**
initrd    /initrd.img-2.6.33-14-generic
quiet

---

### Post by lyager on 2008-01-20
I'm seeing the same thing. Running on a P5K SE Asus motherboard, but Gutsy is booting ok without ACPI=off, however, when hitting suspend the Desktop machine just locks up, without suspending anything.

Any help?

---

### Post by gjhicks on 2008-02-17
Hi,

Am having exactly the same problem.

Am using a USB stick install of Xubuntu 7.10 (gutsy) that works fine on several machines.

But on a Gigabyte GA-8SG800P get the error and boot process hangs up.

Have tried the replacement of "quiet splah" with "acpi=off" suggested above, have tried keeping the "quiet splash" and adding "acpi=off".  Have also tried "noacpi" on the kernel command line, in various combinations.

Always booting hangs up with the same error.

Any suggestions gratefully received.

---

### Post by happyhamster on 2008-02-18
The 'DSDT.aml not found' message isn't necessarily a sign of something bad. See:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/58386](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/58386)

---

### Post by gjhicks on 2008-02-18
That may be the case for some users but, using a USB stick persistent installation of Xubuntu 7.10, that boots fine on several other PCs, hangs up during booting, with the above message, on one particular PC.

So, still looking for a solution, without having to re-build the kernel.

---

### Post by sgtkazz on 2008-05-29
Does anyone know if this was ever addressed. I am having this exact problem in 8.04. My machine will not suspend, hibernate, or even shutdown properly. 

Any help would be very appreciated.

---

### Post by mazamazine on 2008-05-29
> **sgtkazz said:**
> Does anyone know if this was ever addressed. I am having this exact problem in 8.04. My machine will not suspend, hibernate, or even shutdown properly. 

Same thing for me... And sometimes it doesn't boot at all, it seems that there's a link to initrd ?

---

### Post by mazamazine on 2008-05-29
It seems to have no importance. I quote Chili555 from an other discussion :
> **chili555 said:**
>  Re: ethernet module e100 wont completely blacklist inhibiting eepro100 loading
Quote:
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found
I this, too. Please see: [https://bugs.launchpad.net/ubuntu/+s....22/+bug/58386](https://bugs.launchpad.net/ubuntu/+s....22/+bug/58386) especially this:
Quote:
The purpose of this optional kernel feature, enabled by "CONFIG_ACPI_CUSTOM_DSDT_INITRD=y" in the kernel .config at build-time, is to allow the user to replace the BIOS Advanced Configuration & Power Interface (ACPI) Differentiated System Description Table (DSDT) with one that has been modified to solve problems in the BIOS shipped by manufacturers.

The message you see is correct. As far as the kernel is concerned it is an error because it is told to expect to find a replacement DSDT.aml and it isn't there. However the message could be altered somewhat to make it sound less harsh.
It doesn't seem like anything either of us should worry about.

---

### Post by sgtkazz on 2008-06-04
Has anyone found any information on this issue elsewhere they could share? I am still unable to shutdown properly, and if the system is suspended it will not wake back up. I am about to take the distro off.

---

### Post by gjhicks on 2008-06-05
Despite the two messages above saying that the error is not important, the fact is that, on some machines, this error occurs and those machines just won't boot.

I gave up on the persistent USB boot for the machine that gave this error and did a regular hard disk install from a live CD.  The problematic machine works fine.

Reckon it was something to do with the USB booting but have no idea what the actual cause of the problem.

---

### Post by mogwai on 2008-06-10
Found a fix that worked for me.

1. Starting at the GRUB menu, highlight your recovery mode kernel (eg:
Ubuntu 8.04 kernel 2.6.24-17-generic (recovery mode) 

2. Press 'e' to edit the kernel parameters.
3. Highlight the second line (the one starting with 'kernel').
4. Press 'e' again.
5. Press END to ensure you are at the end of the line.
6. Put a space then 'acpi=off'  (without the quotes of course).
7. Press ENTER, and you should find yourself back at the kernel line, the same one as step 3.
8. Press 'b' to boot with these parameters.
   Patience is key here. It may seem to stall, and a couple of error messages will display.
   You should get to a 'Recovery Menu'.
9. Select 'root - drop to root shell prompt'.
10. Type in:
sudo dpkg-reconfigure linux-image-$(uname -r)

and press ENTER.
It will show a whole lot of gobbly-gook; this is just the dpkg-reconfigure command reconfiguring your kernel.
11. When this is done, type:
reboot
  or
shutdown -r now

Boot as normal. Should have fixed the showstopping '/DSDT.aml not found' bug.

Hope this helps.

Mogwai

btw, am using Ubuntu 8.04 2.6.24-17-generic on a ThinkPad R61 (T7250, Intel GMA965 X3100)

Link to bug report from where I got the information:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/58386](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/58386)

---

### Post by zakoota on 2008-07-04
> **swejuggalo said:**
> When you get to the boot options press E on the kernel you wish to use. On the second row (if I remember it right) press E again. You should now see "quiet splash"... Replace everything with acpi=off. Boot by B or something. Should be described what to press there...
This is only tempoary. Will be lost the next boot. Will post the permanent solution when found...

......

in a terminal, sudo gedit /boot/grub/menu.lst , You should now replace as before... Replace "quiet splash" with "acpi=off". Save and the setting is permanent.

example:

title       Ubuntu 7.10, kernel 2.6.22-14-generic
root      (hd0,0)
kernel  /vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root ro **quiet splash**
initrd    /initrd.img-2.6.33-14-generic
quiet
hi,
i had the same problem, and was able to boot with the temporary solution.
However, when trying the permanent solution, the message is 
"sudo: gedit/boot/grub/menu.lst: command not found"

Can you help pls,

Regards,

ZAKOOTA

---

### Post by zolero on 2008-07-04
Your command line was misspelled **Zakoota**.

It must be:
```
sudo gedit /boot/grub/menu.lst
```
(gedit is the command, and /boot/... tralala... is the argument **separated by space**). ;)

---

