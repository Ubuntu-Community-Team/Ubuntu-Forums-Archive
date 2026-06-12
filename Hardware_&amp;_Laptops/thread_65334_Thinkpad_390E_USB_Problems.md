---
title: "Thinkpad 390E USB Problems"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by conor on 2005-09-13
Hi guys,

I was hoping you could give me a hand whenever I plug in a usb device it will not mount and doesn't even seem to appear.  I am really a total noobie so I have no idea what comands to enter.  If you guys could help me out it would be awesome.  From other people with similar problems I've seen them enter this thinda stuff:

```
[4294672.355000] usbcore: registered new driver usbfs
[4294672.355000] usbcore: registered new driver hub
[4294672.362000] USB Universal Host Controller Interface driver v2.2
``` 

That is the only USB listed in dmesg.  

As I said I am on a Thinkpad 390E.

Thanks in advance.

---

### Post by conor on 2005-09-15
Anyone?

---

### Post by kkjoki on 2005-11-25
Hi. I have a similar problem with my 390e (my USB mouse doesn't work) and have narrowed it down to these errors: "uhci_hcd 0000:00:02.2: init 0000:00:02.2 fail, -16" and "uhci_hcd: probe of 0000:00:02.2 failed with error -16". I can also say that uhci_hcd module works on that machine with Debian Woody (and kernel-image-2.6) but Breezy has some problems with it... I've removed all PCMCIA cards from the laptop, upgraded the BIOS and tried to remove almost all other modules and reload "uhci_hcd" but nothing seems to work.

Does anyone have any suggestions? Or should I just go back to Debian and compile madwifi/wpasupplicant again... :(

PS. Breezy's wpasupplicant package doesn't seem to work so well with madwifi and DHCP. I had to install wpasupplicant (0.4.6-0ubuntu1) from dapper universe to get any IP-address with DHCP. Only static address worked with 0.4.5-0ubuntu1 version.

---

### Post by conor on 2005-11-25
My laptop died, 5topped working all together.  5trangely enough when I 5witched to a new one (5ame make and model, ju5t a different phy5ical computer) my u5b 5tarted working again.  The only problem i5 that the 'e55' button on the keyboard doe5n't work, a5 you may have been able to tell.

---

### Post by kkjoki on 2005-11-26
I just noticed this forum was for Hoary and I'm talking about Breezy, but anyway...

It took me a week but now the USB port works :) . "acpi=off" had to be added to kernel parameters. Debian Woody's kernel seems to disable ACPI automatically so I tried the same with Breezy and it worked.

---

### Post by BarryTice on 2006-12-05
I also have a 390E. I started with RedHat 8, and couldn't get the USB to work. I moved to RedHat 9 on it and somewhere found something (I don't remember what...) that let the USB work.

I later moved to Ubuntu (a good move, I might add...) Hoary Hedgehog, and lost my USB accessibility.

Two nights ago I replaced Hoary with Edgy Eft and on a whim I plugged my USB MP3 player in, and it recognized it and automounted it with no problem. (You may have to download the Alternate installer. I did, but I only have 128 MB.)

I never ran Badger, so I don't know how many of the improvements I'm seeing are newer than that. But if you upgrade to Edgy you may find (as I did) that the USB flash drive issue is now working for you.

Hope this helps.

-- BarryTice

---

