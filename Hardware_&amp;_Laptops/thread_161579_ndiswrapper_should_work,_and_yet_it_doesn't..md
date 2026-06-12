---
title: "ndiswrapper should work, and yet it doesn't."
date: 2006-04-17
forum: Hardware &amp; Laptops
---

### Post by theoldsausage on 2006-04-17
Ok, recently I install ubuntu 5.10 on my dell inspiron 2200 laptop. My wireless card is a "dell 1370 Wlan Mini-PCI."   The first thing I did was check if my wireless card was supported. Obviously, since I am asking this question, it was not. The next thing I tried to do was to setup ndiswrapper, this went smoothly and I opened the graphical interface to select my wireless cards .inf file. This also worked, just to be sure I ran the "ndiswrapper -l" command in the terminal. This showed that the driver was functioning as it should.
Next I proceeded to run the " sudo depmod -a" and the " sudo modprobe ndiswrapper" commands. I checked for error messages, there were none. 

Here comes the problematic part, when I run the command "sudo ifdown wlan0" I get the error message "/etc/network/interfaces:16: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces" The same thing happens when I run "sudo ifup wlan0" . 

Does anyone happen to know why this is happening, and how I can fix it?.

Thanks

---

### Post by mpvano on 2006-04-18
Does the file exist? It sounds like it's missing or contains no information about the interface. If you don't put instructions there for ifup and ifdown, they won't know what to do.

Ubuntu Breezy usually doesn't use it for all operatons. It's used by the setup program to set your default networking for when you startup, but the Gnome applets that most people use to configure networks may or may not update the file and may not do so correctly since they don't use it.

Network control and startup are part of the scripting that's added by each release's individual vendor. Instructions for one distribution are usually incorrect for another.

If you want to manually use ifup and ifdown, you'll need to read how the file's constructed and operates (try "man interfaces") and make sure the file contains meaningful information.

Try using the gnome applets in the System:Administration menu first to configure your interface, if they don't do what you need, then you'll need to learn how to write interfaces files. Search this forum on that topic. It's been discussed over and over in literally HUNDREDS of postings,

It's usually a good idea to search this forum first before asking questions. Most problems have occurred before.

Mario

---

### Post by trent dillman on 2006-04-18
What does your /etc/network/interfaces file have in it? Post it here, but be sure to remove any WEP keys...

---

