---
title: "crush after second reboot on T20"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by enternet on 2006-08-25
Hi,
I reinstalled Ubuntu twice. It crushes after second reboot.
After installation (restart is required)I login succesfully. After second reboot - crush, after Saving VESA state - OK.

What to to do? What to check
Laptop: IBM Think Pad T20 750 MHz 256M Video card S3 (I guess:) )
It doesn't like something. But worked fine after installation.
I had Suse and CentOS on it before.

Please provide troubleshooting tips.

Thanks,
Michael.

---

### Post by Sef on 2006-08-25
Do you have any problem using a live cd?

---

### Post by enternet on 2006-08-25
Absolutely not.
It booted nicely. I clicked install. Restarted once. Worked first session. On second reboot crush...
BTW
I restarted couple of times now.
In safe mode:
It run up to:
root@ubuntu:~# 

saving VESA Ok
Starting system log  -

[146.990073]lo

Disabled Privacy Extentions 
[146.990559]  IPv6 over Ipv4 tunneling driver
[146.989713] NET: registered protocol family 10

What to do :) ?
I don't want to give up with Ubuntu.
Michael.

---

### Post by enternet on 2006-08-26
I have to add that after first reboot Mozilla was not "responding".
So I "turned off" IPv6 in Mozilla and it started to work.
May be my problem is a result of this.

---

### Post by enternet on 2006-08-28
Can somebody provide a help with initial question.

Thanks,
Michael.

---

### Post by GuruCesc on 2007-02-14
Hello,
  I had this very same problem (in a T20 700 Mhz, 512 RAM). This is what I did. It will hopefully help other member:

- Turn off ACPI and turned on APM:
Added "apm" at the bottom of /etc/modules

- Added acpi=off noacpi to the kernel line in /boot/grub/menu.lst

- Added 'Option "HWCursor" "false"' without the single quotes to the "Device" section of the /etc/X11/xorg.conf file

- Changed the color dept to 24 in the /etc/X11/xorg.conf file

  The T20 still won't completely turn off when I ask it to... but at least it turns on nicely every time. I'll let you all know if I have any further issues.

  I had to start in recovery mode after the second reboot and enter the "root" password for maintenance (so I could work in text mode). Then I just restarted and it worked nicely!

Regards,
GuruCesc

---

