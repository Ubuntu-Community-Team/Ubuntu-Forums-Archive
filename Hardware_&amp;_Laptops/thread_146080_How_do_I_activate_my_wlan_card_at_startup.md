---
title: "How do I activate my wlan card at startup??"
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by sudome on 2006-03-17
Hi!
I've just installed dapper flight 5 and is currently involved in a fierce fight with my wlan card (pcmcia).. :D 

To get the card (netgear wg511v2 china) up and going on my toshiba a60 laptop I need to do the following:

1. sudo setpci -s 0:14.4 SUBORDINATE_BUS=0A  --- something with the pcmcia controller, so that the card will be detected by system!(?)
2.eject and reinsert the pcmcia wlan card
3.ndiswrapper -l ---to see if driver and hardware is detected
4.sudo modprobe ndiswrapper ---the leds on the card lights up
5. sudo ifup wlan0 ---bringing the network up

Is there some way to make the os do this at startup by it self or with a single click/command???:confused: 

I'm getting a bit boored typing this all everytime i want to use the wireless network...    phew!

Cheers!

---

### Post by Henry Rayker on 2006-03-17
not that I know how to really fix this, but it sounds like this could be a step in fixing my problem...

where did you find out about that setpci business? basically, I can't even get the system to recognize that I even HAVE a card in the cardbus slot...

I'm having my difficulty in Breezy, though, if that matters.

---

### Post by sudome on 2006-03-18
Hi.. 
I found this out (setpci stuff) in a post in the linuxquestions forum.
(more specifically : LinuxQuestions.org > Forums > Linux  > Linux - Newbie Wireless PCMCIA card D-Link, not found??)

in the post they say that you should add the line at the bottom of rc.pcmcia file, which if unfourtunatly cant find in ubuntu. ](*,)
Suggestions on where this should be written in ubunt would be very much appreciated... 

Hope this helps you... please write if u get it to work for you!

---

### Post by chuckyp on 2006-03-18
You would have to follow the ndiswrapper wiki as to directions for loading the modules on boot.  Typically you just add the ndiswrapper module to the modprob.conf or whatever your distro is using.  Not in ubuntu right now so can't really tell ya.  There is also a command using ndiswrapper -a or -m to add the alias for you but again this is all described int he directions for ndiswrapper.

---

### Post by sudome on 2006-03-18
yeah, done that..

Problem is that the card isnt recognized ( so that the module can be loaded) before the setpci command i have to enter... i think i need to run that command, in some way, before modules are loaded... can this be done? 
Do you know?:confused: 

thanks...

edit:
>>sudo setpci -s 0:14.4 SUBORDINATE_BUS=0A<<  
..is the command. Dont really know what it does but makes the ndis module able to be loaded and card working....

---

