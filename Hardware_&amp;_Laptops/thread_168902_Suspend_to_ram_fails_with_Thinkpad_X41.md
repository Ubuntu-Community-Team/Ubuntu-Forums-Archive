---
title: "Suspend to ram fails with Thinkpad X41"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by mikegr on 2006-05-01
Hello, Maybe someone can help me to debug this problem: 

I have a Thinkpad X41 model 2525 and I'm trying to get "suspend to ram" 
and "supsend to disk" to work with Ubuntu. I have updated my Kubuntu with 
dist-upgrade today (2006-05-01) from an installation with Flight 6. 

After some search about this topic I have added "resume=/dev/myswapdevice" to 
my kernel line in /boot/grub/menu.lst. Since that Suspend-To-Disk works. 

However there are some problems with Suspend-To-Ram:

I have already removed "splash" and "vga=0x318" from my kernel line and 
added "acpi_sleep=s3_bios". Unfortunately it hanged after 
executing /etc/acpi/sleep.sh. After a hint from thinkwiki.org I have changed 
in /etc/acpi/sleep.sh line

#echo -n $ACPI_SLEEP_MODE >/sys/power/state
to
echo -n 3 > /proc/acpi/sleep

Now it starts again, but every second resume I get a error message after resume. After this message my root partition is mounted read-only and any disk access fails.

[some numbers] ata1: disabling port
[some numbers] Assertion failed! ata_dev_present(master) 
ata_dev_presetn(slave), drivers/scsi/libdata-core.c, ata_get_mode_mask, 
line=2232
[some numbers] Buffer I/O errors on device sda7, log block 232....
and so on...

Sometimes I get this message,too:

/etc/acpi/sleep.sh
ERROR: Couldn't attach to DCOP server!
xscreensaver-command: no screensaver is running on display :0.0
xscreensaver-command: no screensaver is running on display :0.0
 * Shutting down ALSA...                                                            
[ ok ]
Calling INT 0x15 (F000:6543)
 EAX is 0x5F20
Error: something went wrong performing real mode call
ifup: interface eth0 already configured
 * Setting up ALSA...                                                               
[ ok ]
grep: /proc/acpi/fan/*/state: No such file or directory
xscreensaver-command: no screensaver is running on display :0.0
.

I have already applied the latest harddisk firmware update, but nothing has changed. 
I suppose it's mainly a problem with my SATA harddisk, but I think Dapper Drake should have included all patches for Serial ATA harddisk. Furthermore /var/log/acpid doesn't contain any more useful information than I have already written. 

Any ideas?

Thanks for any help.

Mike

---

### Post by anandrd on 2006-05-08
I am getting the same problem. I am running Dapper on Dell Inspiron 6000 with a SATA drive. Currently I am using 2.6.15-22-386 kernel. As Mike said, when I resume from suspend, my root partition is sometimes mounted as read only. All the disk accesses fail. My kernel arguments were root=/my/device1 swap=/my/device2 ro quiet. Suspend to disk works reliably.

---

