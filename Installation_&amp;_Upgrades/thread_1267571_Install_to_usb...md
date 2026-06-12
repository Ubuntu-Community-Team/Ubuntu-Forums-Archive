---
title: "Install to usb..?"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by Dracar on 2009-09-15
Hello. I am trying to install ubuntu on my flash drive, but I cannot get it to work. I found a few things online but its like all they do is make the usb dirve = the live cd, is there any way to actually install the system to a flash drive so its a full working os?

---

### Post by gadolinio on 2009-09-15
I'm not completely sure about what you mean by "fully working OS", but I think this can be your answer:
What I have succesfully done is:
system-->administration-->create a usb startup disk (the package is <usb-creator>). A window appears, where i chose the downloaded .iso file (the same one used to make the live CD). Insert the usb stick.
There's an option that says "when starting up from this disk, documents and settings will be:" --> choose "stored in reserved extra space", and specify how much space you want to use for that purpose (I've specified the maximum possible, as i'm running ubuntu from a 2GB SD card). Then click "make startup disk". It takes about 5 minutes.
That usb drive is essentially a liveCD, but all you settings, wallpaper, themes, installed applications, panel launchers, documents stored in your user's folder, etc. remain there every time you turn the computer off and on. That would fit the profile of a "fully working OS", I think. The disadvantage would be that running from the usb stick is slower than having the OS installed in the computer's hard disk drive, but is much faster than doing it from a liveCD.
I've done  this because I share a laptop, and my co-owner doesn't want it to have linux installed. So I have ubuntu in the SD card, in the laptop's SD port/reader, and am able to use ubuntu exactly as I do in my desktop (where I have it installed in the hard disk drive). But if I remove the SD card, there's no trace of linux in the laptop.
Hope you find this useful...

---

### Post by scrooge_74 on 2009-09-15
I guess you need to have the usb plugged in when you have the live session running and then tell the system to install in there. So next time you boot I guess you need to tell BIOS to boot from usb and not from HD

---

### Post by Dracar on 2009-09-16
Ok, I was using a tool before that rigged it, i used the tool built in with 8.04 and up and it does work, but like you said, its a live cd rip. It just bugs me a bit that I cant just install to the flash drive. Could i get an explanation?

---

### Post by Mighty_Joe on 2009-09-16
> **Dracar said:**
> OIt just bugs me a bit that I cant just install to the flash drive. 

Who told you that you couldn't?  Look at my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680") for instructions on how to install and optimize a flash drive install.

---

### Post by gadolinio on 2009-09-16
> **Dracar said:**
> Ok, I was using a tool before that rigged it, i used the tool built in with 8.04 and up and it does work, but like you said, its a live cd rip. It just bugs me a bit that I cant just install to the flash drive. Could i get an explanation?
I don't know what tool you were using.
If you "burn" your flash drive with usb-creator and select "stored in reserved extra space" you'll have ubuntu installed there. I haven't found a single function that is not available that way.

---

### Post by Dracar on 2009-09-30
Ok, I haven't had much time to test, my home computer cant boot from USB. anyways, I've used the built in "USB startup disk creator". It doesn't do what I am looking for. Its still just a live CD, is there no way to just flat out install it? not try to emulate a live CD? It really bugs me that firefox settings don't save from session to session, new usernames don't save, etc etc... I also installed a few programs, and they didn't save either.

---

### Post by Mighty_Joe on 2009-09-30
> **Dracar said:**
> is there no way to just flat out install it? 

So you didn't read the link I posted two weeks ago?  You can install Ubuntu directly to a flash drive just like you can any other drive.

---

### Post by Dracar on 2009-09-30
UNetbootin? I've tried that, its the exact same thing as the create usb startup tool built in, accept it causes more problems. I had to redo it every 2 boots.

---

### Post by earthpigg on 2009-09-30
three options:
1) unetbootin
2) usb startup disk creator with reserved extra space
3) standard install onto thumb drive. boot from live cd, click install, select the thumb drive as the target. important: at the final screen before the partitions are committed to disk, there is an 'advanced' button. you will need to hit that button and then tell it to install the bootloader onto the thumb drive as well.

the problem with option three is that thinks will get funky if you start using it with multiple computers. i used option three to use the thumb drive as a hard drive on a laptop with a busted hard drive.

option 2 is probably the best.

---

### Post by Mighty_Joe on 2009-10-01
> **earthpigg said:**
> the problem with option three is that thinks will get funky if you start using it with multiple computers. 

Does this problem really exist?  I've tried my bootable USB drive on several computers and haven't had any problems.  
I've heard a claim that it was due to xwindows needing reconfiguring in previous versions of Ubuntu (so it's not an issue with 9.04) and another claim that if one used proprietary drivers (I don't).

---

### Post by earthpigg on 2009-10-01
> **Mighty_Joe said:**
> Does this problem really exist?  I've tried my bootable USB drive on several computers and haven't had any problems.

those produced with usb startup disk creator and unetbootin generally do not have this problem.

---

### Post by Mighty_Joe on 2009-10-02
> **earthpigg said:**
> those produced with usb startup disk creator and unetbootin generally do not have this problem.

Sure, because they are basically Live CD's, which are set up to detect hardware at startup.  You said your "option 3" (a full install) can have this problem.  I haven't seen it, though I won't claim that the 3 computers I'm using are an exhaustive test, so I was wondering if you *had *seen it.

---

### Post by ramazani on 2009-10-02
use unibootin in linux just type sudp apt-get install unibootin and if did not managed to install it  you need to do the follwoing 



sudo gedit /etc/apt/sources.list
and add this two to end of list and save it 
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) jaunt
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
sudo apt-get update
sudo apt-get install  unetbootin

---

### Post by earthpigg on 2009-10-02
> **Mighty_Joe said:**
> Sure, because they are basically Live CD's, which are set up to detect hardware at startup.  You said your "option 3" (a full install) can have this problem.  I haven't seen it, though I won't claim that the 3 computers I'm using are an exhaustive test, so I was wondering if you *had *seen it.

no, but the same thing about exhaustive testing applies to me... i dont want to claim it ***will*** work unless i know that to be the case.

---

### Post by beacon on 2009-10-04
This all sounds so simple, but I can't get past the first hurdle. The flash disk is recognised, but when I insert the DVD (ubuntu Jaunty iso), I am told that 4.4.gb are required and that my disk isn't big enough. The directions given in Linux Format say you can even install it with 1gb. Any idea what I am doing wrong, and how I can correct it?

---

### Post by Dracar on 2009-10-04
I didn't even see an option to install it directly to a thumb drive, I would have because every single computer in my college is the exact same, I did option 1 first, then option 2, nothing saves inbetween session,having to re delete the examples folder every single time and make a username and reconfigure firefox and reinstall all my apps gets old fast. Considering some other OS's now, i cant stand using windows for anything but games.

---

### Post by Habboblob on 2009-10-04
Some of these ways are a bit complicated.

I've got a very easy method, which let me run Ubuntu persistently off a USB.

So I could save files, install programs, just like a normal OS, but on a USB!

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

It have a casper-rw file which seems to store all your data.
The tutorial by default comes with a 2GB file, but if you have a larger usb, like I had a 4GB, you would be better off with the 3GB Casper-rw file. Look near the end of the tut for the casper-rw files.

Hope this helped :)

---

### Post by Mighty_Joe on 2009-10-05
> **Dracar said:**
> I didn't even see an option to install it directly to a thumb drive,

There is no distinct option to install to a USB flash drive.  Linux sees a USB drive the same as an internal hard drive.  I linked you to step-by-step instructions two weeks ago.  Did you follow my links?

---

### Post by Dracar on 2009-10-05
^> **Dracar said:**
> UNetbootin? I've tried that, its the exact same thing as the create usb startup tool built in, accept it causes more problems. I had to redo it every 2 boots.

And I know it sees them the same, i mean the drive wasnt in the list, only my 3 internal drives.

---

### Post by Mighty_Joe on 2009-10-05
> **Dracar said:**
> 
And I know it sees them the same, i mean the drive wasnt in the list, only my 3 internal drives.

You have to be *really *specific when describing what you've tried.  We aren't looking over your shoulder, ya know ;)
There is a recent post that [certain vendor's flash drives]("http://ubuntuforums.org/showthread.php?t=1266014") don't play well with either the installer or USB Creator. Note that the original poster's problem was apparently a [bios setting]("http://ubuntuforums.org/showpost.php?p=8004221&postcount=22"). Have you tried more than one USB drive?  More than one host computer?    
There's a lot to go wrong here.  The more details you give us, the better.

---

### Post by Dracar on 2009-10-05
Ive tried many computers and 4 flash drives all of different makes lol. i am dealing with it at the moment... Deffinitely gunna need an alt. at some point, i cant stand resetting everything so much, Il see if i cant come accross another flash drive to test with it just in case...

---

