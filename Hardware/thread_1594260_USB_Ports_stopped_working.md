---
title: "USB Ports stopped working"
date: 2010-10-12
forum: Hardware
---

### Post by Smartflight on 2010-10-12
About one and a half year ago, I decided to try Ubuntu 7 (or whichever was the latest one that time). To my surprise, I liked it and decided to keep it alongside XP (Vista was too buggy, obviously).

I used it often. I had an Internet connection that would work with USB. One fine time, it decided to just stop working. I was only downloading a song, and BAM! It just stopped, all four of the USB ports. Ever since, they haven't worked. Now I'm back on Ubuntu 10, and I would like to have a solution...if there is one.

My vendor said it's an hardware issue, but I would like you Linux experts to decide.

---

### Post by Smartflight on 2010-10-15
*Bump*

---

### Post by Smartflight on 2010-10-16
Cmon guys!
My USB ports died year and a half ago and I'm hoping I can atleast know if it's just some conflict (my linux friend said that) or not!!

---

### Post by TNT1 on 2010-10-16
What hardware? Do they work under windows? You haven't had usb for 18 months? More details, please.

On my hp6730b, I get periodic usb issues, that can only be resolved by powering down, removing battery and waiting up to fifteen minutes - a solution I found on this forum. I have narrowed it down to a bastardberry issue, as it only happens when I connect that monstrously bad piece of technology via usb - not every time mind you...

---

### Post by Smartflight on 2010-10-19
> **TNT1 said:**
> What hardware? Do they work under windows? You haven't had usb for 18 months? More details, please.

On my hp6730b, I get periodic usb issues, that can only be resolved by powering down, removing battery and waiting up to fifteen minutes - a solution I found on this forum. I have narrowed it down to a bastardberry issue, as it only happens when I connect that monstrously bad piece of technology via usb - not every time mind you...

Hardware, umm, what would you like to know?
I got a Dell Inspiron 1501.

Yes, for around 18 months, I have been without my USB ports. I checked the BIOS- they are turned on. I reinstalled the drivers (by removing all from Device Manager, and restarting) but it did not work. I have tried what you've done with the battery, that doesn't work either.

That's the story when I was mainly using Windows Seven.
The thing is, they all went dead while I was using Ubuntu.

Now I have reinstalled Ubuntu and well, it does not detect anything- does not even give any notification.

And no, they don't work in Windows either. They're just dead.

---

### Post by Smartflight on 2010-10-24
Anyone?

---

### Post by Smartflight on 2010-10-24
This is what 'syslog' reads when I attach a USB pen drive.

```
Oct 24 13:02:52 ruppi-laptop kernel: [ 7977.304094] usb 2-1: new full speed USB device using ohci_hcd and address 2
Oct 24 13:02:52 ruppi-laptop kernel: [ 7977.448090] usb 2-1: device descriptor read/64, error -62
Oct 24 13:02:52 ruppi-laptop kernel: [ 7977.692100] usb 2-1: device descriptor read/64, error -62
Oct 24 13:02:52 ruppi-laptop kernel: [ 7977.932086] usb 2-1: new full speed USB device using ohci_hcd and address 3
Oct 24 13:02:52 ruppi-laptop kernel: [ 7978.072113] usb 2-1: device descriptor read/64, error -62
Oct 24 13:02:53 ruppi-laptop kernel: [ 7978.316372] usb 2-1: device descriptor read/64, error -62
Oct 24 13:02:53 ruppi-laptop kernel: [ 7978.558292] usb 2-1: new full speed USB device using ohci_hcd and address 4
Oct 24 13:02:53 ruppi-laptop kernel: [ 7978.964073] usb 2-1: device not accepting address 4, error -62
Oct 24 13:02:53 ruppi-laptop kernel: [ 7979.100090] usb 2-1: new full speed USB device using ohci_hcd and address 5
Oct 24 13:02:54 ruppi-laptop kernel: [ 7979.512050] usb 2-1: device not accepting address 5, error -62
Oct 24 13:02:54 ruppi-laptop kernel: [ 7979.512124] hub 2-0:1.0: unable to enumerate USB device on port 1
```

---

### Post by Smartflight on 2010-10-26
[I]Bump
[/I]

---

### Post by corncob on 2010-10-26
I usually have found it to be one of my attached devices when my USB stops working.  Try unplugging all the USB cables, including any hub, and boot up.  Try plugging them in one by one.  But I guess after 18 months you've already tried this?

---

### Post by Smartflight on 2010-10-27
> **corncob said:**
> I usually have found it to be one of my attached devices when my USB stops working.  Try unplugging all the USB cables, including any hub, and boot up.  Try plugging them in one by one.  But I guess after 18 months you've already tried this?

The topic title should have been "USB Ports died while using Ubuntu 7."
So yes, I've tried that, and no, it doesn't work.

---

### Post by cellarweasel on 2011-05-16
Those syslog messages look unfortunately familiar.  I also am having this on a friends machine. Weird thing is that the machine is a dual boot and they work perfectly fine in Windows Xp. 

Also Unfortunatly there are a bunch of unresolved threads about USB not working. Is there a diagnostic for identifying hardware vs. software issues? Or are we left with voodoo? any research is appreciated. 
:confused::confused::confused:
-Evan

---

### Post by cliff01 on 2011-07-28
I have the same USB issue since I upgraded (fresh install) from 10.10 to 11.04 I have a Compaq Presario V2000 which has been quite Linux friendly until now. I search these threads every day for a solution. I sure hope the "powers that be" see these posts and can help us.

---

### Post by cliff01 on 2011-08-04
No response, so I will try to either use a previous kernel or go back to 10.10 Stay tuned.....

---

### Post by cliff01 on 2011-08-11
Ok, going to a previous kernel didn't work. I re-installed 11.04 and that didn't work. Next step is install 10.04.

---

### Post by pinkpooj on 2011-08-11
I'm having the same problem on my laptop with 11, I'm going to go ahead and try 10.04 too.

---

### Post by cliff01 on 2011-08-19
My problem was my motherboard on a Compaq Presario V2000 laptop. The usb ports wouldn't work on either Linux or Winblows. Had to retire the laptop. I might try to reset the motherboard to ressurect the usb ports. Ubuntu rocks on my new (used) IBM T42 laptop. So far everything works and works fast.:)

---

### Post by Darth Trix on 2011-08-29
I'm using ubuntu 11.04 in a HP Latptop and i have the same problem. Suddenly all USB ports aren't working.

---

