---
title: "Internal HDD connected through USB not working"
date: 2010-11-15
forum: Hardware
---

### Post by vikrang on 2010-11-15
I recently upgraded my HDD to 160 GB ..I actually wanted to exchange the old HDD (40GB) and adjust with the price of the new one..The comp service guy said that the internal HDD could be used as a USB disk if I purchase a CASE for this..
 
I bought a case thro which I attached the old IDE HDD...
 
The LED is on when I connect (The USB cable had 2 leads which I had to connect it in 2 USB slots- Direct in my cabinet (not thru Hub),,,
 
Ubuntu 10.04 is recognizing the disk in "System Info" as "USB - Generic HDD"...But that's it,  I am not able to run Gparted or anything...Even in win7 , it said "Installing software for devices" and later on nothing happens...This is not shown in File Manager
 
I would like to know how to format and make it usable..
 
Also , since HDDs involve some amount of power , is it wise to connect it to another computer, I mean there wont be an overload or spike or something like that?? We have 220 Volt electricity in my country... Aso logically speaking there has to be a limit I mean, you cant keep "chain loading" multiple HDD through USB Hubs ,right!!

---

### Post by Jacdeb6009 on 2010-11-16
Hi there vikrang,

You wrote :

> **vikrang said:**
> I recently upgraded my HDD to 160 GB ..I actually wanted to exchange the old HDD (40GB) and adjust with the price of the new one..The comp service guy said that the internal HDD could be used as a USB disk if I purchase a CASE for this..
 
I am not quite clear what drives you have.  Are these 2.5 inch or 3.5 inch drives?

If they are 2.5 inch drives, your computer has enough power to run them, but if they are 3.5 inch drives, you will normally need an external power supply for the external hard drive box.  The USB ports on a computer can normally not supply enough power for a 3.5 inch drive.

The "two headed" USB cable does not (in my experience) solve this problem.  I have a couple of external boxes with cables like this and I don't actually know what they are supposed to be used for :)

> Also , since HDDs involve some amount of power , is it wise to connect  it to another computer, I mean there wont be an overload or spike or  something like that?? We have 220 Volt electricity in my country... Aso  logically speaking there has to be a limit I mean, you cant keep "chain  loading" multiple HDD through USB Hubs ,right!!I don't know that connecting the drive to a second computer helps, if anything it may only create more of a problem (I've never actually tried this :) )

As for "chain loading" multiple drives, this is only possible if you use external power supplies.  The USB system on a computer (desktop or notebook/laptop) can only supply a limited amount of power (current), I cannot recall the exact numbers, but it is something like 500mA.  This is fine for a mouse, keyboard, webcam, memory stick and so on; even 2.5 inch drives, but at some point the USB hub cannot supply enough power and then it will simply "throttle" the amount of power available to the ports meaning that some devices will stop working.

I run a number of external drives on my machines for various purposes (both 2.5 and 3.5 inch) but the 3.5 inch drives and some of the 2.5 inch drives are all supplied with external power.

This may explain why the drive light comes on, and even why your system "sees" the drive, but nothing more happens.  There is enough power to "power" up the interface, but to run the actual disk.

Hope this helps!

I will experiment with one of my large drives a bit later when I have some time to see whether I can duplicate your problem.  Let me know whether you manage to fix this.

Cheers,

---

### Post by vikrang on 2010-11-16
Thanks Jac..
 
Well I have a 40GB IDE drive originalled shipped with my bro's Dell Inspiron 6-7 yrs ago.
 
It is a 2.5" disk
 
I tried the following but cant kick start the disk
 
1. In win7 , device manager recognises as "Generic Mass Storage " with all other parameters like volume , etc as "unknown"..In disk management whwn I right click and try to "Initialize disk" , it is not working
 
2.In Linux I dont hava clue ...Ubuntu is also wildly guessing the USB attached as "Generic Storage ddevice" .
 
3. I downloaded Acronis Disk Mgt tool from IBM/harddrive ...THis is not recognizing ..
    I also tried OGA diagnostic tool provided by Hitachi , I am getting the error that some dll file is not located (scsiot.dll)..
 
Think it will have to go to my closet :(

---

### Post by Jacdeb6009 on 2010-11-16
Hi there vikrang,

This is really strange.  I have seen something like this once or twice before.  I have a couple of really cheap and nasty external drive enclosures which I used for hard drives from various "dead" notebook computers and these sometimes have very poor connectors (both internal to the box and on the USB side).  From time to time the drive lights would turn on, but the machine would not see the drive.  Both Linux and Windows would report this as a "generic storage device" but neither would be able to access the drive in any way.  In my case (since I knew that the drives were good and had in fact been used a day or two before) I would normally disconnect the drive and reconnect it and then things would be good (sometimes this had to be done a couple of time before the machine would "see" the drive properly).  Eventually I trashed the boxes and got something better. :)  I have learnt that saving money in this way usually only amounts to wasting money.

It sounds as if it could be a problem with the IDE interface not working properly, but it is difficult to tell.

The only suggestion that I have would be to install the drive in a machine that is known to work and see whether the result is any different (that is, if you have a desktop machine with a spare IDE interface that you know works) also, if you have another 2.5 inch drive installed somewhere that you know is good (that is, the machine detects it as a proper working drive) try installing that in the external drive box and see whether your machine detects this properly.

Lastly, if you know someone that has (or if you have) another external drive box lying around, you could try the drive in this and see what happens.

Depending on the outcome of these tests, you either have a drive that is damaged or you have an external drive box with an interface card that is not working properly.

This unfortunately is a bit time consuming, but I don't know of any other way to figure it out.  Given that it seems to be a problem with both Windows and Linux, I would suspect it to be a hardware issue and not a problem with the OS.

Sorry I can't be of more use on this one.  Hope you can get it sorted without having to bin the drive!

As a side note, I have now trashed all my IDE drives.  They are old and small and the interfaces are a nuisance.  If you are ready to move to SATA drives (of course a question of money and availability depending on where you are located) I would recommend looking at the Icy-Dock products ([www.icydock.com]("http://www.icydock.com"))  I use a MB881US-1S-1 Ez Dock.  This will take both 2.5 and 3.5 inch drives, has a USB 2.0 and eSata interface and a seperate power supply.  It comes with all the necessary cables including a eSata back-plane connector for a desktop in case the desktop only has internal Sata ports.  Really neat and very useful.

Cheers,

---

### Post by vikrang on 2010-11-17
Thanks a lot Jac for the  reply....I will probably wait and see if something else comes up...Like you said , I will connect to my desktop via IDE cable and see or try to see if some other case solves the problem...
 
You are 200% right, sometimes in an endeavour to save money you actually end up losing more !! Considering the effort and the time involved , might as well go in for a new drive !:)
 
 
Thanks once again for the detailed post

---

