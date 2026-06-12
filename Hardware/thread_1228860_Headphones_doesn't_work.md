---
title: "Headphones doesn't work"
date: 2009-08-01
forum: Hardware
---

### Post by Elijah on 2009-08-01
Hi, 

I've just recently purchased an MSI CR400 laptop and found out that the headphone jack doesn't work with jaunty, the sound still outputs to the laptop speakers and doesn't get transferred to the actual headphone jack. 

> 00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)

There is no hardware problem with the jack as I've tested it with the latest fedora install, it's only on this installation that it doesn't work. 


Anybody has the same problem? 


Best regards, 
Elijah

---

### Post by Elijah on 2009-08-03
> **Elijah said:**
> Hi, 

I've just recently purchased an MSI CR400 laptop and found out that the headphone jack doesn't work with jaunty, the sound still outputs to the laptop speakers and doesn't get transferred to the actual headphone jack. 



There is no hardware problem with the jack as I've tested it with the latest fedora install, it's only on this installation that it doesn't work. 


Anybody has the same problem? 


Best regards, 
Elijah

aw c'mon, nobody? :( 

I've already tried upgrading to the latest alsa to no avail..

---

### Post by jaxsrb on 2009-08-03
have you tried other spikers / headphones you plugged corectly
i'm using jaunty netbook remix for my msi u-100 wind .. have no problems with sound.

---

### Post by Elijah on 2009-08-03
Yes, everything I've got. I also have that netbook of yours, it works fine in there of course.  

But I have this new MSI cr400 that has a different chipset than the netbook. 

And like I mentioned - it worked in fedora so it's most likely a driver/module issue.

---

### Post by thenoid on 2009-10-11
Hi,

Same problem here with my newly bought msi cr400. Audio out worked with Windows Vista trial version. Has this been fixed yet? Thanks in advance.

Dino

---

### Post by thenoid on 2009-10-11
Upgrading ALSA worked!!! - [URL="http://ubuntuforums.org/showthread.php?p=6589810"]http://ubuntuforums.org/showthread.php?p=6589810 
[/URL]

---

### Post by Cruuncher on 2009-10-12
i have this problem with an Acer Aspire 5536-5255, headphones work when i run vista

---

### Post by Elijah on 2009-11-24
> **thenoid said:**
> Upgrading ALSA worked!!! - [URL="http://ubuntuforums.org/showthread.php?p=6589810"]http://ubuntuforums.org/showthread.php?p=6589810 
[/URL]

Thanks! that works real good =) 

A few notes though as I struggled a bit to keep it working
- 2.6.31-15 kernel ver doesn't seem to work for me (display is ruined)
- but 2.6.31-14 kernel works real fine, anything below like -11 and it won't work.

---

