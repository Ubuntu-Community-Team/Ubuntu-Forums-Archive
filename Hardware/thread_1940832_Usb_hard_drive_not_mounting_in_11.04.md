---
title: "Usb hard drive not mounting in 11.04"
date: 2012-03-14
forum: Hardware
---

### Post by kd4dii on 2012-03-14
Hello
     I am running Ubuntu 11.04 on my Toshiba laptop.  I have a Western Digital my book usb hard drive.  It was working fine a few days ago but now it is not auto mounted when plugged in.  It doesn't show in gparted.  The only place it shows is in the Gnome device manager.  
     The device was a little strange for an external drive while it was working.  If you did a safely remove drive it would disconnect and reconnect right away.  The only way to disconnect it was to power down and unplug the usb connector with the system down.
     I would really like to get this drive back working as I use it for back up and storage and have a lot of stuff on there I don't want to lose.  Any help is appreciated.

Thanks
Bob

---

### Post by kd4dii on 2012-03-15
Hi again
     Anybody have any ideas on this.  I would try mounting it through the terminal but I am not sure what commands to use.  Any suggestions are welcome.

Thanks
Bob

---

### Post by ahallubuntu on 2012-03-15
Obviously the drive could be failing or could have failed completely.  Hard drives fail all the time, sometimes gradually, sometimes without warning.  That's why it's crucial to keep two copies of important files on different devices.  Sometimes when a drive fails, it's impossible to get data off without paying for expensive data recovery (where they may even take the drive apart).

It's hard for people to help you try to debug something a bit obscure without asking you 80 questions about it.  Have you tried plugging the drive into a different computer (Linux or Windows - is it formatted as a Windows drive that is FAT32 or NTFS?)?  In your case, that's absolutely the first thing I would do so I could make a backup ASAP of those important files so I wouldn't lose them.  If the drive does not work on another computer then it's probably the drive itself failing or failed.

With an external drive that has failed, you can also take the drive itself out of the casing and try plugging it into another enclosure or adapter  in case only the old controller or power supply was the problem.  You could also plug such a drive directly into a desktop computer.  The trick is that many of these external drives are sealed with special screws that make them difficult to get open.

---

### Post by kd4dii on 2012-03-15
Hi
     Thanks for the reply.  The drive is formatted as ntfs.  I have tried it on another computer also running 11.04 but no joy on that.  The drive is a Western Digital Mybook which is a sealed housing that I don't think I could open easily, don't see any screws on the outside to remove to open it and for all I know it could have some sort of non-standard hook up inside.  I guess it is a write off.  Oh well.
     Thanks again for the reply.

Bob

---

### Post by ahallubuntu on 2012-03-15
Bob, if this is a drive with its own power supply (not just a USB cable), I would probably try a different power supply first.  If the power supply has simply failed, that might be all there is to it.  Also, if it ISN'T the type of drive with its own power supply, (just has a USB cable and nothing else to power it), you might try one a USB cable that has TWO USB plugs on the end to attach at the same time to a computer, to give it 2X the power.  Yes, I know that if it worked before it shouldn't need two plugs now...but I'm also not sure how/where it has been plugged in in the past.  Not all USB ports provide the same power.

I'd also try plugging it into a Windows computer too if possible, just for kicks.

I think if you could open the drive it's a pretty standard type of drive.  You would likely destroy the outside casing if you get it open, though, so you'd have to plug it into something else permanently - but if you're ready to write it off anyway, not much to lose.  I'm pretty sure you can open it without destroying the drive itself, even if the hard casing around it is cracked afterward.

---

### Post by kd4dii on 2012-03-15
Hi
     The drive has its own power supply.  I don't have a Windows box available to try.  I will dig around in my junk box to see if I have another power supply in the range of the one that came with it and give it a shot.  Still a bit reluctant to pry off the case as the only other system I have is not working at the moment.  I will probably do that once I get the other box working.  Thanks again for your help.

Bob

---

