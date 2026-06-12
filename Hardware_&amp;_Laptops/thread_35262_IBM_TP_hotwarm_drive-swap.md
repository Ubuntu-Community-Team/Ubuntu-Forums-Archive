---
title: "IBM TP hot/warm drive-swap"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by rooster on 2005-05-18
Hello everybody,

I just installed Ubuntu 5.04 to an IBM T20 for my wife (she has to do her PhD-work on it). 

Everything is working quite well and so I hope she will keep it (and not return to M$ Windows)! 

But is there any news to [http://www.ubuntuforums.org/showpost.php?p=30089&postcount=8](http://www.ubuntuforums.org/showpost.php?p=30089&postcount=8) ?

I tested the unplugging of the DVD-drive (the brute way), the computer worked, but I couldn't work with the floppy. After returning the DVD everything worked, too.

How could I get the floppy to work? My wife has many floppy-disks for her texts and for data exchange with colleages.

Or do we need to buy some USB-sticks?

I would appreciate any help, thank you in advance!

Oliver

---

### Post by rooster on 2005-05-20
I have to give an update to the situation:

After removing acpi and adding apm every time I want to swap the drive there is a loud beeping (from BIOS?) like I know it from Windows.

So there is the need to unmount the device?

If there is someone with a good tip I can test I would be very glad!

Thanks out there!

Oliver

---

### Post by rooster on 2005-05-24
Hi everybody,
I spent the last few days searching on the Internet for this problem. But I found nothing :-( :-( :-(

So maybe someone who is more competent than me can have a look at the hot-plug-capabilities.

Since my wife is using the T20 for her PhD I can't test everything with the thinkpad (I had to convince her of Linux), but I'm willing to help with the installation and testing of, e.g., deb-packages for hot-plug! :idea:

Hope someone is reading this...

Oliver

---

### Post by Arthemys on 2005-05-24
I've found that when I load ACPI at grub, it allows me to use the wireless power key and a number of other power related things. Hot swap is one of them, however ACPI on my notebook will not allow me to suspend properly, which is sad because APM can suspend. APM however is older then ACPI.

---

### Post by rooster on 2005-05-24
Hi Arthemys,

so I should give ACPI a try...

Thank you for the tip!!!

In Germany we have a long weekend (Thursday is bank holiday and Friday a got a day off :-) :-)) so I have a little bit of time.

I hope I will not get more problems than are solved with ACPI.

Suspension is not so important for my wife as changing between floppy and CD.

I will write about my experiences.

Oliver

---

### Post by rooster on 2005-06-01
Hi there,

just a few words: I haven't got time for testing... :-(

More to come soon (I hope so...)

---

