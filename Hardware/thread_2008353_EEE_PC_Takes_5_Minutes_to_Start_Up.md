---
title: "EEE PC Takes 5 Minutes to Start Up"
date: 2012-06-22
forum: Hardware
---

### Post by ChannelZ28 on 2012-06-22
my laptop is acting weird. its an asus eee pc 900. when i turn it on, there is no startup sound, the initial ASUS screen comes on and stays on for about 5 minutes. from there it starts up, i hear the fan turn on and it goes to the black screen with the blinking cursor in the top left. it stays on that screen for about a full minute before the operating system starts up normally. 

everything then works fine. i dont think it has anything to do with ubuntu since the slowness is before it loads up. what could be causing the delay?

---

### Post by john stiles on 2012-06-22
Sounds as if the system is searching for a bootable drive. Check the BIOS settings to see that your boot drive is the first in the queue. Disable any unused drives in the BIOS. You could also check the grub menu options to see if there is a delay set. I'm not sure how any of these may have crept in, unless you have recently upgraded the system?

---

### Post by ChannelZ28 on 2012-06-22
thanks, i already checked the boot order. but what is the grub menu option and how do i check for delays?

i just replaced the keyboard. thats just popping the old one out and a new one in. it shouldnt affect anything. this started happening as soon as the new one went it. i assume thats pure coincedence.

---

