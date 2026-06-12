---
title: "Toshiba Satellite WiFi/USB/ACPI conflicts"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by cookevillain on 2007-06-04
Hi everybody!

I have just installed 7.04 on Satellite A45-S121. Everything works great except that the only way I can get both WiFi and USB to work is to add acpi=off to the kernel line in /boot/grub/menu.lst . At first wireless would simply freeze the machine (just the mere fact of sticking it in the PCMCIA slot) to the point that it dropped any landline connection and stopped responding to the mouse and keyboard input. Then I wrote a little script to activate it manually and it started working (I am using Motorola WN825GP with bcm43xx drivers). I then discovered that I cannot mount any USB flashdrives (dmesg complains about `bad cable' but that of course is bs). After looking at [this bug report]("http://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/83984") I tried `acpi=off' and everything started working ... except, of course, the machine does not poweroff. Interesting enough, nm-applet (the Network Manager) does not freeze the machine anymore, so I do not have to run my wifi script.  Does anyone have any idea whether this bug is being worked on?

Thanks for any info

Alex

PS I could not get ndiswrapper to work at all (not that I want to anymore, now that I found bcm43xx drivers), however, it worked flawlessly in Puppy Linux 2.13, as well as USB drives AND acpi.

PPS I have disabled 'Legacy keyboard support' in BIOS and re-enabled acpi. Everything seems to work (I can mount/unmound usb flashdrives and my wireless card works). However, I still get

bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR

in dmesg. The link is not affected but it looks a bit scary. I would still appreciate if someone can point me to a 'cleaner' fix.

---

