---
title: "HP Mini 110-3000 netbook"
date: 2013-03-13
forum: Hardware
---

### Post by Linux4Anna on 2013-03-13
Greetings,

I'm a mac user (since 1984) and, as I despise windows system and since a friend gave me an HP Mini 110-3000 netbook, few days ago I tried a linux system on it.
I fell in love.

Unfortunately, I then did something which I should not have done: since the info said the drive space available was far less than the drive actually is, I deleted the system recovery partition and the windows 7 system, thinking I'd then reboot and reinstall linux from scratch.

I've been struggling since (3 days now), as no matter what usb flash I use to boot the computer, I get this "No bootable device -- insert boot disc and press any key" error. 

I found this thread: [http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g-Windows-8-and-Software/No-bootable-device-insert-boot-disc-and-press-any-key-error/td-p/151244](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g-Windows-8-and-Software/No-bootable-device-insert-boot-disc-and-press-any-key-error/td-p/151244) and tried everything there. Understanding that this was not a usb key issue (the other masterboot fat32 formated install images restored on usb key and made with my PPC G5 OS 10.4.11 DID previously work on the netbook), I went to get a new drive today.

Come back home, change the drive... same error.

I had also bought a usb enclosure to put in the old drive and connect it to mac via usb port to visually see what was happening in the drive. No use... the whole content left is written in chinese or something. All folders are. So I can't understand squat.

Setting up an HD for mac is so simple. It's like ABC.
But a PC one ?

BIOS and drivers and... such... are to me just as the chinese folder naming are. 
Also as I read, it seems that the error I get from the netboot would indicate that there is something wrong with the "MBR" ? what in the world is this ?

Pain, pain, pain.

Now I wished to install ubuntu onto this drive/netbook.

How can I, with the components I have, make this work ?

I dont care about the HP stuff that was in there, nor do I care for windows stuff.

- Is it absolutely necessary that there is a windows system installed for ubuntu to be installed ?
- How is it that PC drives and computers needs BIOS and MBR and Drivers and such... I cant install those on the HD as they are exe files and I'm on a mac.. all I could do is restore an image on a partition.. is there some type of GNU image that could help me setup this HD so it works on the netbook ? 

I just need this to work and as simply as possible.
I have computer work to do on the netbook that is due for friday, and I already spent 3 days on this issue..

I would very much appreciate any help on setting up this drive and then installing ubuntu on it.

Thank you!

Anna

---

### Post by Mark Phelps on 2013-03-13
You do not need an OS running on a Windows PC in order to install Ubuntu to it, in fact, having one is only a burden in that case.

What you need to do is boot from the Ubuntu installation medium -- optical disk or USB stick.  When you start through the installation, there is generally an option to use the entire disk -- choose that.  

When you're done installing, remove the installation medium reboot, and you should get to an Ubuntu desktop.

---

### Post by Linux4Anna on 2013-03-13
Thank you Mark, that very well settles one part of the issue !

However that MBR error thing prevents the computer from booting the ubuntu install key... So I figure that BIOS and MBR and drivers and such ARE something that firstly needs to be installed on any PC HD before installing a system... is it not so ?

---

### Post by steeldriver on 2013-03-13
The BIOS would typically be in ROM and completely separate from what's on either the internal hard drive or the install medium

The MBR required to boot the installer will be on the install medium (CDROM / DVD /USB stick). If the computer is complaining about a missing MBR then either (1) it's not even trying to boot from the install medium - e.g. the boot order that's set in the BIOS needs to be changed to 'find' the CD/DVD/USB instead of looking on the HDD for the (now deleted) original OS; or (2) it's trying, but the install medium is faulty (for example it's important to 'burn' the CD as a bootable disk using appropriate software rather than simply copy the ISO file on to it)

Hope this helps

---

### Post by Linux4Anna on 2013-03-13
Indeed, very welcome information steeldriver.

About 1-, no matter how the BIOS is set, and even if the stick does show up in the list and is selected on top of being first in the boot list, it still wont boot from it. Also setting the BIOS settings back to default didnt change anything. You mention that BIOS is in ROM.. can the ROM itself be reset  somehow ?

About 2-, there is no optical drive in the HP Mini, so I am using usb keys. Those are formated as Masterboot fat32 ms-dos system in the mac and then the install image is restored onto it (restored, not copied). It did previously work as I had installed that linux system this way before the screw up.. but since then it's not..

Also I did use the BIOS to run all the possible test with it since it's now all I have access to with this computer, and all results were fine..

---

