---
title: "Trouble-free SanDisk?"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by tgbrowning on 2007-06-29
Read quite a bit so far on how to get a SanDisk to mount and the question occurs to me:  Is there anybody out there who had a flawless mount of one, from the first?  No messing around with the mount command or fstab.  

Correct me if I'm wrong, but such memory cards are designed, supposedly, to be recognized and not messed with -- in theory. In Windows, over the last couple of years, I never had to mess around with them at all.

Why is that not the case with Ubuntu? 

I have USB drives that work fine and there's no fstab entry at all. 

When I plug it in, the system recognizes it and when I run mount -l, there's a nice long entry for the USB drive, detailing the characteristics of that particular drive. 

Where does all that come from? How does the system come up with it? 

It strikes me that SanDisk cards ought to be operating in the same way, but they aren't.  

Can anybody give me a little of the theory here?

Browning>>>

---

### Post by jespdj on 2007-06-29
What do you mean with "a SanDisk"? SanDisk is a company that makes different products. Do you mean a SanDisk card reader, a CF or SD or other format memory card or a SanDisk MP3 player?

Assuming that you mean a memory card: How do you know that the card is the problem, and not the card reader? Do you have other brand memory cards that work well in the same card reader? Did you try a different card reader? Did you try plugging your card reader into a different USB connector?

My SanDisk MP3 player and Ultra II / Extreme III CF cards (I have several, 512 MB to 4 GB cards) all work without any problem on Ubuntu 7.04 / 64-bit.

---

### Post by tgbrowning on 2007-06-29
> **jespdj said:**
> What do you mean with "a SanDisk"? SanDisk is a company that makes different products. Do you mean a SanDisk card reader, a CF or SD or other format memory card or a SanDisk MP3 player?

Sorry, I get kind of focused. I'm refering to the SD, specifically in all of it's different sizes (from a 16 meg card up to a 2 gig one).

> 
How do you know that the card is the problem, and not the card reader?

Actually, I know there's nothing wrong with the cards at all. As for the reader, I know the reader is fine because the same built-in reader works with Windows XP, just like all of different cards. I'm running a Compaq V2000 with a dual Dapper/XP configuration. Also, an external reader has been tried, same response exactly.

And to forstall further questions about the cards themselves, I bought the cards from Circuit City and I'm reasonably certain that all of them are authentic and not fake like some of the ones I've heard of on eBay.
> My SanDisk MP3 player and Ultra II / Extreme III CF cards (I have several, 512 MB to 4 GB cards) all work without any problem on Ubuntu 7.04 / 64-bit.

Tha's what the sort of thing I've been wondering about. Are there entries in your /etc/fstab for the reader you're using? If so, could you put a copy of your fstab up so I could have a look at it. This has kind of ceased to be a regular fix-the-problem kind of question with me. I'm curious as heck about what is causing this. I'd like to figure it out.

Browning>>>

---

### Post by az on 2007-06-29
> **tgbrowning said:**
> 
Tha's what the sort of thing I've been wondering about. Are there entries in your /etc/fstab for the reader you're using? If so, could you put a copy of your fstab up so I could have a look at it. This has kind of ceased to be a regular fix-the-problem kind of question with me. I'm curious as heck about what is causing this. I'd like to figure it out.


Fstab is for static mount points.  Hotpluggable devices get automounted by HAL and Udev.

If this is not happening, it's either a hardware issue or a bug.

Boot your computer into Ubuntu and run

tail -f /var/log/messages

and then plug in the device for the first time (since booting).  Post the output.  That will display what the kernel sees when you plug in the device.

---

### Post by tgbrowning on 2007-06-29
Ahh, that's what I was looking for. I'll take a look and get back to you.

Browning>>>

---

### Post by hardyn on 2007-06-29
Sandisk has reciently been putting a windows based compression utility on the new ones, which makes them a pain in windows, and an even bigger one in linux; there is a format utlity on the sandisk website; the utlity must be used, a normal format/partition does not work

---

### Post by tgbrowning on 2007-06-29
Okay, there definitely is something not kosher.

Here's what I get BEFORE I instert the card: No errors noted and everything looks fine.

Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readwrite:/home/browning/.gconf" to a writable configuration source at position 1
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 29 09:45:50 localhost kernel: [17179624.664000] NET: Registered protocol family 10
Jun 29 09:45:50 localhost kernel: [17179624.664000] lo: Disabled Privacy Extensions
Jun 29 09:45:50 localhost kernel: [17179624.664000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 29 09:45:50 localhost kernel: [17179624.664000] IPv6 over IPv4 tunneling driver
Jun 29 09:45:54 localhost gconfd (browning-4999): Resolved address "xml:readwrite:/home/browning/.gconf" to a writable configuration source at position 0

Now, here's what I get (edited down because of all of the errors:


bash: syntax error near unexpected token `('
browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ Jun 29 09:45:50 localhost kernel: [17179624.664000] NET: Registered protocol family 10
bash: Jun: command not found


Where do I look to get rid of that pesky "(" token that seems to be gumming up the works.

Browning>>>

---

### Post by tgbrowning on 2007-06-29
Don't think that's the problem for a couple of reasons, one being that I decided that stuff might be clearer if I made sure I had a clean card so I reformeted it. Anything that was on the card, put there by the SanDisk is gone, gone, gone.

---

### Post by hardyn on 2007-06-29
how did you reformat it?

how new is it? goes it say something like "sandisk g2" or some other flashy name, pardon the pun.

---

### Post by az on 2007-06-29
> **tgbrowning said:**
> Okay, there definitely is something not kosher.

Here's what I get BEFORE I instert the card: No errors noted and everything looks fine.

Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readwrite:/home/browning/.gconf" to a writable configuration source at position 1
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 29 09:45:50 localhost kernel: [17179624.664000] NET: Registered protocol family 10
Jun 29 09:45:50 localhost kernel: [17179624.664000] lo: Disabled Privacy Extensions
Jun 29 09:45:50 localhost kernel: [17179624.664000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 29 09:45:50 localhost kernel: [17179624.664000] IPv6 over IPv4 tunneling driver
Jun 29 09:45:54 localhost gconfd (browning-4999): Resolved address "xml:readwrite:/home/browning/.gconf" to a writable configuration source at position 0

Now, here's what I get (edited down because of all of the errors:


bash: syntax error near unexpected token `('
browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ Jun 29 09:45:50 localhost kernel: [17179624.664000] NET: Registered protocol family 10
bash: Jun: command not found


Where do I look to get rid of that pesky "(" token that seems to be gumming up the works.

Browning>>>

Unless you only posted a small portion of the messages, there is no indication that the kernel sees your device.  It's like you didn't plug it in at all.

---

### Post by tgbrowning on 2007-06-29
with the camera and under Windows XP. Then took some pictures. pictures were fine and the camera had no problem with the card. Did NOT use the QuickFormat option under XP.

Browning>>>

---

### Post by tgbrowning on 2007-06-29
I edited down the results hopeing to save space. 

Here's the unedited results, which contain what I had before the card was inserted, directly after the boot, what it looked like after I inserted the card (16 M) and then what happened after I removed the 16 M card and put in a 2 G card.

******************

browning@browning-laptop:~$
browning@browning-laptop:~$ tail -f /var/log/messages
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readwrite:/home/browning/.gconf" to a writable configuration source at position 1
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 29 09:45:50 localhost kernel: [17179624.664000] NET: Registered protocol family 10
Jun 29 09:45:50 localhost kernel: [17179624.664000] lo: Disabled Privacy Extensions
Jun 29 09:45:50 localhost kernel: [17179624.664000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 29 09:45:50 localhost kernel: [17179624.664000] IPv6 over IPv4 tunneling driver
Jun 29 09:45:54 localhost gconfd (browning-4999): Resolved address "xml:readwrite:/home/browning/.gconf" to a writable configuration source at position 0
Jun 29 09:49:14 localhost kernel: [17179827.812000] mmcblk0: mmc2:0001 16M    15680KiB <NULL>
Jun 29 09:49:14 localhost kernel: [17179827.812000]  mmcblk0: p1





exit

[1]+  Stopped                 tail -f /var/log/messages
browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readwrite:/home/browning/.gconf" to a writable configuration source at position 1
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ Jun 29 09:45:50 localhost kernel: [17179624.664000] NET: Registered protocol family 10
bash: Jun: command not found
browning@browning-laptop:~$ Jun 29 09:45:50 localhost kernel: [17179624.664000] lo: Disabled Privacy Extensions
bash: Jun: command not found
browning@browning-laptop:~$ Jun 29 09:45:50 localhost kernel: [17179624.664000] ADDRCONF(NETDEV_UP): eth0: link is not ready
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ Jun 29 09:45:50 localhost kernel: [17179624.664000] IPv6 over IPv4 tunneling driver
bash: Jun: command not found
browning@browning-laptop:~$ Jun 29 09:45:54 localhost gconfd (browning-4999): Resolved address "xml:readwrite:/home/browning/.gconf" to a writable configuration source at position 0
bash: syntax error near unexpected token `('
browning@browning-laptop:~$
browning@browning-laptop:~$
browning@browning-laptop:~$
browning@browning-laptop:~$ [1]+  Stopped                 tail -f /var/log/messages
bash: [1]+: command not found
browning@browning-laptop:~$ browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ bash: syntax error near unexpected token `('
> browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readwrite:/home/browning/.gconf" to a writable configuration source at position 1
> bash: syntax error near unexpected token `('
> browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
> bash: syntax error near unexpected token `('
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ bash: syntax error near unexpected token `('
> browning@browning-laptop:~$ Jun 29 09:45:48 localhost gconfd (browning-4999): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
> bash: syntax error near unexpected token `('
> browning@browning-laptop:~$ Jun 29 09:45:50 localhost kernel: [17179624.664000] NET: Registered protocol family 10
> bash: Jun: command not found
> browning@browning-laptop:~$ Jun 29 09:45:50 localhost kernel: [17179624.664000] lo: Disabled Privacy Extensions
> bash: Jun: command not found
> browning@browning-laptop:~$ Jun 29 09:45:50 localhost kernel: [17179624.664000] ADDRCONF(NETDEV_UP): eth0: link is not ready
> bash: syntax error near unexpected token `('
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ browning@browning-laptop:~$ Jun 29 09:45:50 localhost kernel: [17179624.664000] IPv6 over IPv4 tunneling driver
bash: browning@browning-laptop:~$: command not found
browning@browning-laptop:~$ bash: Jun: command not found
bash: bash:: command not found
browning@browning-laptop:~$ browning@browning-laptop:~$ Jun 29 09:45:54 localhost gconfd (browning-4999): Resolved address "xml:readwrite:/home/browning/.gconf" to a writable configuration source at position 0
bash: syntax error near unexpected token `('
browning@browning-laptop:~$ bash: syntax error near unexpected token `('
> browning@browning-laptop:~$
> browning@browning-laptop:~$
> browning@browning-laptop:~$
>
> Jun 29 09:45:50 localhost kernel: [17179624.664000] lo: Disabled Privacy Extensions

---

### Post by tgbrowning on 2007-06-29
Finally, here's what I get with repeatedly inserting and removing the card. You can see that the card is recognized, but there's no notification that the card has been mounted and is capable of being either read or written to.

************************

browning@browning-laptop:~$ tail -f /var/log/messages
Jun 29 10:17:27 localhost kernel: [17179626.108000] lo: Disabled Privacy Extensi ons
Jun 29 10:17:27 localhost kernel: [17179626.108000] ADDRCONF(NETDEV_UP): eth0: l ink is not ready
Jun 29 10:17:27 localhost kernel: [17179626.108000] IPv6 over IPv4 tunneling dri ver
Jun 29 10:17:31 localhost gconfd (browning-5024): Resolved address "xml:readwrit e:/home/browning/.gconf" to a writable configuration source at position 0
Jun 29 10:18:18 localhost kernel: [17179676.324000] usb 3-1: new high speed USB device using ehci_hcd and address 2
Jun 29 10:18:18 localhost kernel: [17179676.612000] Initializing USB Mass Storag e driver...
Jun 29 10:18:18 localhost kernel: [17179676.612000] scsi0 : SCSI emulation for U SB Mass Storage devices
Jun 29 10:18:18 localhost kernel: [17179676.616000] usbcore: registered new driv er usb-storage
Jun 29 10:18:18 localhost kernel: [17179676.616000] USB Mass Storage support reg istered.
Jun 29 10:18:20 localhost kernel: [17179678.856000] usb 3-1: USB disconnect, add ress 2

Jun 29 10:20:27 localhost kernel: [17179805.516000] mmcblk0: mmc2:e624 SD02G 198 5024KiB <NULL>
Jun 29 10:21:53 localhost kernel: [17179891.996000] mmcblk0: mmc2:0001 16M    15680KiB <NULL>
Jun 29 10:21:53 localhost kernel: [17179892.116000] printk: 83 messages suppressed.
Jun 29 10:22:31 localhost kernel: [17179929.864000] mmcblk0: mmc2:e624 SD02G 1985024KiB <NULL>
Jun 29 10:22:31 localhost kernel: [17179929.984000] printk: 83 messages suppressed.
Jun 29 10:23:40 localhost kernel: [17179998.556000] usb 3-1: new high speed USB device using ehci_hcd and address 3
Jun 29 10:23:40 localhost kernel: [17179998.688000] scsi1 : SCSI emulation for USB Mass Storage devices
Jun 29 10:23:45 localhost kernel: [17180003.688000]   Vendor: LEXAR     Model: JD FIREFLY        Rev: 3000
Jun 29 10:23:45 localhost kernel: [17180003.688000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jun 29 10:23:45 localhost kernel: [17180003.852000] Driver 'sd' needs updating - please use bus_type methods
Jun 29 10:23:45 localhost kernel: [17180003.856000] SCSI device sda: 7928832 512-byte hdwr sectors (4060 MB)
Jun 29 10:23:45 localhost kernel: [17180003.856000] sda: Write Protect is off
Jun 29 10:23:45 localhost kernel: [17180003.864000] SCSI device sda: 7928832 512-byte hdwr sectors (4060 MB)
Jun 29 10:23:45 localhost kernel: [17180003.864000] sda: Write Protect is off
Jun 29 10:23:45 localhost kernel: [17180003.864000]  sda: sda1
Jun 29 10:23:45 localhost kernel: [17180003.972000] sd 1:0:0:0: Attached scsi removable disk sda
Jun 29 10:23:45 localhost kernel: [17180003.992000] sd 1:0:0:0: Attached scsi generic sg0 type 0

exit


[1]+  Stopped                 tail -f /var/log/messages
browning@browning-laptop:~$ tail -f /var/log/messages

---

### Post by az on 2007-06-29
> **tgbrowning said:**
> Finally, here's what I get with repeatedly inserting and removing the card. You can see that the card is recognized, but there's no notification that the card has been mounted and is capable of being either read or written to.



Jun 29 10:20:27 localhost kernel: [17179805.516000] mmcblk0: mmc2:e624 SD02G 198 5024KiB <NULL>
Jun 29 10:21:53 localhost kernel: [17179891.996000] mmcblk0: mmc2:0001 16M    15680KiB <NULL>
Jun 29 10:21:53 localhost kernel: [17179892.116000] printk: 83 messages suppressed.
Jun 29 10:22:31 localhost kernel: [17179929.864000] mmcblk0: mmc2:e624 SD02G 1985024KiB <NULL>
Jun 29 10:22:31 localhost kernel: [17179929.984000] printk: 83 messages suppressed.

OK.  It's a bug:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/53923](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/53923)

---

### Post by tgbrowning on 2007-06-29
Which means, what? That there is, as yet, no work around? 

Browning>>>

---

### Post by tgbrowning on 2007-06-29
WHEW!

Wend through the bug thread (all umptine entries) and confess myself completely flummoxed.

I have no idea what can or should be done, unless it means finding a external cardreader that is not a Texas Intruments card reader. Anybody know which card readers are NOT Texas Instruments?

Browning>>>

---

### Post by stchman on 2007-06-29
> **tgbrowning said:**
> Read quite a bit so far on how to get a SanDisk to mount and the question occurs to me:  Is there anybody out there who had a flawless mount of one, from the first?  No messing around with the mount command or fstab.  

Correct me if I'm wrong, but such memory cards are designed, supposedly, to be recognized and not messed with -- in theory. In Windows, over the last couple of years, I never had to mess around with them at all.

Why is that not the case with Ubuntu? 

I have USB drives that work fine and there's no fstab entry at all. 

When I plug it in, the system recognizes it and when I run mount -l, there's a nice long entry for the USB drive, detailing the characteristics of that particular drive. 

Where does all that come from? How does the system come up with it? 

It strikes me that SanDisk cards ought to be operating in the same way, but they aren't.  

Can anybody give me a little of the theory here?

Browning>>>

My girlfriend has a SanDisk e250 that I plug right into my laptop.  It brings up Rythmbox and a desktop icon so I can drag and drop .mp3 files onto it.  No problem.

I had to change the USB to MSC and everything worked fine.  The MSC mode make it act like a removable hard drive allowing drag and drop.  Drag and drop is good.

---

### Post by tgbrowning on 2007-06-29
For more clarification, try this link. Apparently, there is no support for texas instrument card readers under the Dapper distro. 

Browning>>>

---

### Post by tgbrowning on 2007-06-29
Whoops:   

HEre's the link.

[http://ubuntulinuxtipstricks.blogspot.com/2007/04/texas-instruments-sdmmc-card-reader.html](http://ubuntulinuxtipstricks.blogspot.com/2007/04/texas-instruments-sdmmc-card-reader.html)

---

### Post by tgbrowning on 2007-06-29
Well, I shelled out some cash to see if I could locate an external card reader that might not have the problems that my built in one did, as well as the other external one which was also a SanDisk product.

Here's the results from plugging it :

browning@browning-laptop:~$ tail -f /var/log/messages
Jun 29 16:26:45 localhost kernel: [17187965.896000]   Type:   Direct-Access                  ANSI SCSI revision: 00
Jun 29 16:26:45 localhost kernel: [17187966.288000] SCSI device sda: 1984000 512-byte hdwr sectors (1016 MB)
Jun 29 16:26:45 localhost kernel: [17187966.292000] sda: Write Protect is off
Jun 29 16:26:45 localhost kernel: [17187966.296000] SCSI device sda: 1984000 512-byte hdwr sectors (1016 MB)
Jun 29 16:26:45 localhost kernel: [17187966.296000] sda: Write Protect is off
Jun 29 16:26:45 localhost kernel: [17187966.296000]  sda: sda1
Jun 29 16:26:45 localhost kernel: [17187966.300000] sd 23:0:0:0: Attached scsi removable disk sda
Jun 29 16:26:45 localhost kernel: [17187966.300000] sd 23:0:0:0: Attached scsi generic sg0 type 0
Jun 29 16:27:01 localhost kernel: [17187981.944000] usb 3-3: USB disconnect, address 25
Jun 29 16:27:01 localhost kernel: [17187981.944000] lost page write due to I/O error on sda1
Jun 29 16:31:55 localhost kernel: [17188276.016000] usb 3-3: new high speed USB device using ehci_hcd and address 26
Jun 29 16:31:55 localhost kernel: [17188276.148000] scsi24 : SCSI emulation for USB Mass Storage devices
Jun 29 16:32:00 localhost kernel: [17188281.148000]   Vendor: Multi     Model: Flash Reader      Rev: 1.00
Jun 29 16:32:00 localhost kernel: [17188281.148000]   Type:   Direct-Access                  ANSI SCSI revision: 00
Jun 29 16:32:00 localhost kernel: [17188281.536000] SCSI device sda: 1984000 512-byte hdwr sectors (1016 MB)
Jun 29 16:32:00 localhost kernel: [17188281.536000] sda: Write Protect is off
Jun 29 16:32:00 localhost kernel: [17188281.540000] SCSI device sda: 1984000 512-byte hdwr sectors (1016 MB)
Jun 29 16:32:00 localhost kernel: [17188281.540000] sda: Write Protect is off
Jun 29 16:32:00 localhost kernel: [17188281.540000]  sda: sda1
Jun 29 16:32:00 localhost kernel: [17188281.544000] sd 24:0:0:0: Attached scsi removable disk sda
Jun 29 16:32:00 localhost kernel: [17188281.544000] sd 24:0:0:0: Attached scsi generic sg0 type 0

It still won't let me write to it, but frankly that's not an issue with me.

I picked up a GE Secure Digital & MultiMedia Card Reader/Writer (:))
 for under 20 bucks.  It's a packaging attempt by GE for a small company/manufacturer called Jasco Products Company, which I think imports the stuff from China -- at least the components. The address for the company (Snail Mail is Jasco Products Company, 10 East Memorial, Oklahoma City, OK, 73114) and the URL for their website is [www.jascoproducts.com](www.jascoproducts.com) 

Module number, by the way, is one of four -- I can't tell which it is because it's not clearly marked on the unit (and my eyesight is not very good, to boot):  HO97929, HO97930, HO97931 or HO979

---

