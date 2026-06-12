---
title: "Ubuntu to the rescue!"
date: 2008-08-22
forum: General Help
---

### Post by weightgain4000 on 2008-08-22
Hello 

I need some help

Im getting into windows xp/vista desktop support and often Ive come across viruses or spyware or other situations that completely lock me out of clients computers (even access from safe mode)

So what I want to know is 

Can I alter ubuntu to meet my needs 
(im not THAT linux savvy but Im willing to try)

Or does anyone know of another distro that meets my needs? 
(Ultimate boot CD is not suitable for me so thanks but no thanks)

My requirements 

1 something that works!

2 can boot from preferably USB (there’s an important reason for this) or as last resort CD 

3 all aspects when OS is loading have minimum user intervention 
I want something quick and easy that I can just use without having to remember lots of commands or going to bash to get something working

4 auto configure network card prefer wireless support but not a huge priority

5 Max hardware support and auto configure hardware 
and has the ability to be updated semi automatically (so I can manually tell the OS to update and it looks for the latest drivers and installs them by itself) 

6 low system requirements so can run on a machine with min 128 ram and a duron/celeron processor in at least 640x480 or prefer 800x600 

7 can fit and work comfortably on at 2gig USB or last resort CD-R

8 autostart in Gui interface TWM, IceWM, Blackbox etc

9 mouse support

10 gui/xwindows apps that can scan and remove windows specific viruses spyware greyware and can auto/manually update itself from internet and definitions can be stored on USB (so I dont have to download new updates each time or if Im working on a machine without internet access)

11 gui/xwindows apps to mount NTFS and fat32 file systems in read only and read/write

12 gui/xwindows apps to browse file system copy/backup files from NTFS or fat32 to flash disk, DVD or CD

13 gui/xwindows apps to for basic disk utilities, partition tools error checking and undelete  

14 gui/xwindows apps for text editor/word processor and ability to store documents (USB version)

15 ability to change/reset windows passwords (but not a huge priority)

16 internet brower (firefox) and other basic network functions ping tracert 

17 ability to store bookmarks on (USB version) 

18 uses open source or freeware but happy to use "not for commercial use"/limited license

19 is free to distribute

20 fun and easy to use

Any help appreciated 

P.S if this is not in the correct forum please move me :-)

---

### Post by jimv on 2008-08-22
You can install Ubuntu onto a 4 gig (or larger) USB thumbdrive just like a regular hard drive.  If you want lower system requirements, then you can use Xubuntu.

---

### Post by weightgain4000 on 2008-08-22
> **jimv said:**
> You can install Ubuntu onto a 4 gig (or larger) USB thumbdrive just like a regular hard drive.

Thanks for the reply 

What im looking for is a more customised version of ubuntu thats geared towards xp/vista system rescue

Ive looked at trinity rescue kit and SystemRescueCd but these are more designed for the experienced linux user
and Im wanting something quicker and easier to use

---

### Post by panhandle on 2008-08-22
What about Knoppix?

[http://www.pendrivelinux.com/2007/01/01/usb-knoppix-510/](http://www.pendrivelinux.com/2007/01/01/usb-knoppix-510/)

---

### Post by weightgain4000 on 2008-08-22
> **panhandle said:**
> What about Knoppix?

[http://www.pendrivelinux.com/2007/01/01/usb-knoppix-510/](http://www.pendrivelinux.com/2007/01/01/usb-knoppix-510/)

Thanks for your reply

Ive considered Knoppix but its a little too heavy weight for my purposes

what I really really want it a stripped down version of linux with max hardware support! is 99% gui and as small as possible under the circumstances and is geared towards system recovery

Knoppix has to many other packages that are not needed but it could be an option so I will post a similar thread on the forums there

---

### Post by prshah on 2008-08-22
> **weightgain4000 said:**
> 
what I really really want it a stripped down version of linux with max hardware support! is 99% gui and as small as possible under the circumstances and is geared towards system recovery


I'd suggest you start with a basic Xubuntu (or Arch- but that might take a lot longer to get the way you want it) installation; customize that with whatever packages you want to add/remove; then, once you have reached a point where you are happy with the system, create a custom live CD using [remastersys]("en.wikipedia.org/wiki/Remastersys").

Note that you can install ICEwm seperately into any ubuntu distro you want, with a single command.

You can also xfer this live CD to a USB stick for booting, look in [www.pendrivelinux.com](www.pendrivelinux.com) for instructions, or post back here if you have difficulties.

---

### Post by weightgain4000 on 2008-08-22
Thank you very very much :-D

That is extremely useful

so I just want to clarify I need to install basic Xubuntu then add/remove the packages as required 

and then I can create a custom live CD using remastersys.
then look here for [www.pendrivelinux.com](www.pendrivelinux.com) instructions on how to put this onto a pendrive correct?

---

### Post by ugm6hr on 2008-08-22
PuppyLinux fulfils most of those requirements, and is designed to fit on USB sticks.  It is also a lot faster running from USB than Ubuntu.  It used to run from RAM with 128MB+.

Not sure about the Windows virus checker, but I'm sure one must be available in the repo.  Resetting Windows passwords is probably not possible either.

---

### Post by MaxIBoy on 2008-08-22
I think ClamAV (free open source antivirus) has a Linux version for scanning Windows partitions, try putting that on your little remastering project.


Now, saving stuff on a LiveUSB may be impossible, I've never used a LiveUSB distro so I wouldn't know for sure. From what I understand, a LiveUSB is basically just a LiveCD with more room for packages and faster. I could be wrong.



At least under Windows XP, hitting the right buttons at the right place in the boot process will show you what your administrator password is (or the administrator password for the school computers, for that matter.)

---

### Post by prshah on 2008-08-22
> **weightgain4000 said:**
> correct?

Yes. 

There are a number of anti-virus options, including: AVG, Kaspersky, and more. ClamAV is dead (?), I believe.. not sure. However, most linux anti-virus clients are free; Kaspersky is the exception.

---

### Post by weightgain4000 on 2008-08-22
ok thanks!!!! 

this is even better!!! :-D

---

### Post by jimv on 2008-08-22
You might also want to look into making a BartPE disk or USB key.

[http://www.google.com/search?q=bartpe&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=bartpe&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

