---
title: "dismanteling IBM laptop"
date: 2008-08-28
forum: Hardware
---

### Post by suri.mahendra on 2008-08-28
Hi,

I got a an IBM thinkpad a20 from ebay.  The BIOS is password protected so I cannot change the boot sequence.  I have tried to reset the BIOS via software and disconnecting the BIOS battery nothing worked.  Now I need to rip the unit apart to jump some pins on the BIOS.

I got so far and then it seems I can't expose the motherboard.  Any suggestions on how to proceed?

thanx

---

### Post by kerry_s on 2008-08-28
ibm uses a security chip, your screwed.

try pressing f12 at boot to select a boot device.

from the manual:

> Supervisor password:
A supervisor password (SVP) protects the system
information stored in the IBM BIOS Setup Utility. The SVP
must be entered in order to get access to the IBM BIOS
Setup Utility and make changes to system configuration
settings.
      Attention
    If the SVP has been forgotten and cannot be made
    available to the servicer, there is no service
    procedure to reset the password. The systemboard
    must be replaced for a scheduled fee.


---

### Post by linux_tech on 2008-08-28
I had a T21 that the lcd went out on .  So I looked on ebay and found a "working" T21. When I got it, I turned it on and it immediately went to the password screen. It had a security password that was set on the a special chip on the systemboard.  Thanks IBM! The best thing to do is resell it for parts, the display is worth about $100, so you could probably get approx $150.  I learned that its pretty tough to buy a laptop on ebay, unless you 
 get it from a really reputable seller that offers a good return policy.  Your much better off test driving one in the store before buying.  I know Dell has a 21 day no questions asked return policy and after that a 1 year parts and labor warranty built in to the price.   

Here is the alternate route.  I wouldn't suggest it unless you really enjoy electronics projects or maybe have a electronics shop that would do it.  But it would probably end costing more than the laptop is worth. 
[http://www.ja.axxs.net/unlock/](http://www.ja.axxs.net/unlock/)

---

### Post by kerry_s on 2008-08-28
i found this-> 
[http://www.cgsecurity.org/wiki/CmosPwd](http://www.cgsecurity.org/wiki/CmosPwd)
[http://www.tech-faq.com/ibm-thinkpad-bios-password.shtml](http://www.tech-faq.com/ibm-thinkpad-bios-password.shtml)

i found the hardware hack->
[http://sodoityourself.com/hacking-ibm-thinkpad-bios-password/](http://sodoityourself.com/hacking-ibm-thinkpad-bios-password/)

---

### Post by linux_tech on 2008-08-28
It can be done.  The system board probably has to come out to have enough room to solder the the serial port that will be used to connect to to get the 
password.  The chip is on the bottom side surrounded by plastic case. The chip is quite small so you need to be good with soldering small components.
You need to be careful not to damage the system board and also solder the leads to the correct location on the correct chip.  This is what increases the difficulty rating. 

After soldering the 2 leads off the chip you have to be careful with reassembling so the wires do not lose contact. The laptop needs to be reassembled before it can be powered on.

---

### Post by Comzee on 2008-08-28
I don't know if this  will work or not, but you should try it out before you start soldering stuff onto your mainboard lol.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)


It's a sweet compilation of bootable programs that has every thing from memory and hard drive testing software to stuff like bios resets and password recovery. The specific programs it has on it for bios password cracking and resetting are:

BIOS 
WipeCMOS	 
CMOSPWD	 
!BIOS

Just download the iso, burn it to a disc, then boot from it.

Usually the preset key for the boot screen selection is f10 or f12. try looking at your specific notebooks manual to make sure. You could probably find it at ibm.com

---

### Post by RedPandaFox on 2008-08-28
I got an IBM Think pad, its a mean one to take apart! I spent an hour and a half trying to get it apart but couldn't get the final screw! I ended up giving up and leaving everything the way it was.

---

### Post by linux_tech on 2008-08-28
That cd has some good tools on it.  But for this situation the password is not on the bios chip, its on a different chip  The sole job of the chip is to provide the encrypted password.  I think this was a impractical design to have bios security on a second chip that was so simple that the only way to interface with it was through the terminals on the chip itself.

---

