---
title: "mp3 player USED to work then stopped working"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by WayneSchuller on 2007-01-10
I have a cheapo ebay mp3 player - about 2 years old.

its always worked perfectly in ubuntu, just gets mounted as a usb drive.

but one day it just stopped auto mounting in linux.

the mp3 player itself still plays the music that is still on it, and its osd reports no errors.

the kernel reports strange error messages to /var/log/messages:
Jan 11 06:54:46 homoousion kernel: [17220381.004000] usb 3-2.3: new full speed USB device using uhci_hcd and address 4
Jan 11 06:54:46 homoousion kernel: [17220381.452000] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
Jan 11 06:54:47 homoousion kernel: [17220381.900000] usb 3-2.3: new full speed USB device using uhci_hcd and address 6
Jan 11 06:54:47 homoousion kernel: [17220382.384000] usb 3-2.3: new full speed USB device using uhci_hcd and address 7
Jan 11 06:56:42 homoousion kernel: [17220497.352000] usb 3-2.3: new full speed USB device using uhci_hcd and address 8
Jan 11 06:56:43 homoousion kernel: [17220497.800000] usb 3-2.3: new full speed USB device using uhci_hcd and address 9
Jan 11 06:56:43 homoousion kernel: [17220498.248000] usb 3-2.3: new full speed USB device using uhci_hcd and address 10
Jan 11 06:56:44 homoousion kernel: [17220498.732000] usb 3-2.3: new full speed USB device using uhci_hcd and address 11

it just seems to keep increasing the address number. if I keep unplugging and replugging it just keeps this log message with increasing "address numbers" (up to 23 now and counting)

how can I better diagnose this problem with edgy? can i turn on more usb logging somehow?

---

### Post by hal10000 on 2007-01-10
Plug in the stick and in a terminal window type mount, then plug it off, plug it in again and do the mount command again, compare the two outputs of mount wether  the player is mounted both times. (post the output(s)).

Did you accidentially remove one of the pmount, discover1 or udev packages?
Or did you on the other hand install one of the usbmgr or usbmount packages (which may cause different behaviour than usually)?

Also post the content of /etc/fstab.

What i suppose is, that every time you plug it in and off an in again, it is mounted under another mountpoint, I had this problem some time ago under SuSE.

---

### Post by WayneSchuller on 2007-01-10
> **hal10000 said:**
> Plug in the stick and in a terminal window type mount, then plug it off, plug it in again and do the mount command again, compare the two outputs of mount wether  the player is mounted both times. (post the output(s)).

Did you accidentially remove one of the pmount, discover1 or udev packages?
Or did you on the other hand install one of the usbmgr or usbmount packages (which may cause different behaviour than usually)?

Also post the content of /etc/fstab.

What i suppose is, that every time you plug it in and off an in again, it is mounted under another mountpoint, I had this problem some time ago under SuSE.

well you were right about the discover1 package - I didn't have it (hadn't heard of it). installed it - no difference.

i haven't installed usbmgr or usbmount.

i only use nautilus to graphically mount or unmount devices like this. I don't run any command line utils.

I have other usb mass storage devices (including other mp3 players) that all work fine. The kernel reports to /var/log/messages the vendor and type of device for the ones that work.

But for this one particular mp3 player it stops at the above message and doesn't recognise the vendor or that it is a mass storage device.

I have seen the fstab mounting problem when it keeps getting new numbers - I am not having that problem because nautilus/hal takes care of those details. it feels to me like this is more a lowlevel usb driver issue. anyone recommend some debugging tools for usb?

in fact, using "lsusb" - this device doesn't change anything in that list. my working mp3 player appears in the lsusb list when it is plugged in.

I'm wondering if I have a hardware problem on the mp3 player (even though it independently still plays music and seems to work well) - could it be a faulty usb plug connection?
the software option i'm wondering is if the vendor data for this usb device has gone missing, so if this is so how can I test for this and how could I manually add it to the usb device database (discover1?) as a mass storage device?

---

### Post by hal10000 on 2007-01-11
If you think you have a hardware problem, then plug in the stick and use [COLOR="Red"]sudo fdisk -l[/COLOR] in a terminal window; post the output here.

---

### Post by hal10000 on 2007-01-11
Is your player a usb version 1 or 2 device?

---

### Post by WayneSchuller on 2007-01-11
> **hal10000 said:**
> If you think you have a hardware problem, then plug in the stick and use [COLOR="Red"]sudo fdisk -l[/COLOR] in a terminal window; post the output here.

fdisk -l only shows my hard drives.

as i've said, I only get the obscure message to /var/log/messages, after that, it does not say anything about a mass storage device (or even appear on lsusb) so I don't think fdisk is going to give any info

---

### Post by WayneSchuller on 2007-01-11
> **hal10000 said:**
> Is your player a usb version 1 or 2 device?

i'm not really sure - usb 2 I think. there are no comments on the device about this. (and as far as I understand its the same plug type).

thanks for all your help - please keep giving me ideas!!!

my one idea I haven't tried is to test the device on a windows machine. But I don't have easy access to one...

---

### Post by hal10000 on 2007-01-11
If you have an usb 2 player, then in your /var/log/messages should appear ehci_hcd ........ (and not uhci.....)
So, perhaps you have a kernel module loading problem.

To verify this, then do [COLOR="Red"]lsmod | grep ehci[/COLOR]
If you get no output, then plug off your player, do [COLOR="Red"]sudo modprobe ehci_hcd [/COLOR] (do a lsmod |grep ehci again to see if it's loaded).
Then plug in the player and see what happens.

---

### Post by hal10000 on 2007-01-11
btw, did you reboot after you installed the discover package?

---

### Post by WayneSchuller on 2007-01-11
> **hal10000 said:**
> If you have an usb 2 player, then in your /var/log/messages should appear ehci_hcd ........ (and not uhci.....)
So, perhaps you have a kernel module loading problem.

To verify this, then do [COLOR="Red"]lsmod | grep ehci[/COLOR]
If you get no output, then plug off your player, do [COLOR="Red"]sudo modprobe ehci_hcd [/COLOR] (do a lsmod |grep ehci again to see if it's loaded).
Then plug in the player and see what happens.

I don't have the ehci_hcd module loaded, but I loaded it and it made no difference.

I have many other usb devices, cameras, another generic asian mp3 player. They all work fine, many of them are usb 2.

I'm moving closer and closer to considering it a hardware problem.

Other than "lsusb", is there another way to verbosely watch what happens between the bios and the kernel with regard to usb devices being added?

It is just strange that it just keeps logging "new device" with a new address number. It is like the device doesn't fully communicate its usb specs with the kernel...

Thanks for your help - please keep trying with me, I know we can crack this!

---

### Post by WayneSchuller on 2007-01-11
> **hal10000 said:**
> btw, did you reboot after you installed the discover package?

no - but I just did and no diff.

what I can't remember was whether the device just stopped working one day or whether it stopped working after some software upgrade

---

### Post by hal10000 on 2007-01-11
> Other than "lsusb", is there another way to verbosely watch what happens between the bios and the kernel with regard to usb devices being added
FIRST: the usbview command has some options (see which with [COLOR="Red"]lsusb --help[/COLOR] e.g. you can use [COLOR="Red"]sudo lsusb -v[/COLOR] which gives you much more info than just lsusb.

SECOND: you may install a graphical tool called [COLOR="Red"]usbview[/COLOR] which provides a look to your usbdevices in a gui.

Maybe your right and the player is damaged.

I think we have to get to a new beginning. So plug off your player and reboot (just to be sure we have a well defined beginning).

We might try the following steps:

1. WITH THE PLAYER PLUGGED OFF:
1.1. do [COLOR="Red"]lsusb > lsusb_plugged_off.txt[/COLOR] This creates a file with the name lsusb_plugged_off.txt
1.2. WITH THE PLAYER PLUGGED IN:
do [COLOR="Red"]lsusb > lsusb_plugged_in.txt[/COLOR]
1.3. do [COLOR="Red"]diff lsusb_plugged_off.txt lsusb_plugged_in.txt[/COLOR]

If you get no answer from diff command, then your player is'nt recognized and may be somehow damaged.
If you get an answer, then post it here.
We can then do further steps to go on with testing.

---

### Post by WayneSchuller on 2007-01-11
> **hal10000 said:**
> FIRST: the usbview command has some options (see which with [COLOR="Red"]lsusb --help[/COLOR] e.g. you can use [COLOR="Red"]sudo lsusb -v[/COLOR] which gives you much more info than just lsusb.

If you get no answer from diff command, then your player is'nt recognized and may be somehow damaged.


I have tried usbview - but I think its just the same data as lsusb.

lsusb -v looks interesting.

but unfortunately I have already tried lsusb without and with the device plugged in and there is no difference, it doesn't appear. (tried after a fresh reboot) All my other usb devices appear though.

the interesting thing is I still get that kernel log message about some kind of usb device (see original post), but it doesn't make it to the lsusb list. Is there anyway of getting detailed information about what is happening in the kernel that makes it do that initial report but then goes no further?

thanks in advance for your help - mucho appreciated. (and who knows other people may google there way here to benefit from your help)

---

### Post by hal10000 on 2007-01-11
I'm sorry to say that i have no idea.
I don't know how it comes to the kernel message.
Maybe thr easies way would be to plug it to a windows box and see if it works there.

---

