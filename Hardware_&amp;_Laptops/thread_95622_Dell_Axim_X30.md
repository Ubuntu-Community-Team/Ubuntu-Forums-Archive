---
title: "Dell Axim X30"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by Dexter4560 on 2005-11-27
Okey here's the deal,

I just bought a brand new dell axim x30, so i cant get it sync with ubuntu, the problem persist in the fact, that when i plug my craddle to the usb of my laptop and use "usbview" for check the usb conecction the IPAQ thats how it reconized it is going down and going up, on - off i said.

So what can i do?

---

### Post by onesojourner on 2005-12-02
I have a dell x50v and I messed with synce and its not that great. from the research I have done you can sync up your contacts and your calender. no file transfers, no installing programs and no data back up. Those are the 3 things I did the most. I have been backing stuff up to the sd card and sticking it in a camera to transfer the files. 

On a side note check out aximsite.com for lots of info on your pda. Also check out SPB pocket plus (adds lots of features that windows mobile should have had)and SPB pocket diary(makes your calender so much better).

---

### Post by André on 2006-01-15
Hi Dexter4560,

did you finally get this thingy to work?

Thinking about buying a Axim myself and asking myself if it would work ;-)

Greetings
André

---

### Post by TransitMan on 2006-01-15
You folks are trying to use a PDA that a flavor of Windows on it.
Trying to sync it with Linux is like fighting a fire with gasoline. 

Suggestion, why don't you install Wine, and then install the CD disc to sync with the PDA in Wine?

Otherwise, look for a Palm device that will talk to to Linux and Windows without to much of a problem.

---

### Post by André on 2006-01-15
Hi TransitMan,

getting a palm sounds reasonable but as far as i can tell (without actually owing one) is that the newer devices (with wlan and bluetooth features) do not work properly either.

Namely the palm lifedrive and the palm tx are not really what you would call a syncing master right now :-(

That is why i am looking for working alternatives (even when they are running windows) as long as they work ;-)

Greetings
André

---

### Post by batty505 on 2006-04-26
Hi

Yea, I agree with Andre, PalmOS is too old/expensive to run and support for those of us who still have to use M$ for many things.I remember the Palmstuff, and it was great back in the day for what I needed, but my needs have changed.

anyway, I like the features of Ubuntu, and will try Fedora 5/Kubuntu as a server and see if I can migrate my clients, both Linux and M$ to them. if it works the way I expect,  I probably will go linux completely through my lan.

Peace.

---

### Post by brucevangeorge on 2006-10-09
Soooo... Did anyone get the X30, or X3 any other Axim working??

---

### Post by wiresquire on 2006-10-10
I followed the guide [here](http://www.ubuntuforums.org/showthread.php?t=136257).

This worked - kind of. It allows me to copy files to/from my Axim. I really like Synce Trayicon and the gnomevfs. It's almost as good as raki :-)

I had trouble with the firewall. I am running firestarter. Basically, I disable it when connecting to the axim. Do a dmesg when you see the axim trying to connect/disconnect. If you get a lot of firewall log errors, then you'll need to open up the ports/device.

I also had some trouble with multisync syncing between the axim and evolution. Duplicate entries. I've given up on this for the moment. You may be able to get it to work. 

Good luck
ws

---

