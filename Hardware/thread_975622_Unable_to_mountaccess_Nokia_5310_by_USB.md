---
title: "Unable to mount/access Nokia 5310 by USB"
date: 2008-11-08
forum: Hardware
---

### Post by Krank on 2008-11-08
I recently got myself a spanking new Nokia 5310 (xpressmusic) mobile phone, which uses a MicroSD card and is connectable through a Micro-USB cable.

I dualboot Intrepid and Windows XP (for those pesky gaming needs), and run an Asus EEE 900 on the side dualbooting EEEUbuntu and Windows XP.

In XP on both machines, I'm very much able to see the phone as a regular USB mass storage device. No funny business.

In EEEUbuntu, the phone is instantly recognized and mounted as an USB mass storage device. Again, no funny business.


However, my Intrepid install refuses to play along. I get an incredibly annoying error message, as follows:

> 
**Unable to mount Nokia Mobile Phones Nokia 5310 XpressMusic.**
Failed to get folder list: -1: Unspecified error


This error message only comes up the first time I try to plug the device in after a reboot, irrelevant of user login etc. In kde-hal-device-manager (which i installed because I could not find anything similar for Gnome) I can see the phone just fine.

I have purged and reinstalled HAL (and all associated packages). No change. Since the DBUS package is tied up in all kinds of packages I'd rather not have to reinstall later, I've only tried aptitude reinstall:ing it. No change.

This is incredibly annoying. According to google, noone has EVER gotten the same error message I got. Not one hit. Not only is it annoying, but it's kind of ridiculous.

In any case, I'm starting to wonder if it could have anything to do with DBUS. I may have managed to fsck up some config file or another. I have no idea which one or if I'm even on the right track.


Any ideas? Please? Pretty please?

---

### Post by razorxpress on 2008-11-10
You are not alone. Be careful with intrepid ibex with you Xpress Music? Because i was brave enough to shot it down when i tried to unmount the card from ubuntu ibex and never got boot back. So i had to send it for a good amount(:( my money) repair. I had to reinstall the os(in short flexing). Be careful. I did not know intrepid ibex has problems until recently. After flexing when i tried to mount Nokia on ibex, it listed on the usb (lsusb), but did not mount. So i thought of giving a try with live boot cd of hardy (8.04) and it worked. So ibex has some problems. Even if your phone mounts on ibex, be careful

---

### Post by razorxpress on 2008-11-10
Solved (by jmaxx). You may visit the 3rd page for his post. The post says 

1- Download these two files

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)

2- Backup 60-persistent-storage.rules and 40-permissions.rules of /etc/udev/rules.d/


3- rename 65-persistent-storage.rules to 60-persistent-storage.rules

4- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/


Thanks jmaxx. It worked for me in 8.10. Hope it works for all.

---

### Post by TyraMisoux on 2008-11-12
me too! Nokia 5610 XpressMusic.
I managed to mount (manual mode-select on the phone, then press abort after connecting) as memorydevice and I am able to read from the phone as well as create folders but as soon as I try to write a file to the phone's flash memory there is "-1 unknown error".

---

### Post by jmaxx on 2008-11-12
i have the same problem. I can't mount my 5310, only in modo photographie i can download my pictures. Any solution??

---

### Post by Krank on 2008-11-12
No solutions yet.

Right now, I use either a cheap bluetooth adapter (slow, but works) or a microSD-capable card reader (cumbersome, but works and is faster).

I've even contemplated switching back to Hardy by reinstalling just to get this to work.

Bah.

---

### Post by TyraMisoux on 2008-11-13
Yes, I also use an external cardreader to maintain my phone's music-archive (I use it as an mp3/aac player daily).
The access is faster but unfortunately it takes ages after put the flash back to the phone to rebuild the library.
I'd really appreciate to have that issue fixed.

---

### Post by Krank on 2008-11-13
Yeah, like I said, cumbersome.

My solution for the moment is to cram one album of each of the artists I usually feel like listening to onto the MicroSD, and then not touching anything. Pros: Not spending a lot of time updating the database or transfering mp3's. Con: Same bloody albums every bloody day...

Seriously, has anyone filed a bug report on this? If not, I think I will, despite the fact that I don't have any idea whatsoever which piece of software/driver is responsible.

Quite probably, the peoblem is completely unknown to people upstream - if it only affects one specific type of phone...

---

### Post by t1010011 on 2008-11-14
> **jmaxx** I can't mount my 5310, only in modo photographie i can download my pictures..

Exactly... Same problem here... Also when someone comes with a good idea on how to solve this, i'd appreciate some help on syncing with Rhythmbox...

---

### Post by skiold on 2008-11-14
Hi, exactly the same trouble here. I have a Nokia 3500c.

---

### Post by skiold on 2008-11-15
I did a test with my 8.04 live CD and I can confirm there is no problem with the USB connection, Hardy recognizes the phone and the internal micro SD memory. Definitely it's a bug in 8.10.

---

### Post by Krank on 2008-11-15
> **skiold said:**
> I did a test with my 8.04 live CD and I can confirm there is no problem with the USB connection, Hardy recognizes the phone and the internal micro SD memory. Definitely it's a bug in 8.10.


Has anyone tried a 8.10 livecd?

---

### Post by mac.ryan on 2008-11-15
The problem also exists for 5300.

---

### Post by skiold on 2008-11-15
Yes, I tried the 8.10 live cd, and the trouble persist.

---

### Post by matjazs on 2008-11-16
I get the same error message with Canon PowerShot S3 IS digital camera:

Unable to mount Canon, Inc. Canon Digital Camera
Failed to get folder list: -1: Unspecified error

---

### Post by Krank on 2008-11-16
This is good news, and bad...

Bad, because it seems something major is broken in Intropid - and because it causes a lot of trouble for us.

Good, because I don't think any devs would spend time investigating something minor. If the problem involves not just one phone model but serveral (and at least one camera as well), then I believe there's a bigger chance of someone actually taking the time to investigate.

Anyone posted a bug report on the issue?

---

### Post by skiold on 2008-11-16
Not yet, Could you post this bug? I don't know how to do it. Hope to find a solution as soon as possible.
Greetings.

---

### Post by ConfidentiaL on 2008-11-17
same problem here with 5610...

---

### Post by Krank on 2008-11-18
Submitted a bug here:

[https://bugs.launchpad.net/ubuntu/+bug/299484](https://bugs.launchpad.net/ubuntu/+bug/299484)

Let's see if anyone cares.

---

### Post by davidlb on 2008-11-18
Krank, please check your bug report and update.

Most of the Nokia phones are reporting one more sector on the microSD card than are really there, and others are giving other problems in addition to this. Even some Motorola phones are having this problem, but they seem to have been caught early on in the 2.6.27 dev process.

Edit: So far the only way to fix this is with a kernel patch. But from what I have learned about it a firmware update from Nokia might also be able to fix it.

---

### Post by peacewithall on 2008-11-19
Having the same problem with a Sony Ericsson K310i. Very frustrating, cannot access (and so cannot download) anything like photos, or video's taken with the phone, with intrepid via USB connection.

---

### Post by Yezinki on 2008-11-20
You would need windows for that access.

---

### Post by peacewithall on 2008-11-22
Well I could access these folders before , with Hardy. Intrepid seems to be a hardware nightmare compared to the last few versions.
Unfortunately, yes I'm back using Vista, at least until the pulseaudio problems get fixed, hopefully soon.....sighs :( .

---

### Post by jmaxx on 2008-11-22
I discovered this possible solution 

1- Download this two files

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)


2- rename 65-persistent-storage.rules to 60-persistent-storage.rules

3- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/

is very important to make backup of the files...
I am using hardy And I have not tried this solution

bye

---

### Post by peacewithall on 2008-11-22
> **jmaxx said:**
> I discovered this possible solution 

1- Download this two files

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)


2- rename 65-persistent-storage.rules to 60-persistent-storage.rules

3- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/

is very important to make backup of the files...
I am using hardy And I have not tried this solution

bye

jmaxx !!....guess what, u fixed it !!.

I just choose folder mode from menu and up pops my phone folder complete with sub-folders !.

Thanks so much for this :)

---

### Post by cevatceyhun on 2008-11-23
Works for me too!


PS: In 8.10 my phone was working perfectly but suddenly it stopeed. I don't know why but I didn't install any software or didn't change configuration.

---

### Post by poing on 2008-11-24
> **jmaxx said:**
> I discovered this possible solution 

1- Download this two files

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)


2- rename 65-persistent-storage.rules to 60-persistent-storage.rules

3- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/

is very important to make backup of the files...
I am using hardy And I have not tried this solution

bye
Works for me. Thank you!

---

### Post by t1010011 on 2008-11-28
Tried the solution above and still not working for me... 

I don't know if it helps, but a heard another guy talking that a fix could come with a kernel update, well today, for me, ubuntu uptaded to the kernel to 2.6.27-9-generic, and little has changed, it opens as Nokia Mobile Phones Nokia 5310 XpressMusic, but as a camera, and I can't write anything into it...

anybody else?

---

### Post by Krank on 2008-11-28
The solution above does nothing for me. Thanks for the tip though.


I'm currently running kernel 2.6.27-10, and nope, it doesn't work. In Media Suite mode, I can get the phone to show up, but it canät be properly managed or anything. I still want good old regular mass storage drive access.


On a brighter note, VirtualBox recently added support for Nokia phones in Linux hosts, so if you don't mind running a virtual machine with windows 2000/XP every time you want to access your phone's memory, it's a nice solution. Me, I'd like a beter solution, but this one will have to do for the moment. It lets me make semi-regular backups and I can use Nokias own software etc. Not that the software is all that great, but compared to the weird interfaces offered by the Linux alternatives... it's erh, slightly less than perfect but still preferrable. Why are so many interfaces in the Ubuntu world designed by people who know a lot about programming in general but nothing about interface design? How do they manage to create interfaces that look cluttered and still lack features? Bah.

Anyways, I will survive, at least for the time being. It's a pain to boot a virtual machine every time I want to backup etc, but what the hey...

---

### Post by zachalekos on 2008-11-29
> **jmaxx said:**
> I discovered this possible solution 

1- Download this two files

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)


2- rename 65-persistent-storage.rules to 60-persistent-storage.rules

3- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/

is very important to make backup of the files...
I am using hardy And I have not tried this solution

bye

This fixed the issue with Sony Ericsson w980

---

### Post by Protezis on 2008-11-29
> **jmaxx said:**
> I discovered this possible solution 

1- Download this two files

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)


2- rename 65-persistent-storage.rules to 60-persistent-storage.rules

3- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/

is very important to make backup of the files...
I am using hardy And I have not tried this solution

bye

This is working for me, but **I had to format the memory card** with phone. Thank you!

---

### Post by Huss on 2008-11-30
The new rules worked for me - Nokia 6280.

---

### Post by skiold on 2008-12-01
I'm in the same situation as you mention Krank. Jmaxx solution does nothing for me neither. Maybe the next kernel update could fix this trouble.
> **Krank said:**
> The solution above does nothing for me. Thanks for the tip though.


I'm currently running kernel 2.6.27-10, and nope, it doesn't work. In Media Suite mode, I can get the phone to show up, but it canät be properly managed or anything. I still want good old regular mass storage drive access.


On a brighter note, VirtualBox recently added support for Nokia phones in Linux hosts, so if you don't mind running a virtual machine with windows 2000/XP every time you want to access your phone's memory, it's a nice solution. Me, I'd like a beter solution, but this one will have to do for the moment. It lets me make semi-regular backups and I can use Nokias own software etc. Not that the software is all that great, but compared to the weird interfaces offered by the Linux alternatives... it's erh, slightly less than perfect but still preferrable. Why are so many interfaces in the Ubuntu world designed by people who know a lot about programming in general but nothing about interface design? How do they manage to create interfaces that look cluttered and still lack features? Bah.

Anyways, I will survive, at least for the time being. It's a pain to boot a virtual machine every time I want to backup etc, but what the hey...

> **jmaxx said:**
> I discovered this possible solution 

1- Download this two files

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)


2- rename 65-persistent-storage.rules to 60-persistent-storage.rules

3- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/

is very important to make backup of the files...
I am using hardy And I have not tried this solution

bye

---

### Post by 3dxtrip on 2008-12-08
> **jmaxx said:**
> I discovered this possible solution 

1- Download this two files

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)


2- rename 65-persistent-storage.rules to 60-persistent-storage.rules

3- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/

is very important to make backup of the files...
I am using hardy And I have not tried this solution

bye

Works fine on Nokia 3500c

Many thanks

---

### Post by t1010011 on 2008-12-24
well, there is certainly something going on in here:

[http://www.nabble.com/-PATCH--SRU-Bug--287701--intrepid--USB-mass-storage-doesn%27t-mount-automatically-with-nokia-5610-express-td20845782.html]("http://www.nabble.com/-PATCH--SRU-Bug--287701--intrepid--USB-mass-storage-doesn%27t-mount-automatically-with-nokia-5610-express-td20845782.html")

but i can't understand....

maybe they are plaining a kernel patch??

---

### Post by joeycbulk on 2009-03-05
> **jmaxx said:**
> I discovered this possible solution 

1- Download this two files

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)


2- rename 65-persistent-storage.rules to 60-persistent-storage.rules

3- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/

is very important to make backup of the files...
I am using hardy And I have not tried this solution

bye

Hey Thanks! it fixed the problem

---

### Post by lilj26 on 2009-04-17
> **Krank said:**
> I recently got myself a spanking new Nokia 5310 (xpressmusic) mobile phone, which uses a MicroSD card and is connectable through a Micro-USB cable.

I dualboot Intrepid and Windows XP (for those pesky gaming needs), and run an Asus EEE 900 on the side dualbooting EEEUbuntu and Windows XP.

In XP on both machines, I'm very much able to see the phone as a regular USB mass storage device. No funny business.

In EEEUbuntu, the phone is instantly recognized and mounted as an USB mass storage device. Again, no funny business.


However, my Intrepid install refuses to play along. I get an incredibly annoying error message, as follows:



This error message only comes up the first time I try to plug the device in after a reboot, irrelevant of user login etc. In kde-hal-device-manager (which i installed because I could not find anything similar for Gnome) I can see the phone just fine.

I have purged and reinstalled HAL (and all associated packages). No change. Since the DBUS package is tied up in all kinds of packages I'd rather not have to reinstall later, I've only tried aptitude reinstall:ing it. No change.

This is incredibly annoying. According to google, noone has EVER gotten the same error message I got. Not one hit. Not only is it annoying, but it's kind of ridiculous.

In any case, I'm starting to wonder if it could have anything to do with DBUS. I may have managed to fsck up some config file or another. I have no idea which one or if I'm even on the right track.


Any ideas? Please? Pretty please?

Sorry I can't exactly help you out! You are not alone with those pesky error messages when try to do the same! i have to take my memory card out of my phone and put it in a usb adapter to add mp3 files or any other files for that matter! i can only create a new folder when i attach my phone to my computer! im really not liking linux for reasons like this! i am also having difficulties catching a non encrypted wireless internet connection with my belkin wireless usb adapter! i had no problems with any of this crap when i was running windows xp! i can cath signals but they are all locked with an encryption key or passphrase! any suggestions for my problem? Do i need to just go out and purchase a wireless usb device with  a  wider  signal  range ? Any  help  would be wonderfull!

---

### Post by lilj26 on 2009-04-17
> **t1010011 said:**
> Tried the solution above and still not working for me... 

I don't know if it helps, but a heard another guy talking that a fix could come with a kernel update, well today, for me, ubuntu uptaded to the kernel to 2.6.27-9-generic, and little has changed, it opens as Nokia Mobile Phones Nokia 5310 XpressMusic, but as a camera, and I can't write anything into it...

anybody else?
The only solution without downloading anything was to just get ahold of a usb adapter that fits the micro sd card in it!  
Sorry I can't exactly help you out! You are not alone with those pesky error messages when try to do the same! i have to take my memory card out of my phone and put it in a usb adapter to add mp3 files or any other files for that matter! i can only create a new folder when i attach my phone to my computer! im really not liking linux for reasons like this! i am also having difficulties catching a non encrypted wireless internet connection with my belkin wireless usb adapter! i had no problems with any of this crap when i was running windows xp! i can cath signals but they are all locked with an encryption key or passphrase! any suggestions for my problem? Do i need to just go out and purchase a wireless usb device with a wider signal range ? Any help would be wonderfull!

---

### Post by maverick340 on 2009-04-17
> **jmaxx said:**
> I discovered this possible solution 

1- Download this two files

[http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar](http://www.esnips.com/doc/2ca0b833-cae6-4522-81ff-d6d0439ddf70/65-persistent-storage.rules.tar)

[http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar](http://www.esnips.com/doc/79f10bc4-bb62-439c-995d-398a7b9ac210/40-permissions.rules.tar)


2- rename 65-persistent-storage.rules to 60-persistent-storage.rules

3- copy 60-persistent-storage.rules and
40-permissions.rules in /etc/udev/rules.d/

is very important to make backup of the files...
I am using hardy And I have not tried this solution

bye
Awesome, My Sony Ericsson t700(new phone) worked on 8.10 before but suddenly stopped working. This helped, thanks a ton ( i was really upset !)
Shouldn't someone file a bug or something about this problem ? 
Okay I'll do it (if its already not there)

---

### Post by albertz on 2009-05-12
Bump. Is there already a bug report? I don't like to mess around in system files (where they probably got overriden anyway at the next update). Can't we get this fix as a proper Ubuntu update?

---

### Post by Jazzinghen on 2009-05-13
> **zachalekos said:**
> This fixed the issue with Sony Ericsson w980

Which of the four modes should I choose to make it work? Because with the files the Mobile Phone is recognized and mounted, but then all I can see are the Folders, inside there isn't any file...

---

### Post by Tectuktitlay on 2009-08-19
Thanks JMaxx!

Just reporting that your fix works for my Sony-Ericsson W980 and W595.

Kind regards, Tec

---

### Post by b0uncyfr0 on 2009-09-23
Can someone please re-upload those two files. The links are expired. I just bought a W980 and im hoping this might get storage mode working.

Another way ive found is through virtualbox but its just too long. Any help would be greatly appreciated on this.

---

### Post by Tectuktitlay on 2009-11-05
Here they are.

---

### Post by Tectuktitlay on 2009-11-05
By they way, they don't work on Karmic Koala, unfortunately. I hope someone can fix this.

Grtz,

Tec

---

