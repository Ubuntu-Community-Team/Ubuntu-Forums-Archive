---
title: "Suspend resumption issue"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by StewD on 2007-01-09
Hi

I have purchased a Intel Celeron D351 3.2 Ghz 775, to go with an Asrock 775i945GZ i945 socket 775.

I have installed Ubuntu 6.10 and am trying to make the "suspend" feature work so that the PC will largely shut down and use minimal power until I press a button on the keyboard (ideally USB, but I do have a PS/2 keyboard in at present as well) or another machine on my network attempts to access a file from the hard drive.

The motherboard offers Wake On Lan, so I assume this is possible. I will be following the advice in [http://ubuntuforums.org/showthread.php?t=234588&highlight=wol](http://ubuntuforums.org/showthread.php?t=234588&highlight=wol) but first am tring to get basic wake up working.

I have changed the ACPI BIOS setting as follows, without full understanding of what each function does, especially Ring-In:


Suspend to RAM	[Auto]
Repost Video on STR Resume	[Yes]

Restore on AC/Power Loss	[Power Off]
Ring-In Power On	[Enabled]
PCI Devices Power On	[Enabled]
PS/2 Keyboard Power On	[Enabled]
RTC Alarm Power On	[Disabled]
ACPI HPET Table		[Disabled]


I then successfully go into Ubuntu, select Suspend and the machine dutifully suspends itself , with the monitor being switched to a suspend state as well. Success?!

No....The USB keyboard is ignored, keys on the PS/2 are responded to with the HDD light and the DVD light coming on. The Monitor switches back on and presents me with the following error messages.

Please note I have had to type these on a different machine, so there may be the odd typo!! 

Most lines are also prefixed with [17179748.296000]


pnp: Failed to activate device 00:0c.S
Build Number: 1295 PC 14.12 02/17/2006
...2 other lines that flash up too quickly to read....

pnp: Failed to activate device 00:0c.s
ata1: failed to set xfermode (err_mask=0x4)
Buffer I/O error on device sda1, logical block 9511957
	last line repeated 10 times for different blocks

Anorting journal on device sda1
ext3_abort called
EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
Remounting filesystem read-only
Buffer I/O error on device sda1, logical block 3
Buffer I/O error on device sda1, logical block 9502720
 and repeated 5 more times
Hangs.


Any ideas what is going on, and how I can achieve Wake on keyboard and wake on network?

Many thanks,

Stewart

---

