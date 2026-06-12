---
title: "Nokia N80 (Symbian OS-9.1) Flash disk access"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by ruien on 2006-07-02
Hi.
I have a Nokia N80 phone and want to access its flash disk for transfering musikk, photo's etc but it doesnt show up like a removable disk like my old SE k750i does. It shows in lsusb but the disk doesnt mount. If i connect my k750 it shows up at once. No problem there.

It would be nice to access this phone from gnome instead of fire up vmware and load xp to access this thing. 

Anyone have a tip on what i need to do?

Thanks:cool:

---

### Post by reclusivemonkey on 2006-08-05
> **ruien said:**
> Hi.
I have a Nokia N80 phone and want to access its flash disk for transfering musikk, photo's etc but it doesnt show up like a removable disk like my old SE k750i does. It shows in lsusb but the disk doesnt mount. If i connect my k750 it shows up at once. No problem there.

It would be nice to access this phone from gnome instead of fire up vmware and load xp to access this thing. 

Anyone have a tip on what i need to do?

Thanks:cool:

Just got one of these myself, what a great phone. Now I've not done this myself, I need to work out how to do it, but it is possible. You need to patch the kernel as per this message;

[http://lists-archives.org/linux-usb-users/02867-possible-bug-is-usb-storage-sda-module-i-o-errors-with-nokia-n80-mass-storage-mode.html](http://lists-archives.org/linux-usb-users/02867-possible-bug-is-usb-storage-sda-module-i-o-errors-with-nokia-n80-mass-storage-mode.html)

You'll need the kernel sources and then you will have to recompile the kernel I think, and I am not sure whether it will work with the current Ubuntu kernel, but it is possible. I am going to try myself, but as I have a month old son, time is pretty sparse at the moment ;-)

---

### Post by jamaas on 2006-08-12
I have the same prob.  Can anyone tell us if this patch will find its way into subsequent ubuntu kernel versions?

Thanks

Jim

> **reclusivemonkey said:**
> Just got one of these myself, what a great phone. Now I've not done this myself, I need to work out how to do it, but it is possible. You need to patch the kernel as per this message;

[http://lists-archives.org/linux-usb-users/02867-possible-bug-is-usb-storage-sda-module-i-o-errors-with-nokia-n80-mass-storage-mode.html](http://lists-archives.org/linux-usb-users/02867-possible-bug-is-usb-storage-sda-module-i-o-errors-with-nokia-n80-mass-storage-mode.html)

You'll need the kernel sources and then you will have to recompile the kernel I think, and I am not sure whether it will work with the current Ubuntu kernel, but it is possible. I am going to try myself, but as I have a month old son, time is pretty sparse at the moment ;-)

---

### Post by adam.tropics on 2006-08-31
Any progress with this? I have my N80 in the mail at the moment!

jamaas: Hey, I went to school in Uppingham (My father was the then Chaplain of the school (Michael Smith), and I was in Meadhurst house.....blast from the past!

---

### Post by reclusivemonkey on 2006-08-31
> **adam.tropics said:**
> Any progress with this? I have my N80 in the mail at the moment!


Nope, I've not had any chance at all to work out how to apply the patch. It may be worth starting a new thread with an appeal to any kernel gurus with links to the patch. I should imagine it will eventually make it into the main kernel, but when that will appear is anyone's guess?

---

### Post by jay_cee on 2006-09-01
I've got an E70 with similar problems. I'm kind of hoping we don't have to rebuild the kernel, but can just rebuild the USB kernel module. I may fight with it some this weekend...

---

### Post by reclusivemonkey on 2006-09-03
Nothing on the kernel yet, but I did find this which people might find useful. I've installed it on my N80 and it works great on my home LAN, via my wireless router!

[http://s2putty.sourceforge.net/download.html](http://s2putty.sourceforge.net/download.html)

---

### Post by jay_cee on 2006-09-09
I was excited by this when I first saw it, but as far as I can tell:
a) No way to use it as a tunnel.
b) No support for sftp.

Is this correct? I would be very interested in a tunnel and I would kill for someway to transfer files between my phone and my PC. I'm pretty unimpressed that these s60v3 phones don't even support browsing windows shares or include an ftp client. I would happily install samba or proftp.

---

### Post by reclusivemonkey on 2006-09-10
> **jay_cee said:**
> I was excited by this when I first saw it, but as far as I can tell:
a) No way to use it as a tunnel.
b) No support for sftp.

Is this correct? I would be very interested in a tunnel and I would kill for someway to transfer files between my phone and my PC. I'm pretty unimpressed that these s60v3 phones don't even support browsing windows shares or include an ftp client. I would happily install samba or proftp.

I have no idea. Have you contacted the author? What are you wanting to tunnel?

As I have an N80, I can simply use email to transfer files between my phone and PC. That was the crucial factor for me in getting the phone; I knew with email and WiFi, I would get the connectivity I wanted with Linux, whatever was on offer software wise. Finding Putty was just a nice suprise :)

---

### Post by jay_cee on 2006-09-10
Well, I would immediately tunnel mp3 streams from my home PC's Slimserver. I would also be interested in tunneling something like VNC if I could find a good client out there.

As far as the file transfer goes - email is fine right up until you hit your email provider's size limit. I'm really interested in moving mp3s and video files, neither of which are really possible via email. 

I did a little more searching yesterday and found a java app called MobyExplorer that has a built in FTP client. Its $15, but has a 15 day trial. I'm not sure I'm going to keep it. It does work, but it is amazingly slow. It took > 5 minutes to transfer a 15MB video from my PC to my phone via WiFi. I really hope the slowness is because the ftp client is written in Java and its not the phone's radio or its TCPIP stack. I recall seeing reports of 1mbit/s throughput w/ javascript bandwidth tests which seems more reasonable to me.

The other option is to get a bluetooth dongle. I already have a Logitech Dinovo Lazer Bluetooth keyboard and mouse, but unfortunately no one know how to use it as a normal bluetooth dongle. I may try to pick up a normal  USB dongle and just hope it doesn't conflict with the dinovo...

Anyways - I'm still planning on futzing with the kernel patch, I'll post results if I have any luck.

Regards- J

---

### Post by jay_cee on 2006-09-23
Update!

I flashed my E70 firmware with the Nokia Update software this afternoon and the new E70 firmware seems to be behaving much better wrt USB Mass Storage. I was able to transfer a bunch of MP3s this afternoon with no problems. I would suspect that all of the E series will be better behaved (since they all basically got the same firmware at the same time). It would make sense that the N-series would be updated as well, but I know that they are on a different firmware release cycle (which isn't to say they haven't been fixed, I know there has been at least one N80 firmware update in the last few weeks).

Regards - J

PS - Be very cautious updating yor phone, if something goes wrong during the flash, you are SOL.

---

### Post by adam.tropics on 2006-11-18
Since updating Nokia N80 firmware, and installing Edgy,(not sure which, or if both are responsible) the N80 is seen as USB mass storage and automatically mounted. All you need do is plug in the usb cable, and select data transfer mode, and it will mount and open a nautilus window. And that's the last windows need I had, so this is great!

---

### Post by Sidster on 2006-12-04
Hi Guys.

I have a Nokia N91 and it also works well wrt "file transfer mode" on Edgy. It simply picks it up as a USB mass storage device and voila!
My only disappointment is that it doesn't seem to work when connected in "PC Suite" mode so that I can use it as a modem.

Here's the interesting bit... The "PC Suite" mode worked in dapper but the "Mass Storage" mode didn't. I could successfully use my N91 as a modem on dapper but not for transferring files. ](*,) I'm sure there's a simple enough solution to all of this but the Ubuntu team don't know about it. That's why I've decided to submit a bug report on launchpad about this issue. I'm just busy getting the correct info together and reading up on the correct way to submit bugs etc. I'll try to post the outcome here or some other relevant place on the forum.

---

### Post by 5T5 on 2007-06-04
> **ruien said:**
> Hi.
I have a Nokia N80 phone and want to access its flash disk for transfering musikk, photo's etc but it doesnt show up like a removable disk like my old SE k750i does.... Anyone have a tip on what i need to do?

You need SymSMB, its like Samba for Series 60 3rd edition phones.

---

### Post by BatPenguin on 2007-10-07
Has anyone tried this SymSMB and gotten it to work? I just bought an E70 and even though my machine detects the flash card (data transfer mode) when plugging it in, it never seems to transfer anything to it, even when I copy files to the card and then unmount it before unplugging the USB cable. The phone warns me about unplugging and, it seems like the files are not transffered, no matter how long I wait after unmounting. So I was wondering if the SymSMB would work better...but I don't feel like buying it without first hearing some opinions. I'm using Edgy by the way.

---

### Post by duxxyuk on 2008-02-14
I agree with Sidster here.
Having had an N80 and now an N95 I found it best to simply use the cable that comes with the phone and mount it as USB Storage. (I know this is slower but hey... it works)

I found that cards bigger than 1gb  were causing problems. On the N80 I had one card of 2GB and one of 128 mb. The 128 mb card worked fine (in the usb card reader via the SD adapter) however the 2gb card refused to mount. The same appears to be the case with the Micro SD cards that the N95 takes as well. 32gb Micro SD works fine but the 2gb card I have doesn't mount.
I tried all this with freshly formatted cards that had no password whatsoever.

As for unmounting the card / phone I too don't see the "<device> can now be safely unplugged" popup. I suggest that you open a terminal and issue the command SYNC. This ensures that all data is copied and the interface is in an idle state. Then go about unmounting and unplugging the phone. I've not had any problems doing it this way.

One other thing, I agree that it would be nice to have access to the modem and the phone data directories at the same time (via PC Suite mode) but alas this appears not to be the case yet. In this mode I think that data is transferred using some sort of OBEX protocol. I had a quick gander for Nokia USB OBEX and I fell on this page : [http://dburr.veritel.com.au/nokia/](http://dburr.veritel.com.au/nokia/)
If anyone has a play, can they put their thoughts back in here please ? (although I suspect that the mods might grumble if we deviate too far from simple mass storage)

Ho! wait: looky over here : [http://ubuntuforums.org/showthread.php?t=211810&highlight=Nokia+Obex](http://ubuntuforums.org/showthread.php?t=211810&highlight=Nokia+Obex) \\:D/

---

