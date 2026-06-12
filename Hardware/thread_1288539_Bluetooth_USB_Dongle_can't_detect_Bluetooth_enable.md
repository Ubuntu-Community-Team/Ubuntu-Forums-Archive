---
title: "Bluetooth USB Dongle can't detect Bluetooth enabled devices"
date: 2009-10-11
forum: Hardware
---

### Post by the_joey_o on 2009-10-11
I'm having trouble getting my computer to recognise any bluetooth device, including my Wiimote and cell phone. I have a USB Bluetooth dongle that appears to be working. When I plug it in, I get the bluetooth symbol in my device tray. The USB Bluetooth dongle also works in my other laptop that runs Windows Vista, although I had to download a driver from [bluesoleil.com]("http://bluesoleil.com/download/Default.aspx") to make it work. I downloaded and installed an Ubuntu version of the software from bluesoleil, but when I try to open the program, nothing happens. I'm running Jaunty on an old Gateway tablet.

I'm not certain what the make and model is for the dongle, but here's a [link to the page]("http://www.shop4tech.com/item6492.html") that has all the info for the product.

I first posted this question in the [HOW TO: Wii remote in Ubuntu 8.04 thread]("http://ubuntuforums.org/showthread.php?t=836231&page=25&highlight=wii+remote"). 

Additionally, there are two threads with very similar issues that appear to be unresolved:
[http://ubuntuforums.org/showthread.php?t=1242948&highlight=Bluetooth+USB+Dongle]("http://ubuntuforums.org/showthread.php?t=1242948&highlight=Bluetooth+USB+Dongle")
[http://ubuntuforums.org/showthread.php?t=1224854&highlight=Bluetooth+USB+Dongle]("http://ubuntuforums.org/showthread.php?t=1224854&highlight=Bluetooth+USB+Dongle")

---

### Post by madsmeg on 2009-10-11
It might not be the best advice, but what i did to get my bluetooth working was look in synaptic for "bluetooth" and downloaded anything that looked important for the running of a bluetooth device. I stress this is not the best or most technically savvy approach, but it worked for me :)

---

### Post by Boondoklife on 2009-10-11
Hey one more thing I forgot to mention, try to load up the new karmic iso and see if that works. I have a few devices that really benefited from the new release.

---

### Post by tqft on 2009-10-11
> **Boondoklife said:**
> Hey one more thing I forgot to mention, try to load up the new karmic iso and see if that works. I have a few devices that really benefited from the new release.

I am running karmic and have a similar problem with my bluetooth adapters.

Looks like they want to work and then time out? "Fail to parse incoming data" is what Nautilus reports.  So Karmic is no guarantee.  I haven't dug into it yet.

The oldest bluetooth adapter was working in Intrepid, so I know they work.

---

### Post by the_joey_o on 2009-10-11
> **madsmeg said:**
> It might not be the best advice, but what i did to get my bluetooth working was look in synaptic for "bluetooth" and downloaded anything that looked important for the running of a bluetooth device. I stress this is not the best or most technically savvy approach, but it worked for me :)

Tried this. Didn't work, but I like the creative thinking. :D

> **Boondoklife said:**
> Hey one more thing I forgot to mention, try to load up the new karmic iso and see if that works. I have a few devices that really benefited from the new release.

Can I test this off the disc? Or do I have to actually upgrade to the beta?

---

### Post by the_joey_o on 2009-10-11
> **tqft said:**
> I am running karmic and have a similar problem with my bluetooth adapters.

Looks like they want to work and then time out? "Fail to parse incoming data" is what Nautilus reports.  So Karmic is no guarantee.  I haven't dug into it yet.

The oldest bluetooth adapter was working in Intrepid, so I know they work.

Yeah. 1 in every 100 tries will give me the Bluetooth mac number and maybe identify the device, but it won't stay connected for more than a second.

---

### Post by the_joey_o on 2009-10-13
Bump.

Any more ideas???

---

### Post by tqft on 2009-10-18
As far as I know this is the main bluetooth bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502?comments=all)

"Leif Gruenwoldt  wrote 13 hours ago:  	  #258

Success! Fixed for me on Ubuntu 9.10 Karmic-beta Live-CD

"

So I am going to update again now and see how if anything is working again.

Mine isn't a clean Karmic install so I may try some stuff - something like
suXXXdo dXXXpkg-reconfigure -a *blue*
Suggestions appreciated
[XXX's so people don't just copy and paste hoping it works and blame me]

---

### Post by tqft on 2009-11-04
This isn't me filing this bug, but I have subscribed to it

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/453885](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/453885)
"Since my upgrade to kubuntu karmic my USB dongle stopped working, but it still works in my other jaunty machine and in Windows XP."

---

