---
title: "No luck... Gigabyte Z77X-UD5H"
date: 2013-05-07
forum: Hardware
---

### Post by tscastello on 2013-05-07
This issue concerns a Gigabyte Z77X-UD5H it's an 1155 socket
[http://www.gigabyte.us/products/product-page.aspx?pid=4139#ov](http://www.gigabyte.us/products/product-page.aspx?pid=4139#ov)
I have an i7 Sandybridge overclocked to 4.6GHz
32Gb RAM
Try as I might but luck isn't on my side.. I have tried 4 times so far to get Ubuntu to install but I'm not having an ounce of luck. First time I got the furthest all the way to getting it to boot up into Ubuntu and it went to do it's first restart and when it restarted it had a few lines of text all with [OK] by them and it ejected the CD and didn't do anything. I restarted and it booted right back into Windows. Not to mention that on the second try the drive decided after it ejected the CD and i pushed the tray back in the drive wouldn't respond, I had to open device manager uninstall the drive, pull the cover off the side, unplug the drive and plug it back in, it finally started working again. So finally I went into the BIOS and changed the boot priority and it was listed in this order:

1 - Windows Boot Manager
2 - My bluray player
3 - Samsung 830 SSD
4 - Samsung 830 SSD

Now common sense told me that ok move the CD rom into the 1st spot and move windows boot manager down one spot. So I did that and then right after BIOS booted it said "NO BOOT MANAGER FOUND Press Ctrl+Alt+Delete to reboot".

So the conclusion I am coming to is that this motherboard isn't compatible. If there are drivers that I need to install a head of time can someone point me in the right direction.

I'm so sick of Windows, I need this to work and I really don't want to have to purchase another motherboard so that it will work correctly.

Sorry if this has been posted somewhere else, I did a search but with all my frustration I'm sure I probably just missed it. Anyhow thank you in advance.

:::UPDATE:::  Okay so I gave it another shot because I have issues giving up. This time I changed the boot selection in the BIOS to what I seen was UEFI : CD Rom and that worked great booted right up into the CD and went through the whole installation like before and then after all was done it finished and wanted to restart so I clicked restart then black screen and all 3 of my monitors went black. Wouldn't reboot but system was still on it just hung basically with the CD Ejected so I pushed the CD back in and restarted manually.  After the restart it went to Windows boot loader and said something like this:

There was an issue with your load

1. Insert windows disk and restart
2. Choose Language click next
3. Repair your computer.

Info: The selected entry could not be loaded because the application is missing or corrupt
Ubuntu\winboot\wubildr.mbr

Status: 0xc0000098

---
I found a couple links does anyone know if they are accurate at all for windows 7. This person is having the same issue but windows 8.
[http://askubuntu.com/questions/239245/ubuntu-winboot-wubildr-mbr-error](http://askubuntu.com/questions/239245/ubuntu-winboot-wubildr-mbr-error)
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
------
Anyone make anything of this?

---

