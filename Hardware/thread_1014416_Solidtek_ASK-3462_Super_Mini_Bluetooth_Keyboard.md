---
title: "Solidtek ASK-3462 Super Mini Bluetooth Keyboard"
date: 2008-12-17
forum: Hardware
---

### Post by bmwman on 2008-12-17
I just got this Solidtek ASK-3462 Super Mini Bluetooth Keyboard. I got it for Christmas and I'm trying to get it to work. Under XP i search for it and when i try to pair, it generates 6 digit code. Then I have to type in the code on the little keyboard itself and then press enter. That's how i pair it to XP. In Ubuntu i edited the  /etc/bluetooth/hcid.conf file and added the mac for the keyboard. Then I do :
```
backend@backend:~$ sudo hidd --search
Searching ...
	Connecting to device 00:18:00:00:6E:64
backend@backend:~$ 
```
So it seems it is connected but it's not. I doesn't give me the code that i'm supposed to be typing.

Any ideas?

P.S. Here is the keyboard:[http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=4222282&SRCCODE=GOOGLEBASE&cm_mmc_o=TBBTkwCjCVyBpAgf%20mwzygtCjCVRqCjCVRq]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=4222282&SRCCODE=GOOGLEBASE&cm_mmc_o=TBBTkwCjCVyBpAgf%20mwzygtCjCVRqCjCVRq")

---

### Post by bmwman on 2008-12-19
bump

---

### Post by bmwman on 2008-12-20
Any hints please?

---

### Post by bmwman on 2008-12-20
Is this gonna work at all or I should return it while I can? I've been reading all day long and didn't see any info on how to pair keyboard which requires PIN. Which is even worse, that PIN is not the same but it's newly generated when pairing.

---

### Post by bmwman on 2008-12-25
It's  been few days and I still can't get it to work.Any help is apreciated.

---

### Post by bmwman on 2009-01-04
I'm sure that someone has run into this problem before. It's just a "simple" pairing problem. It works just fine in Windows but not sure how to get it to work in Linux. No response from anyone is telling me that Windows wins over Linux on this one and I refuse to belive that.

---

### Post by senatus on 2009-01-15
I have the exact same keyboard working on Ubuntu Intrepid.  Admittedly I chose this release because of reported improvements in bluetooth ease-of-use.

---

### Post by generic.humanoid on 2009-02-01
Senatus - So how did you get this working under Intrepid?  I have the same keyboard and can't get it to pair.  The host sees it but the keyboard requires a passcode and I can't find a way to set/register it.  I'm using the Intrepid built-in bluetooth stack.

I finally got this keyboard to work with Hardy using blueman, altho the passcode entry process is not entirely obvious.  Took me a while to figure out that you have to pick a passcode and enter it on the host side, then re-enter it on the bluetooth keyboard.

---

