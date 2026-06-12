---
title: "Building a simple server...do I need RAID, etc.?"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by dbsoundman on 2008-01-13
I'm toying with the idea of building myself a relatively simple server someday that would serve mostly as a glorified router, but also to setup a network printer, FTP server, and a shared filesystem in the home network. Maybe even host a website someday. I have some hardware questions though. My main concern is whether or not it is really necessary to have a RAID hard drive setup or not. I understand it is advantageous, but I'm not looking to store a lot of information in the shared filesystem, FTP server, or potential website. I am for the most part content with keeping files on individual computers; if I really needed to share them, that's what the FTP server is for really. I'm just concerned about overall performance. The main reason why I want to see if I can skimp on the RAID bit is because I would most likely be making this server out of the cheapest computer I could find. Obviously I would have to upgrade some hardware, but spending $100 or more on a new board for RAID hard disks which I would then also have to buy was not really high on my list of things to do in this cheap endeavor.

My other question relates to network cards. I would be interested in putting in multiple network cards so that I could use the server as a switch essentially as well. Is there some sort of limit on how many network cards I could put in (other than slot space)? I understand I would need at least two to do what I want, because I would need one card for getting the network in (if it's not already included on that computer) and one for getting it out. Is it more advantageous/cheaper to use a switch than multiple network cards?

And one final question: in terms of network printing, can I use a printer with a USB interface, or do I need to actually have a network-connected printer? I wasn't sure if the printer would be addressed through the network, or the network would address the printer through the server.

Any other suggestions would be appreciated too. I think once I get the hardware straightened out, the configuration I can probably figure out from the myriad howtos out there and the given information from the hardware choices...it's just the hardware choices that has me a bit confused.

Thanks!

-Dan

---

### Post by nethbar on 2008-01-24
Dan,
I can answer a few of your questions:

- RAID shouldn't be needed for a simple file server setup.  Your network card won't be able to pass data faster than the hard drive can provide it.  RAID 0 would boost overall system performance, RAID 5 is nice to guard against hardware failure (but you'd still want to backup in case of data corruption) but in your setup, I still don't think so.  

NOTE: you can implement any RAID level using the linux mdadm tools without a hardware controller and still get great performance.  If you don't mind the extra work and were already planning on buying **new** identical drives, I'd stripe them in RAID 0

- I've never run multiple network cards to emulate a switch.  You'd need to 'bridge' them somehow.  The DD-WRT project does that sort of thing with PCs.  I would still recommend a switch though:
* They're cheap.  $20 on Newegg, $50 if you want one with 24 ports
* Less strain on power, cooling and space in your PC
* Less complexity in your setup.  If they're not bridged properly, it could screw up the network services you're providing.

- So long as the printer is supported in Linux (Check out [http://www.linuxprinting.org/](http://www.linuxprinting.org/)), you can share it out on the network using Samba.  It will show up just like a shared printer in Windows.

Good luck with it!

---

### Post by Whiffle on 2008-01-24
Just as an example, I'm running a server here in my apartment that 

hosts a website (although it has almost no traffic...)
ftp
printing
torrents
provides music to my stereo (mpd)
some backup from my main computer

its running on an old compaq laptop w/ ubuntu feisty on it.  Works fine, printing is as fast as if the printer were plugged directly into my computer.  Its not pretending to be a router though, as it only has one lan card and I have a wireless router to do that anyway.  Nothing special on the hardware end (its a presario 1694, 450mhz amd k6-2)

If I were in your position, I'd find the cheapest old hardware you can find that will do what you want it to (I actually wish mine had USB 2.0 on it), and run it till you figure out what kinds of things you'll be using it for.  If you end up doing more than it can handle, upgrade.  Theyr'e very handy to have around,   and I keep finding new ways to put the thing to use.

---

### Post by dbsoundman on 2008-01-24
Thanks for the info! I did find a friend of mine (the person who built me this ubuntu desktop machine I'm using now as a gift actually) has a spare old tower I could use for this project. I think I might try using something like RAID 0. I'm not sure when I'll get around to actually putting this together though.

Oh, and about the printer: it is not a serial printer, it's USB. It is linux compatible (it's an HP), but it's one of those print-scan-copiers, so that brings me to a question: would I still be able to use the scanning part? The way it is now I actually have to open XSane Image Scanner to do the scanning. So would that mean that I would need to dedicate a monitor to the server so I could scan images on the server itself, then save them and retrieve them through a network drive or something? For that matter, how would I set up a network drive? I would rather it be something that automounts, sort of like network drives in larger windows networks.

Finally, how exactly would a switch work? Assuming the server only has one network card, how would I get the network back out of the server to go to the other PCs in the network?

Thanks for answering my newbie questions!

-Dan

---

### Post by nethbar on 2008-01-28
I don't think you'd be able to use it as a network scanner but you CAN scan over the network. (?)  You can setup your network server to run VNC which will allow you to log in to it over the network and use it as though it had a keyboard, mouse and monitor hooked up.  Then you just use XSane to scan the images and store them on a network drive.  You can set up network drives to automount too.

I would have the images stored on the server's local hard drive and then have that directory show up as a network drive on all the other PCs.  If you're running any Windows PCs, you should setup Samba for network drives but might do it anyways 'cause Samba is nice.

The switch handles what's going in and what's going out.  All you need is one network card and a patch cable plugged in to the switch.  Your network might look like this:

Internet
\/
Switch <-Ethernet Cable-> Server <--USB cable--> Printer
/\   
L-------> PC
L-------> PC
L-------> etc.

---

