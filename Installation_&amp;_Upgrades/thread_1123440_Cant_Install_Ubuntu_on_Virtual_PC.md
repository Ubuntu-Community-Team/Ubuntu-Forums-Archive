---
title: "Cant Install Ubuntu on Virtual PC"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by Fonzie2010 on 2009-04-12
Hi guys, I am new to the Ubuntu OS and i would very much like to try it out.

I downloaded an old PPC of Ubuntu 8.10, it was an alternate CD. I downloaded it, burned it to a disc, (kept the Iso). I opened Virtual PC and selected linux, UNIX, Unspecified, no matter what i choose i just doesnt seem to go.

all it says when the VPC starts is this.

Reboot and Select Proper Boot Device
Or Insert boot media in the selected Boot Device.

Yes I have put the CD in, what can i do?

---

### Post by 0cton on 2009-04-12
I am not familiar with Virtual PC but it means the virtual CD-rom witch can be linked to the real one
look into the options on media and stuff (It has a virtual cdrom there witch can be mounted or be related to the "real" cdrom)

---

### Post by Fonzie2010 on 2009-04-12
I start up VPC, Select Linux is my OS, it starts up and gives me that message.

I select the Iso, Nothing Happens, just gives me the message again (and yes i clicked reset computer)

I selected capture disc, and then reset, nothing happened.

I just made a new one with the disc inserted, and still nothing happened.

---

### Post by kpatz on 2009-04-12
Check the boot order in the VPC's settings.  Make sure it boots from the CD before the hard drive.

---

### Post by Fonzie2010 on 2009-04-12
> **kpatz said:**
> Check the boot order in the VPC's settings.  Make sure it boots from the CD before the hard drive.


How do i do that?

---

### Post by kpatz on 2009-04-13
Select the virtual machine and click Settings.  Then go to the Advanced tab.  The boot order is at the top.

[attach]109672[/attach]

Change it so the CD/DVD drive is listed before the hard disk.

Also, make sure the ISO is mounted (from the CD/DVD option on the left side of the settings dialog).

[attach]109673[/attach]

---

### Post by Aubergines on 2009-04-13
If you're struggling to solve this you can install [virtualbox](http://www.virtualbox.org/), it's free open source software and is as good as any other similar targeted virtualisation product around if not better. Not really a solution on how to get it working on virtual PC but you'll find many more people who can help you if you run into problems with virtualbox

---

### Post by Fonzie2010 on 2009-04-13
> **kpatz said:**
> Select the virtual machine and click Settings.  Then go to the Advanced tab.  The boot order is at the top.

[attach]109672[/attach]

Change it so the CD/DVD drive is listed before the hard disk.

Also, make sure the ISO is mounted (from the CD/DVD option on the left side of the settings dialog).

[attach]109673[/attach]

Im on a mac, and VPC 7 does not have those options.


And I am on Mac OS X 10.3 Panthers running a g4 PPC chip, so i cant use Virtual Box.

---

