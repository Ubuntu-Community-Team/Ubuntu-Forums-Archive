---
title: "Installing Ubuntu on Dell M2010"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by Scrammbles on 2009-06-11
So I tried installing through windows, just so I could try the OS out.
I rebooted and picked the unbuntu option.  It looked like it was booting up fine.  When I got to what I guess would be the desktop, most of the screen was black, the mouse cursor was a small orange square, and the top of the screen was...  Like a bad video file...  horizontal lines and multi colors.

Any help?

---

### Post by Scrammbles on 2009-06-11
someone have any advise on this?

---

### Post by Scrammbles on 2009-06-11
So I tried install the newest version of Ubuntu through the Windows install (my dvd drive doesn't read burned disc's anymore, so I had no choice).  The install seems to go fine, but when I reboot and boot into Ubuntu, I get to what I assume is the desktop, except tithe screen is all black.  The mouse is a small orange block, and the top of the screen is all messed up...  Horizontal lines, multi colored.

Any help on this issue?

---

### Post by Scrammbles on 2009-06-11
So I tried install the newest version of Ubuntu through the Windows install (my dvd drive doesn't read burned disc's anymore, so I had no choice). The install seems to go fine, but when I reboot and boot into Ubuntu, I get to what I assume is the desktop, except tithe screen is all black. The mouse is a small orange block, and the top of the screen is all messed up... Horizontal lines, multi colored.

Any help on this issue?

---

### Post by Megrimn on 2009-06-11
did you install it *inside* Windows (like with wubi) or does ubuntu have its own partition on the hard drive?

---

### Post by Scrammbles on 2009-06-11
You will have to excuse me, I'm totally new to the Ubuntu world.
I installed from windows.
Mounted and image of the install disc in Daemon tools, and went through the install process.
the install does not have a partition of its own

---

### Post by Megrimn on 2009-06-11
Well, I have a hunch, and the first thing I would do is to try reinstalling ubuntu, with its own partition. 

to do that, you have to restart the computer with the live cd in the disk drive.  

Once you get to the ubuntu desktop, double click the install icon and go through the install thing.  You can decide how much space you want for ubuntu on the hard drive in the installer ( I would say no less than 20GB, if you have that much.  You can always resize it later).  

Once you get that done, pick the ubuntu option from the GRUB menu like before, and post your results...

---

### Post by Scrammbles on 2009-06-11
I would, try that, but my dvd drive crapped out, thats why I installed through windows. On occasion it will read legit cd/dvd's, and never reads burned ones anymore.

---

### Post by MaindotC on 2009-06-11
Yes you'll need to configure xorg.conf to resolve these issues and I've a feeling that's well beyond your level of patience.  What type of video card are you using?

---

### Post by lisati on 2009-06-11
No need to have multiple threads on the same question

---

### Post by Scrammbles on 2009-06-11
Radeon X1800

---

### Post by PmDematagoda on 2009-06-11
Scrammbles:- Please do not start multiple threads on the same problem, just one thread is more than enough.

---

### Post by FishyFantasy on 2009-06-11
You can try install Ubuntu from a pendrive. Try this? 

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/")

---

### Post by Scrammbles on 2009-06-11
sorry...  just very eager to get this running on my laptop

---

### Post by Scrammbles on 2009-06-11
I thought about it, the pendrive, but form what I have read, it needs to be 8G in size.  I only have a 4g

---

### Post by Megrimn on 2009-06-11
> **Scrammbles said:**
> I would, try that, but my dvd drive crapped out, thats why I installed through windows. On occasion it will read legit cd/dvd's, and never reads burned ones anymore.

Yeah, that sucks.  

If it were me, I'd just hijack a cd or dvd drive from a different computer and put it in the Dell for the time being, or use a USB cd/dvd drive, but that's me.  Sorry I couldn't help more.

---

### Post by MaindotC on 2009-06-11
I sincerely doubt the hard drive has anything to do with this issue and installing Ubuntu on a pendrive really isn't going to help.  I suggest you download the ATI Proprietary driver and follow the installation instructions.  Definitely seems like a video driver issue.

---

### Post by Scrammbles on 2009-06-11
yeah, I thought it may be a vid driver problem as well, but seeing as how I am totally new to Ubuntu, I didn't know for sure, let alone where to start.
Haha, I would hijack a dvd drive from someone, but the one in my laptop is rather unique, and I don't really know how to replace it.

---

### Post by FishyFantasy on 2009-06-11
Well actually I never try to install Ubuntu from a pendrive before. I will always use the LiveCD install because it never gives me any problem. Some other methods like installing from hard disk, my Ubuntu become very unstable.

---

### Post by Scrammbles on 2009-06-11
strAlan - ok, I downloaded the driver, and read the install, then realized a major problem with that plan.  the driver has to be installed from the OS, so I would have to be in Ubuntu to install it.  
I can get into the OS, but like my opening post says "When I got to what I guess would be the desktop, most of the screen was black, the mouse cursor was a small orange square, and the top of the screen was... Like a bad video file... horizontal lines and multi colors."  So, needless to say, I can't get the driver installed

---

### Post by Megrimn on 2009-06-11
> **strAlan said:**
> I sincerely doubt the hard drive has anything to do with this issue and installing Ubuntu on a pendrive really isn't going to help.  I suggest you download the ATI Proprietary driver and follow the installation instructions.  Definitely seems like a video driver issue.

Well, yeah.  That's why I figured a direct install from the live cd would fix that, because it would be able to detect the screen resolution and stuff.  Later, after booting without the cd for the first time, the computer would automatically notify that the driver needed to be downloaded.  

It doesn't help that everything after Hardy is using "autodetect" for screen resolution and stuff now.  Probably the reason why I haven't bothered to upgrade to jaunty.  

----------

In fact if you felt like trying hardy, once you got it installed, you could just open a terminal and use this:

```
sudo displayconfig-gtk
```

to manually configure it.  But that's in Hardy.

---

### Post by Scrammbles on 2009-06-11
Megrimn - I may have to give that a shot, Hardy that is.  I just want to rid myself of Windows haha.


Edit - guess I was wrong on the pen drive size, and I will be able to try this.
So i'm going to give it a shot and hope for the best.
I'll post my results.

---

### Post by Scrammbles on 2009-06-11
Ok, so booting up from the pendrive worked.
I got in, looked around so to say, configured my wireless and what not.
So far the only problem I encountered was trying to play music and gettin flash player for youtube...  Not a major issue.

---

### Post by Megrimn on 2009-06-11
> **scrammbles said:**
> ok, so booting up from the pendrive worked.
I got in, looked around so to say, configured my wireless and what not.
So far the only problem i encountered was trying to play music and gettin flash player for youtube...  Not a major issue.

[color="blue"][size="4"]yay![/size][/color]

---

### Post by Scrammbles on 2009-06-11
Oh, before I forget again, what is a good amount of space to allocate for a Ubuntu partition?
I botted into the OS through the pendrive, but did not fully install it yet as I wasn't sure how much space was needed for a full install, and was way to tired last night to bother looking around for the info I needed.

---

### Post by Megrimn on 2009-06-11
When I first put ubuntu on my computer, allocated 60GB for it.  That appeared to be plenty, because I've only used a little over 20GB (lots of video files and such).  I'd say somewhere between 20GB and 80GB, depending on how much you think you will be using.

---

### Post by Scrammbles on 2009-06-11
Well, right now the plan is only to dual boot with it.
Currently I'm running Win XP Medina Center.  I have a 160G HDD, but only have 12gigs free haha.
the current plan is to give Ubuntu a test run, see if I can run most of my stuff on it, and to see how much I like it, as I am trying to get away from Windows.
Right now I'm working on clearing space off my hdd to I can do a full install and have some space to play with so to say, worst case situation, I will just have to transfer my music folder onto my external drive, which will free up almost 18G's of space haha.

---

### Post by Megrimn on 2009-06-11
I'm dual-booting too, but I have a 250GB Hard drive, so I was able to give space-hog windows 140GB and save 60 for ubuntu.  

You know you can access any files on your windows partition from Ubuntu?  That's my favorite part.  (just don't do anything stupid :D)

Uninstalling programs you don't use anymore can free up space, too.  Especially the crap that comes ***pre-packaged*** with windows...

---

### Post by Scrammbles on 2009-06-11
Haha, yeah, I unloaded a bunch of un-used programs.  Plugging away through my music files right now, deleted quite a few, I'm up to 20.5Gb now.
I tell ya, I f'in hate windows these days haha.
So far the only downfall I have seen to using Ubuntu as my main OS, is a few compatibility issues (games mostly), and the fact that my internal speakers won't work

---

### Post by Scrammbles on 2009-06-12
Ok, so I have cleared 45.5G worth of space on my hard drive....  Turns out I had a lot of crap I didn't need haha.
Anyways, I want to get Ubuntu fully installed onto my hdd, so I don't have to boot off my thumb drive.
Not really sure how to do the partition in Ubuntu though.
I have a screen shot taken, and attached, if someone could point me in the right direction it would be awesome.  I plan to use 20G for the partition. 

[IMG]http://i11.photobucket.com/albums/a175/DaxMaurier/Screenshot.png[/IMG]

---

### Post by Scrammbles on 2009-06-12
going by the above screen shot, can anyone help me set it so the partition for ubuntu is 20G

---

### Post by Megrimn on 2009-06-12
by the screenshot above, it seems you have about 110 GB on there, so move the slider until the number in parenthesis is 90GB.  It will install ubuntu + swap on the other 20GB.

---

### Post by Scrammbles on 2009-06-12
if I move the slider so it say's 90Gb, won't that make the Ubuntu patiton 90 in size?
I thought I would have to move it down to the 20 range

---

### Post by Megrimn on 2009-06-12
no, the orange part of the slider is resizing the partition that is already on there to make room for the new ubuntu partition.

---

### Post by Scrammbles on 2009-06-13
Ok, I wasn't trying to second guess you or anything, I just wanted to be sure.

---

### Post by MaindotC on 2009-06-13
> **Scrammbles said:**
> I can get into the OS, but like my opening post says "When I got to what I guess would be the desktop, most of the screen was black, the mouse cursor was a small orange square, and the top of the screen was... Like a bad video file... horizontal lines and multi colors."  So, needless to say, I can't get the driver installed

Press ctrl + alt + f2 to get to tty2 and login.  You can also select "recovery mode" from GRUB to get to a prompt.  I didn't realize you weren't aware of this and I wouldn't have suggested you install the driver if you had to be logged into the very environment you are trying to fix.

---

### Post by Scrammbles on 2009-06-13
haha dont worry bout it, I managed to get into the system by booting from a flash drive.
thanks for the help though!

---

### Post by MaindotC on 2009-06-14
> **Megrimn said:**
> Well, yeah.  That's why I figured a direct install from the live cd would fix that, because it would be able to detect the screen resolution and stuff.  Later, after booting without the cd for the first time, the computer would automatically notify that the driver needed to be downloaded.  

Good point - I didn't think of that, and I won't upgrade to anything over 8.04 either, primarily b/c of my video card.

---

