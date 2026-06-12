---
title: "USB Hard Drive not seen"
date: 2013-02-02
forum: Hardware
---

### Post by ctav01 on 2013-02-02
I got one of those cables that you can connect to caseless IDE or SATA hard drive and then plug it into a USB port and it's worked great for the most part.  Out of 20 or so hard drives, it's only had problems with two IDE drives.  At first, the system wouldn't see them and then I somehow got them mounted and I was able to copy my data off but I'm trying to connect them up again to securely wipe them and they're just not showing up in Disk Utility.  I've tried rebooting several times without success and I was hoping one of you would have a suggestion or maybe a secret Linux command that would get the USB ports to do a hardware scan (sort of like Windows PnP). Thanks.

---

### Post by gavinjb on 2013-02-02
Is it USB3 as I have heard that a lot of the USB3 devices don't work with Linux (unless you connect through USB2).

Also if you run lsusb in the console can you see it listed?

---

### Post by ctav01 on 2013-02-03
It's just a cable and connectors, I doubt it's usb anything.  Plus it worked for my other drives and it even worked for these two drives, it's just not working at the moment.

If I run lsusb, it does not see the external drive.

---

### Post by sudodus on 2013-02-03
What computer is it? If a desktop or workstation, you can try to connect the 'bad drives' internally.

If not, try to connect them to another computer via your cables or internally, if you have or can borrow one (be it Windows or desktop or laptop ...)

---

### Post by Mark Phelps on 2013-02-03
One thing that makes IDE drives different from SATA is the presence of jumpers.  You should check to make sure the jumpers didn't get dislodged.

---

### Post by varunendra on 2013-02-04
> **ctav01 said:**
> It's just a cable and connectors, I doubt it's usb anything.
There is no such cable in existance which is 'only' cable and nothing in-between the two interfaces (USB and SATA/PATA). All such cables include some kind of circuitory (although it may not necessarily be a separate 'box' in-between) to convert SATA/PATA(IDE) interface to USB. This circuit typically needs 3 or 5 volt supply for itself (apart from the power supplied to the drive) to operate, and can malfunction if this supply drops.

That being said, a few possibilities I can recall are-
[LIST=1]
[*] The drives themselves are dying, since you mentioned they had problems initially in being detected.
[*] If the drives are connected and still lsusb shows nothing, it indicates a possible failure of the adapter (the cable) itself, although there may be a few other reasons as well
[*] If the drives are drawing power from the USB itself (as in 2.5" drives), then maybe they're drawing too much power that the USB port can not supply. Drawing too much power is a common problem for certain drives, especially when they get old.
[/LIST]
In any of the above cases, it is a good idea to try connecting them internally if possible, like *sudodus* suggested.

Otherwise, please give us a description (or maybe a weblink or snap) of your cable and the drive you are connecting (2.5" or 3.5", capacity, etc) and maybe we can make a better guess and offer you a better suggestion accordingly.

Also, connect the drive via the cable, then run and post outputs of -
```
lsusb
dmesg | tail
```
These adapters usually appear as "USB SATA & PATA bridge" in lsusb output. In case of certain errors, dmesg should show us something.

*@ Mark*, in my personal experience (with a few Seagate/Samsung 40GB PATA drives), I've seen that the jumper settings do not have any bearing if the drive is connected via such a USB adapter. But I can't be sure since I don't have much extensive experience with these drives.


**PS:**
*@ gavinjb*, I haven't yet seen any complains with USB3 that are Linux specific like you mentioned. Could you please provide source of such information? I'm asking because I myself have a USB3 port in my Asus X54C and I keep using it all the time, although all the devices I connect are USB2 except a seagate USB3 external drive I once connected (with no probs of course).

By the way, I'm not criticizing, just curious. Hope you don't mind :)

---

### Post by grahammechanical on 2013-02-04
Have you checked the settings in the BIOS? You say

>  At first, the system wouldn't see them and then I somehow got them mounted and I was able to copy my data off 

What did you do then? Do it again?

I recently created a Ubuntu live USB memory stick but I could not get my machine to boot from it. But I was able to do something like this in the past. I had the boot priority set correctly. After going into the BIOS again and again I noticed that when I open the BIOS setting utility with the USB stick in a port I got an extra setting.

The BIOS saw the USB stick as a disk drive and in this menu it was the second drive to boot from. Despite Removable Drive being the first drvie to boot from in the other menu. I had to change the boot order in this second menu as well. I did not know my BIOS utility had that feature.

Now, I know this is not your problem. I am using my experience to suggest that the answer to your issue might be in the BIOS settings.

Regards.

---

### Post by kiwited on 2013-03-10
> **varunendra said:**
> *@ gavinjb*, I haven't yet seen any complains with USB3 that are  Linux specific like you mentioned. Could you please provide source of  such information? I'm asking because I myself have a USB3 port in my  Asus X54C and I keep using it all the time, although all the devices I  connect are USB2 except a seagate USB3 external drive I once connected  (with no probs of course).

By the way, I'm not criticizing, just curious. Hope you don't mind :smile:

I am having problems with my usb3 seagate expansion drive not being seen by the computer on boot, but being recognised by Ubuntu once booted. The drive is seen and can be booted when plugged into USB2.

I have been in contact with Asus with the responses as follows:
[I][FONT=Verdana]"Dear Valued Customer,
Thank you for contacting ASUS Technical Service.
USB 3.0 ports only work under OS. This is normal.
Sorry for the trouble. Wish you a good day.[/FONT][/I]"

My further query to confirm that it was "normal" that one could not boot from a USB3 drive received this:
[I][FONT=Verdana]"Dear Valued Customer,
Thank you for contacting ASUS Technical Service.
Yes. USB 3.0 needs driver to work. So that you could find USB 3.0 driver on our website.
Sorry for the trouble. Wish you a good day.[/FONT]"[/I]

I have not found the driver.

I initially installed 13.04 with LVM partitioning. Thinking this may be the problem, I reinstalled using ext4, but the problem persisted.

As I am contemplating upgrading my machine, perhaps any Ubunters out there who are successfully booting Ubuntu from an external usb3 drive might like to share their knowledge.

Theo

---

### Post by varunendra on 2013-03-11
> **kiwited said:**
> As I am contemplating upgrading my machine, perhaps any Ubunters out there who are successfully booting Ubuntu from an external usb3 drive might like to share their knowledge.
I don't have a usb3 device, but I'd like to offer some suggestions based on my observations.

> **kiwited said:**
> I am having problems with my usb3 seagate expansion drive not being seen by the computer on boot, but being recognised by Ubuntu once booted. The drive is seen and can be booted when plugged into USB2.
I did not test booting with the usb3 drive that I had once used (wasn't mine), but I keep booting a variety of usb2 drives (pen drives, HDD) all the time using the usb3 port. It doesn't make any difference whether I am booting from usb2 port or from usb3 as long as the OS has the driver to handle the port.

So it is evident, in my case, that the BIOS is able to initiate booting from the usb3 port, then it is upto the booting OS whether it is able or not to handle the port.

As such, I suspect it may be a limitation of BIOS not being able to boot from the usb3 port. My Asus X54C has "American Megatrends" BIOS which is what Asus always uses for its motherboards.

Does the drive even show up in BIOS when connected to the USB3 port ?

Not related to USB3, but I have noticed several bugs/incompatibilities in the Award BIOS that Gigabyte uses for its motherboards. Interestingly, those bugs/incompatibilities don't exist in some of their motherboards, even if they are older.

For example, one of the Gigabyte boards that I used for AMD FX4100 cpu couldn't even detect as bootable devices some particular brand/models of pen drives I had. While an older G31 board from them was happily booting from the same devices.

> **kiwited said:**
> 
My further query to confirm that it was "normal" that one could not boot from a USB3 drive received this:
[I][FONT=Verdana]...
Yes. USB 3.0 needs driver to work.....[/FONT]"[/I]
Based on my personal experience that I shared above, the above statement is obviously not entirely true. At least it needs a slight correction.
Yes. It does need driver; so do all other parts whether modern or legacy.
Unless the drive itself has issues *[COLOR="#696969"](quite possible, as the USB3 interface is relatively new)[/COLOR]*, it is the duty of the BIOS to present all the features an onboard device/port is capable of providing during boot up.

Accordingly, here's my suggestions -
[LIST=1]
[*]Given the fact that the same drive is able to boot on usb2 port, see if the BIOS has support to present the USB ports in 'Legacy' mode. Turn it on and try booting again.
[*]Do a hard reboot (ctrl + alt + del) if the drive is not detected in the BIOS. Some devices take more time to get ready than a typical BIOS can wait for. Some BIOS even have a setting to increase the delay before probing bootable devices. Make it 5 to 10 seconds if yours has that setting. 
[*]Also, like I keep doing all the time, try creating a live usb2 device (pen drive/memory card), plug it in the usb3 port, and see if the port even supports booting or not at all.
[/LIST]

Hope I didn't make it too long ;)

---

