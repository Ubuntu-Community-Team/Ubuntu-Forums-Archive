---
title: "USB and external HD not mounting"
date: 2009-10-29
forum: Hardware
---

### Post by yodal on 2009-10-29
I have a western Digital USB HD that when connected the light comes on the drive and the drive makes a repeated dull clicking noise and never lets me view the drive.  I connect the same drive and USB cable to another PC running 9.04 that works perfect on.  I can connect my Black berry to the very same USB port and cable it works fine.  I also put a new USB card in the PC and still same issue.

Any suggestions?

---

### Post by Logan 1229 on 2009-10-29
The clicking is a good sign your drive is failing.  Will work sometimes on some OS but not always.  Use HD tools (ie. smartmontools) to check the health of the drive.  Might not be fully gone yet but will likely be soon.  Backup asap before you loose your data.  Same happened to me few years ago...

---

### Post by yodal on 2009-10-29
I don't suspect it's failing.  It's done this since new (two months now) and has always worked very well on any PC but MINE???

Just booted the PC with a live cd of Kubuntu and same thing, blackberry plugged in and I can access it, memory stick plugged in and I can access it.  I'v tried many different BIOS settings but no luck with the damn drive.

---

### Post by L33tN1nj4 on 2009-10-29
Have you tried the mount terminal command and/or did your hard drive come with an install CD? 
By the way, are your friends/other peoples windows or mac? Try accessing it on another Ubuntu computer.

---

### Post by yodal on 2009-10-29
I mounted it a few months back with similar results.  I since have reinstalled ubuntu.  The other PC's have been same version ubuntu and two other Win PC's.

Is there a specific IRQ USB is suppose to use on ubuntu?

---

### Post by Luis Eduardo Tecnoclasta on 2009-10-30
Yodal,
I have the similar sign in my all sd cards after update to 9.10.
I wish: It's incident with new Karmic. :( 
My cards are mount with smartmontools, but in one minute or two it isn't enable for use.

---

### Post by John Bean on 2009-10-30
> **yodal said:**
> I have a western Digital USB HD
Is it bus powered? Some USB ports don't supply enough power for some portable hard drives and produce symptoms just like those you describe. Self powered devices like your Blackberry are unaffected, as are external hard disks with their own power supplies.

---

### Post by yodal on 2009-10-30
> **John Bean said:**
> Is it bus powered? Some USB ports don't supply enough power for some portable hard drives and produce symptoms just like those you describe. Self powered devices like your Blackberry are unaffected, as are external hard disks with their own power supplies.

That was it John, I got a powered USB hub and things took care of them selfs!

Thanks

---

### Post by John Bean on 2009-10-31
Glad to help. Been there once, used the same fix ;-)

---

### Post by Joebubba360 on 2009-10-31
I have an external WD USB drive as well. Similar problem. Drive has been working on 9.04 and previous w/o problems. My Dell 630 laptop has plenty of power to run the drive. But, cannot see the drive. The light comes on, but the system ignores it.

Any thoughts folks?

---

### Post by Lateralis on 2009-10-31
I think some people are missing the point, but I know exactly what the OP is talking about as I have the same issue with my WD "My Passport" external hard drive. 

Yes; it is powered through the USB.  And yes; some USBs don't provide enough juice to power them.  But My WD hard drive has worked on my laptop ever since I got it in both Windows and Jaunty.  I upgraded from Jaunty to Karmic earlier on this week and the WD passport hard drive no longer automagically mounts.  

The drive is connected though as I can see it when I type *lsusb* into the command line, and I have written an alias to mount it to the same location that it would normally be mounted.  But the point is that it is strange that Karmic no longer does what older versions of Ubuntu did!  

To make matters more complicated, I have two different computers using Ubuntu - my home desktop and my personal work-related laptop.  I upgraded both from Jaunty to Karmic on the same day but the WD passport auto mounts on my desktop but not my laptop and I cannot fathom what the difference is.  (At the expense of labouring the point, I feel I have to reiterate that the WD drive would automount under Jaunty but not Karmic so laptop hardware is not the issue.)  


As an addendum, as the OP has already said, these WD external drives do make a slight "clicky" sound when they are first connected.  This seems quite normal and they do it from day one; an imminent hard drive fail is not the issue.


EDIT: I forgot to mention that this is actually problem I have generally in Karmic with *ALL* external storage devices, including USB flash drives and external hard drives, but again only seems to affect the laptop, not desktop.

---

### Post by John Bean on 2009-10-31
> **Lateralis said:**
> I think some people are missing the point, but I know exactly what the OP is talking about as I have the same issue with my WD "My Passport" external hard drive.
Yes; it is powered through the USB. And yes; some USBs don't provide enough juice to power them. But My WD hard drive has worked on my laptop ever since I got it in both Windows and Jaunty. I upgraded from Jaunty to Karmic earlier on this week and the WD passport hard drive no longer automagically mounts. 
It would seem that you have a different problem, but I fail to see how that means "the point" has been "missed" when the OP reported that lack of power was indeed the problem in his case and all is now well. It's his thread, his problem, and it is now solved - and he made no mention of it being related to Karmic, which is a different issue altogether.

---

### Post by greenkr on 2009-11-01
> **Lateralis said:**
> I think some people are missing the point, but I know exactly what the OP is talking about as I have the same issue with my WD "My Passport" external hard drive. 

Yes; it is powered through the USB.  And yes; some USBs don't provide enough juice to power them.  But My WD hard drive has worked on my laptop ever since I got it in both Windows and Jaunty.  I upgraded from Jaunty to Karmic earlier on this week and the WD passport hard drive no longer automagically mounts.  

The drive is connected though as I can see it when I type *lsusb* into the command line, and I have written an alias to mount it to the same location that it would normally be mounted.  But the point is that it is strange that Karmic no longer does what older versions of Ubuntu did!  

I am also unable to mount my WD passport drive since installing Karmic. Worked fine in Jaunty and also mounts OK in Windows on same PC. I can mount powered external HDs.

How do you create an alias to mount the drive please?

---

### Post by Tokeriis on 2009-11-04
I think I experience the same problem: I cannot mount my "WD MyBook Premium" usb drive after updating from 9.04 to 9.10. Its not a bus powered model.

The drive doesn't show up in the Palimpsest Disk tool. 

Please help me solv ethe problem as I am quite new to Linux.

---

### Post by Lateralis on 2009-11-04
> **John Bean said:**
> It would seem that you have a different problem, but I fail to see how that means "the point" has been "missed" when the OP reported that lack of power was indeed the problem in his case and all is now well. It's his thread, his problem, and it is now solved - and he made no mention of it being related to Karmic, which is a different issue altogether.

Ah, my apologies... I know this is no excuse, but I had read the thread in a bit of a rush as I was getting ready to leave the house and managed to miss yodal's post saying he had solved the problem by using a powered USB.  After reading yodal's first post I assumed our issues were related and thus other people's suggestions were missing the point.  I now see that is not the case so I offer my sincerest apologies for my rashness and the tone of the message.  My intention was never to cause offence.  

But, that being said, it does look like there is a problem with some Karmic upgrades as I am apparently not alone. I did in fact create a thread about this last week after I upgraded but no one seemed interested at the time, although other threads seem to have garnered some attention.

---

### Post by John Bean on 2009-11-04
> **Lateralis said:**
> Ah, my apologies...
Not needed, but appreciated none the less :-)

> But, that being said, it does look like there is a problem with some Karmic upgrades as I am apparently not alone.
I agree. I have tried Karmic and abandoned it; it has IMO far too many major changes in a single release leading to incompatibilities, new bugs and apparent resurfacing of old bugs whose work-arounds no longer work compounded by insufficient knowledge about the new internals for the average desktop user to get a handle on where to even start looking.

I'm sure there are many new users who will love it but for existing users it's got to be the most troublesome update of Ubuntu so far. I'll stay with Jaunty until at least next April...

---

### Post by guiwegian on 2009-11-04
Hi guys,
I v been on the post since yesterday trying everything that has been said so but I am stuck, I cannot mount my pendrive at all, they all used to work on 9.04 but not anymore.
I have 2 external hard drive, with external power, automount fine, one of them has limited transfer speed, only 1Mo/s when the other work as usual. I have a few usb sticks that are all working on windows/ubuntu 9.04 but absolutely nothing on 9.10.I cannot see them.
My keyboard/usb are fine, wifi dongle ok, bluetooh dongle perfect, my nokia 5800 no problem at all.
I am really confused....
Please help.

---

### Post by guiwegian on 2009-11-04
Hi guys,
I v been on the post since yesterday trying everything that has been said so but I am stuck, I cannot mount my pendrive at all, they all used to work on 9.04 but not anymore.
I have 2 external hard drive, with external power, automount fine, one of them has limited transfer speed, only 1Mo/s when the other work as usual. I have a few usb sticks that are all working on windows/ubuntu 9.04 but absolutely nothing on 9.10.I cannot see them.
My keyboard/usb are fine, wifi dongle ok, bluetooh dongle perfect, my nokia 5800 no problem at all.
I am really confused....
Please help.

---

### Post by Lateralis on 2009-11-04
> **John Bean said:**
> I agree. I have tried Karmic and abandoned it; it has IMO far too many major changes in a single release leading to incompatibilities, new bugs and apparent resurfacing of old bugs whose work-arounds no longer work compounded by insufficient knowledge about the new internals for the average desktop user to get a handle on where to even start looking.

I'm sure there are many new users who will love it but for existing users it's got to be the most troublesome update of Ubuntu so far. I'll stay with Jaunty until at least next April...

Yeah, I quite agree with that.  I'm not saying that Canonical and the Ubuntu team shouldn't set ambitious targets, but I think they've done a bit of a Microsoft job with this update.  In particular, I did a fresh install of Karmic on my mother's PC over the weekend and I couldn't find some of the GUI options and things that I was used to in every other edition of Ubuntu.  

I'm sure new people will love it, but for seasoned users it feels like a step backwards rather than forwards. =(

I will persevere with it as I fancy the challenge!  But I am quite disappointed and I don't blame you for changing back to Jaunty; I have considered it!

---

### Post by maldonsailor on 2009-12-08
> **Lateralis said:**
> Yeah, I quite agree with that.  I'm not saying that Canonical and the Ubuntu team shouldn't set ambitious targets, but I think they've done a bit of a Microsoft job with this update.  In particular, I did a fresh install of Karmic on my mother's PC over the weekend and I couldn't find some of the GUI options and things that I was used to in every other edition of Ubuntu.  

I'm sure new people will love it, but for seasoned users it feels like a step backwards rather than forwards. =(

I will persevere with it as I fancy the challenge!  But I am quite disappointed and I don't blame you for changing back to Jaunty; I have considered it!

I am glad you said that, and that it isn't just me.  I had Hardy Heron and upgraded through 8.10 to Karmic, and I'm finding it very disappointing - a bit of a lame duck. Shame.  Would Jaunty Jackalope allow me to see these drives?  Thank you for your advice.

---

### Post by John Bean on 2009-12-09
> **maldonsailor said:**
> I am glad you said that, and that it isn't just me.  I had Hardy Heron and upgraded through 8.10 to Karmic, and I'm finding it very disappointing - a bit of a lame duck. Shame.  Would Jaunty Jackalope allow me to see these drives?  Thank you for your advice.
Try it and see is the only way to find out. I didn't actually use 8.10 so I can't compare directly but in my experience Jaunty is very "well sorted" with very few "new" issues compared with older versions in general - unlike Karmic.

---

### Post by *Boots* on 2010-03-01
I'm sporting a usbless Karmic as well. Its takin my webcam out too!!! ref thread: [http://ubuntuforums.org/showthread.php?t=1384743](http://ubuntuforums.org/showthread.php?t=1384743)

The bug number is: **#445160**

The URL to report the bug is: [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/445160]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445160")

Please report your bugs so the community knows its out there and can fix it. 

Boots

P.S. It seems to me the nature of this problem is somewhat intermittent, and can be fixed by a program that regularly scans the usb system.  Suggestions?

---

