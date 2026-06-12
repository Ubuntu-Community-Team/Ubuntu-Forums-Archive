---
title: "installing external modem, need drivers?, dont have dev/modem folder"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by kye on 2005-07-06
Hi guys,

Im trying to install an external modem, I have it all hooked up turned on and pluged into one of the com ports, I run the pppconfig program set it all up even do a auto detect in the system config networking it finds the modem etc I see the detect lights flash for a second on the modem as it detects,  it finds the right comport when it auto detects but thats as far as I get, it wont ring out, do I need to install some modem drivers or something?, I have noticed I dont have a /dev/modem folder which I think I need, love some help with this.

Thanks guys.

---

### Post by intangible on 2005-07-06
pppconfig seems to find your modem?  Or does it say it can't find it?

An external modem will most likely be /dev/ttyS0 (com1) or /dev/ttyS1 (com2)  you don't need a /dev/modem, just point any program that needs to access the modem at the correct serial port.

---

### Post by kye on 2005-07-06
Yes it finds it and so does the auto detect in the system config, networking program it finds it and gives it a port, when I try to dial with the modem with the modem lights program it doesnt ring out, for eg. I tryed to get it to ring my phone it couldnt and I dont see any new lights light up as it dials, or any sounds etc even with the modem speaker turn all the way up, only the standard lights stay on.

I have tryed 2 diffrent external modems on this and they are doing the same things, ( not dialing but are being auto detected fine) one modem is brand new

In the system config, networking program after it does an auto detect and finds it etc and puts it in the list there is an active box on the side of it a check mark goes in the box for a second then disapears should that check mark be there all the time in that active box?

Thanks for your help.

Kye.

---

### Post by intangible on 2005-07-07
Have you tried testing it with minicom?  You can talk to the modem directly using it and see if it's working properly.  (it should be on the install cd, I think)

**sudo apt-get install minicom**
**sudo minicom -s**
[indent]Select "Serial port setup"
Press "A" and type in the correct port if it's not correct, hit Enter to leave that screen (leave the rest defaults)
Select "Save setup as dfl"
Go down to "Exit"[/indent]

Now, you may see a line that starts with "AT(some junk)" and hopefully an "OK" after that.  That tried to initilized your modem.

Now, let's test the modem itself, type this in:
**ATDT5555555**
That should try to dial a number (5555555) you can try a number you know and see if it goes through.

Press CTRL and C to stop it.
CTRL and A together, then X afterwards to exit minicom. 

This should let you know if the computer can at least talk to the modem and then we can start looking elsewhere for the problem.

---

### Post by abr_ora on 2008-01-07
Sorry to disturb
M new user of UBUNTU and just trying the forum.

---

### Post by abr_ora on 2008-01-07
May any body kindly reply me to check this forum for any help. plz

---

