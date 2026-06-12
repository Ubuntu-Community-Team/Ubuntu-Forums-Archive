---
title: "Mounting my USB flashdrive"
date: 2005-01-26
forum: Hardware &amp; Laptops
---

### Post by taken on 2005-01-26
Hello, all

I've just installed ubuntu and have a ton of problems. Hopefully you guys can help me sort them out.

First up.

My flashdrive is detected by Ubuntu but I don't know how to mount it.

Any clues?

---

### Post by gheorghe_pop on 2005-01-26
First of all you should set yourself as a member of other groups like cdrom,games,floppy,usb if it exists etc.
Choose computer and then double click on the usb drive.

---

### Post by taken on 2005-01-26
And how do I setup myself as a member of those groups?

Incidentally, are there any "getting started" documents that are already installed? If the answer is yes, then how d I acess them, I have been looking for such and haven't found them.

Some reading would probably lead to a lot less posting on real newbie issues by me.

---

### Post by gheorghe_pop on 2005-01-26
You should check the ubuntu starter guide ther is lot of stuf that it might help you.
[http://ubuntuguide.org/](http://ubuntuguide.org/) 
How to set yourself member of that groups:
The simple way it to check your menus for 'Users and Groups'.I think it's under Computer->System...not shure because i'm not aat my pc right now.

---

### Post by taken on 2005-01-26
I am reading the guide but it's mostly "how do I solve X" rather than a starter's guide and I haven't even reached those problems yet. :)

Ok, back to my missing flash drive.

I do have a group called cdrom but no groups called usb. So I couldn't add myself to that. There was a group called "messagebus", I added myself there but it didn't help.

It is not detected in the Computer>Drives section but it is detected in the system configuration, section. (The info there changes automatically as I add or remove the flashdrive but I never see an icon in the drives section or on the desktop.)

---

### Post by taken on 2005-01-27
Somebody help me please!

I really need that stuff. :(

---

### Post by martijntje on 2005-01-27
Did google stopped working for you? There are many tutorials out there...

Anyways, a quick overview:
- plugin your usbdrive
- sudo mkdir /media/usbdrive
- mount /dev/sda1 /media/usbdrive

Provide your password as requested. You should now have mounted your usb drive.
If this worked, you can add it to your fstab if you like. Good luck.

---

### Post by taken on 2005-01-27
I had tried that command already, but it tells me "you must specify filetype".

When I type

(sudo)  mount -t vfat /dev/sda1 /media/usb

It gives me some error, (sorry, I didn't write it down and no 'net on my Ubuntu yet) something about a wrong filesytem.

I used man mount and then tried some of the more likely filesystems that were listed in the "-t" option but it never worked.

When I tried booting with the flashdrive already in place, it gave me a bunch of errors in the likes of
I/0 Buffer error on /dev/sda1 (words of error are from memory.) and then proceeded to boot normally.

I am googling around, I am just not finding the desired answers. :D

---

### Post by gogodidi on 2005-01-27
that should actually work...

did you actually use (sudo)?

with the parenthesis?

cos that isn't really.... smart....

---

### Post by taken on 2005-01-27
No, I didn't use parenthesis around sudo.

That was there to say that I tried with and without sudo, failing in both cases. 

What I had typed was:

"sudo mount -t vfat /dev/sda1 /media/usb"

and no, it didn't work.

---

### Post by martijntje on 2005-01-27
Maybe your usb disc is formatted differently. Have you tried
```
sudo mount -t auto /dev/sda1 /media/usb
```

And did you create the subdirectory usb in your media directory?

---

### Post by taken on 2005-01-27
Yes, the usb folder exists inside the /media subdirectory.

Yes, I did try the "-t auto" option and the error that I got was exactly the same as the one as -t vfat, which is:

mount:
              wrong fstype, bad option, bad superblock, on /dev/sda1 or too many mounted systems.
(aren't  you trying to mount an extended partion, instead of some logical partion inside?)

Hopefully this error will help you guys figure out what exactly am I doing wrong.
----------
As you guys have probably figured out, I'm a total newbie who is just messing around with stuff and reading up on commands and trying them out... Here is a related problem that I'm having. I tried to redirect the output of the mount command to a file, like so:

"sudo mount -t vfat /dev/sda1 /media/usb > file1.txt"

(without the quotations)

It creates an empty file called file1.txt which doesn't show error (typed above). Is the tutorial wrong, or am I typing something wrong?

---

### Post by taken on 2005-01-30
I'm still unable to mount my USB flashdrive.

So I used Windows 98, where it got detected without a problem! (It didn't recognize its brand name) and then transferred the files.

So, I need Windows 98 to move my files back and forth. And Windows 98 to use the net.....

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=taken]I'm still unable to mount my USB flashdrive.

So I used Windows 98, where it got detected without a problem! (It didn't recognize its brand name) and then transferred the files.

So, I need Windows 98 to move my files back and forth. And Windows 98 to use the net.....[/QUOTE]

Hey, use what works...

---

### Post by taken on 2005-02-08
That's a work around.
I'd prefer a solution.

---

### Post by martijntje on 2005-02-08
There should be a "Removable Media" item in the Gnome Menu. I believe it's in one of the Configuration menu's. In there should be an option to run scripts for new devices.

It did the trick for me. I plugged in my MP3 player, and an icon appeared on my desktop, and a nautilus window popped up with the contents of it.

---

