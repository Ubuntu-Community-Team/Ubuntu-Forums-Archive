---
title: "Booting Ubuntu 9.10 from USB"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by imtiazu on 2009-11-10
Hi I have followed all the directions from Ubuntus' website (and many others) on installing and booting the netbook remix version from USB.

The first attempt practically trashed my Vista installation and i had to run a repair to get it back.

I was under the impression that Ubuntu could can be booted and run from a USB with no affect to the PCs HDD.
I have built windows pc for years and am somewhat stumped by how to get this up and running!??!

I am greeted with a number of options e.g. Run Ubuntu Persistance, Install Ubuntu etc...

Neither of them appear to install the OS, and eventually just crash out with errors.

All I want to do is have the OS installed and run solely from the USB! I want to be able to take the USB with me and boot it on other netbooks. Can someone give me any suggestions on how to get this up and running please?

Thanks

---

### Post by wilee-nilee on 2009-11-10
I read your post incorrectly at first. So did you try unetbootin.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
I am not sure if this program allows a extra space for updating and adding programs on top of the ISO download but it probably does.

I wonder if you have a corrupted download, if you could tell us what you have done so far and what program you used to load the thumbit will help us help you.

---

### Post by imtiazu on 2009-11-10
"Have you checked the downloads md5 sum"
YES

"and did you do the check at the boot window where you see try without installing, install, etc"
NEVER SAW AN OPTION TO TRY, HOWEVER THIS WILL NOT ACHIEVE MY GOAL OF INSTALLING IT TO A USB, RIGHT?


"Then did you run it live to see if it works."
CAN I RUN IT LIVE IF ITS NOT SETUP?
I WAS EXPECTING, THAT ONCE THE USB WAS CREATED FROM THE ISO, THAT THE PRODUCT WOULD JUST BOOT FROM USB?

Thanks for your comments, however, do they ultimately lead me to the point of running the OS from the USB only? I.e. Is this even possible??? Simply having the OS (and any saved work in the future) saved and run from my USB stick so that it's portable and bootable from any other netbook??

---

### Post by wilee-nilee on 2009-11-10
> **imtiazu said:**
> "Have you checked the downloads md5 sum"
YES

"and did you do the check at the boot window where you see try without installing, install, etc"
NEVER SAW AN OPTION TO TRY, HOWEVER THIS WILL NOT ACHIEVE MY GOAL OF INSTALLING IT TO A USB, RIGHT?


"Then did you run it live to see if it works."
CAN I RUN IT LIVE IF ITS NOT SETUP?
I WAS EXPECTING, THAT ONCE THE USB WAS CREATED FROM THE ISO, THAT THE PRODUCT WOULD JUST BOOT FROM USB?

Thanks for your comments, however, do they ultimately lead me to the point of running the OS from the USB only? I.e. Is this even possible??? Simply having the OS (and any saved work in the future) saved and run from my USB stick so that it's portable and bootable from any other netbook??

Read my edit and if you want help you will have to settle down, none of us are paid for this we do it because at least myself people have helped me.

---

### Post by imtiazu on 2009-11-10
@ wilee-nilee

Yup, I downloaded 9.10 netbook remix ISO and used a utility to write the ISO to my USB.
Once it was written, I simply ordered my boot process in the bios and had my netbook boot from the USB.

It provided me with a list of options and when i hit INSTALL, it sat with the logo glowing for a few minutes and after it just came up with a few messages (not errors) about disk file paths and then just a prompt, as if i was in linux, and thus could use linux syntax etc...

Thats all i did.. for now :)

---

### Post by wilee-nilee on 2009-11-10
> **imtiazu said:**
> @ wilee-nilee

Yup, I downloaded 9.10 netbook remix ISO and used a utility to write the ISO to my USB.
Once it was written, I simply ordered my boot process in the bios and had my netbook boot from the USB.

It provided me with a list of options and when i hit INSTALL, it sat with the logo glowing for a few minutes and after it just came up with a few messages (not errors) about disk file paths and then just a prompt, as if i was in linux, and thus could use linux syntax etc...

Thats all i did.. for now :)

Hitting install will install it to your computer that is not what you want am I correct. You want a USB that can be booted on any computer, and what utility did you use. You want the try without install if I understand your goals.

---

### Post by wilee-nilee on 2009-11-10
If you use netbootin it will install to the usb the ISO for booting live I think your thinking that the install prompt from the USB boot is installing to the USB when if you use the right ISO to USB loader that is the install you want. Hitting install from the USB boot up will install to your computer. 

And yes I can see why that would screw up Vista, does this make more sense and am I correct in what your goals are a bootable live USB for use on any computer that can boot from a USB.

---

### Post by imtiazu on 2009-11-10
Ye, i guessed i'd gone for the wrong option when I first trashed my netbook!! :S

As for the utility, I initially tried the w32 image writer, but then realised that it only used .img files, not .iso.
I then came across another tool [http://www.pendrivelinux.com/downloads/u910/USB-Installer-U910.exe](http://www.pendrivelinux.com/downloads/u910/USB-Installer-U910.exe)
which created the USB boot disk.

Yes, correct, I want to use the OS from the USB only. Is this possible with the boot from USB or do I need to install the OS to my laptop HDD?

thanks!

---

### Post by wilee-nilee on 2009-11-10
> **imtiazu said:**
> Ye, i guessed i'd gone for the wrong option when I first trashed my netbook!! :S

As for the utility, I initially tried the w32 image writer, but then realised that it only used .img files, not .iso.
I then came across another tool [http://www.pendrivelinux.com/downloads/u910/USB-Installer-U910.exe](http://www.pendrivelinux.com/downloads/u910/USB-Installer-U910.exe)
which created the USB boot disk.

Yes, correct, I want to use the OS from the USB only. Is this possible with the boot from USB or do I need to install the OS to my laptop HDD?

thanks!

You just load the ISO in to the pendrive with the link you have and just choose the option of trying without installing from the USB boot this will give you a live running Ubuntu. I suspect that this pendrive link will also let you have a extra area so you can update the install on the USB and add extra stuff. On my net-book I have it set to boot from the hard drive but if I hit f12 after starting it brings me to a choice to boot from the hard drive or the USB and something else.

I can understand that having your regular Vista trashed is a frustrating situation, but you will get the hang of this and have no more problems, ;)

I think the unetbootin is a more understandable with straight forward instructions, the main thing is don't hit install after booting grom the USB, try without installing.

---

### Post by imtiazu on 2009-11-10
Hmm.. ok... so am I correct in saying that I am not able to have a portable version of Ubuntu?

For example, I boot Ubuntu from my USB and then lets say I do some work... save files etc...
Do these changes get appended/saved to the Ubuntu OS on the USB or not? 
I've had a loot at Unetbootin too, thanks for that link!
However, I'm a bit more confused now about what I a) need to do to achieve my goal and b) if its even possible?

"I want my mom" :(

---

### Post by wilee-nilee on 2009-11-10
> **imtiazu said:**
> Hmm.. ok... so am I correct in saying that I am not able to have a portable version of Ubuntu?

For example, I boot Ubuntu from my USB and then lets say I do some work... save files etc...
Do these changes get appended/saved to the Ubuntu OS on the USB or not? 
I've had a loot at Unetbootin too, thanks for that link!
However, I'm a bit more confused now about what I a) need to do to achieve my goal and b) if its even possible?

"I want my mom" :(

I know the usb loader in Linux allows the extra space, so I suspect these others do to but I haven't used them, so I can't really help with those programs. The good thing is that there are lots of people on here who do know and a google search will probably be helpful I try looking for more info. Also how big is the USB I have a 8gig one that I had loaded at one time that had I think 4gigs open space for the stuff you want to save but I used the USB creator in Ubuntu.

---

### Post by imtiazu on 2009-11-10
on this link ([http://www.pendrivelinux.com/usb-ubuntu-netbook-remix-install/](http://www.pendrivelinux.com/usb-ubuntu-netbook-remix-install/)) it says the following:

"*Note: This installation tutorial does not cover Netbook Remix Persistence. As a result, changes made will not be saved and restored upon subsequent boots."

So I guess the answer is NO after all of that!? :(
Shame... I was hoping I could have a simple OS to take around with me which held updates and changes that I made to it once booted up on to a netbook.

---

### Post by wilee-nilee on 2009-11-10
> **imtiazu said:**
> on this link ([http://www.pendrivelinux.com/usb-ubuntu-netbook-remix-install/](http://www.pendrivelinux.com/usb-ubuntu-netbook-remix-install/)) it says the following:

"*Note: This installation tutorial does not cover Netbook Remix Persistence. As a result, changes made will not be saved and restored upon subsequent boots."

So I guess the answer is NO after all of that!? :(
Shame... I was hoping I could have a simple OS to take around with me which held updates and changes that I made to it once booted up on to a netbook.

If you can find a person running Ubuntu then use the USB creater.
[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)
You can have what you want I am relatively sure that the USB creator is not the only one that will do this so it is a matter or waiting for help on this forum checking other forums and just searching for a windows friendly device that does this.

---

### Post by imtiazu on 2009-11-10
Ahhhaaaaa!! COOL.. got ya!
Ok, will continue in my quest to find how to get that. 
So I'm guessing what I really need to be asking/looking for is...
"a live Usb persistant Ubuntu netbook remix version"? :D

Thanks for your help! The fog is lifting now...

---

### Post by wilee-nilee on 2009-11-10
> **imtiazu said:**
> Ahhhaaaaa!! COOL.. got ya!
Ok, will continue in my quest to find how to get that. 
So I'm guessing what I really need to be asking/looking for is...
"a live Usb persistant Ubuntu netbook remix version"? :D

Thanks for your help! The fog is lifting now...

I think that is the syntax, what you might want to know also about the remix is that it is a regular Ubuntu release with the special cool desktop face. There are several other remixes Kubuntu has one there is moblin, and KDE is working on one and there are probably others. I found this even though you posted a non persistant note from the pendrive link.
[http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/](http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/)
This should work with Karmic if it does with Hardy.

I just searched google with live Usb persistent Ubuntu windows, and here is a link to what Google found.
[http://www.google.com/#hl=en&ei=SGL5SuvDF4rKsAPZ8MjQCQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAYQBSgA&q=live+Usb+persistent+Ubuntu+windows&spell=1&fp=74f5ed7994d722e7](http://www.google.com/#hl=en&ei=SGL5SuvDF4rKsAPZ8MjQCQ&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAYQBSgA&q=live+Usb+persistent+Ubuntu+windows&spell=1&fp=74f5ed7994d722e7)

---

### Post by Mighty_Joe on 2009-11-10
You could do a full install to a USB drive.  It will be faster than the "Live USB" style installs UnetBootin and the Live USB Creator make, but it will take up more space on the drive.  It works on every computer I've tried, but I can't say it will work on all computers.
I posted a link to detailed instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1193680")

---

### Post by wilee-nilee on 2009-11-10
I wonder if the ISO is in windows and you boot a live Ubuntu CD then open the vista partition if you can load the link to the the ISO from Vista into the USB creator then have it load the USB and use the slider in the creator to have the persistent space. 

I like the links above but I wouldn't try them myself when I have gotten used the the Ubuntu IMG and ISO loaders. That should not stop anybody else trying them though. I have a W7 and Karmic dual boot though .

---

### Post by imtiazu on 2009-11-11
INTERESTING!!! Having tried to mess about with the install again last night, there is no option in the menu for "try without installing" :S

I downloaded 9.10 iso from Ubuntu's website. I'm guessing something else is up here too???

---

