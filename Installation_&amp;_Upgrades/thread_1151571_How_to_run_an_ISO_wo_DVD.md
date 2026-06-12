---
title: "How to run an ISO w/o DVD"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by drewv on 2009-05-07
I have a test machine I'm running Ubuntu 9.04 on that doesn't have a DVD drive.  I'm trying to also install Windows 7 RC to test it out.  I downloaded the ISO on my laptop and transferred it over a network to my test machine.  I can mount the ISO just fine and see the files in the ISO.  But I can't get the ISO to run.  When I click on Setup.exe it runs the Archive Manager and I get an error message that says "End-of-central-directory signature not found. Either this file is not a zipfile, or it constitutes one disk of a multi-part archive.  In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive."  

I've looked around on the forums but can't figure out if I'm missing a file or package, or if I'm doing something else wrong.

Thanks for your help!  This forum really helps a noob like me to learn Ubuntu!  :)

---

### Post by Mark Phelps on 2009-05-07
Basically, you're trying to run an MS Windows executable in Linux -- which you can't do.  

You could check out the CodeWeavers site and read up on Wine -- which installs sofware allowing you to run SOME MS Windows apps.

I would be very surprised if you could use Wine to install an MS Windows OS.  But then, stranger things have happened.

---

### Post by HyRax on 2009-05-07
If you want to evaluate Windows 7 within Ubuntu, then what you want to setup is a virtual machine that you can install Windows 7 into.

Go grab yourself a copy of [Virtualbox](http://www.virtualbox.org). This will allow you to create a virtual PC within your real PC to try stuff out on without impacting your main PC.

---

### Post by drewv on 2009-05-07
I was thinking that there not even be a way for me to get the ISO to run.  It seems that you guys are confirming that.  

If I use Virtualbox, will that give me a good idea of how Win 7 would actually run on the hardware?  That was my main purpose in trying to install it on my test computer.  The hardware is just under the requirements for Win 7, so I wanted to see if I could tweak it enough to make it livable.

I know I'm trying to install a Windows program, but I thought that the files on the ISO would not be OS dependent since they are designed to be able to boot before any OS is running.  Am I wrong?  Maybe that is where I'm running into a problem, I need to get the computer to boot from that file.  Is there a way to do that?

---

### Post by kanikilu on 2009-05-07
> **drewv said:**
> I was thinking that there not even be a way for me to get the ISO to run.  It seems that you guys are confirming that. The problem has nothing to do with the ISO, but rather what you are trying to do with it. 

> If I use Virtualbox, will that give me a good idea of how Win 7 would actually run on the hardware?  That was my main purpose in trying to install it on my test computer.  The hardware is just under the requirements for Win 7, so I wanted to see if I could tweak it enough to make it livable. It should give you a *rough* idea - things usually run a little slower in a VM, so if you can "make it livable", it should be better if natively installed.

> I know I'm trying to install a Windows program, but I thought that the files on the ISO would not be OS dependent since they are designed to be able to boot before any OS is running.  Am I wrong?  Maybe that is where I'm running into a problem, I need to get the computer to boot from that file.  Is there a way to do that? You can't boot the computer from an ISO image. I second the suggestion to check out VirtualBox...

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

[http://twoguystech.com/blog/art/installing-windows-7-beta-suns-virtualbox](http://twoguystech.com/blog/art/installing-windows-7-beta-suns-virtualbox)

The second link uses VirtualBox on Windows, but once you have it installed in Ubuntu (first link), the process to get Windows 7 installed should be similar.

---

### Post by sgosnell on 2009-05-07
You can install ImageWriter and burn the .iso to a USB drive, giving you a bootable disk.  Whether it's a live CD is another question, and I know nothing of Windows7.  With Linux, you can burn the .iso to either a CD or a flash drive, and then have a live CD to try the OS.  Windows is not Linux, however, and I don't know if that will work for you.  It's worth a try, though, and won't cost you anything but some time, and you may learn something worthwhile.

On second thought, ImageWriter may not work with a .iso, but if it doesn't, unetbootin will.

---

### Post by drewv on 2009-05-07
I tried the Vitualbox method, but found out that I didn't have enough memory.  My flash drive was only 2 GB so I haven't had a chance to try that out yet.  I guess after a trip to buy some new toys I'll give you an update

---

### Post by HyRax on 2009-05-07
> **drewv said:**
> I tried the Vitualbox method, but found out that I didn't have enough memory.  My flash drive was only 2 GB so I haven't had a chance to try that out yet.  I guess after a trip to buy some new toys I'll give you an update

RAM is cheap - go max out your machine. Mine supports 8GB and that only cost me about AUD$200. Makes running all manner of simultaneous VM's a breeze.

---

### Post by drewv on 2009-05-07
Yeah, I usually max my machines out too!  Someone just gave me my new test computer and I haven't had time to order the RAM to max it out yet.

---

### Post by TSWMIN85 on 2009-07-27
Can't you boot from an ISO using GRUB and install an OS doing that?

An answer would be a million times appreciated!

---

### Post by HyRax on 2009-07-27
> **TSWMIN85 said:**
> Can't you boot from an ISO using GRUB and install an OS doing that?

An answer would be a million times appreciated!

Well, you *can* in a manner of speaking, but it's a bit cumbersome to do so as GRUB does not actually have direct support for booting ISO's and you need to create an extra partition on your hard-drive to store the ISO in question. It's not as simple as sticking a CD into your PC. Overall it IS easier just to burn the damn CD.

Using Virtualbox is a better way to go because it can "boot" from an ISO as it is treating it as a real CD. A real PC is a different story, however.

Personally I'm that lazy that I went to the effort of setting up a PXE boot server so I could do Ubuntu installs off my network rather than use any kind of standard boot media like USB or CD. I'm going to do the same with Windows install media too when I get time to do it.

However any way you look at it, if you're trying to save using up CD media, then it's easier to setup a USB boot stick for Ubuntu or Windows than it is to setup a PXE boot server or manipulate GRUB to boot from an ISO.

---

### Post by unutbu on 2009-07-27
TSWMIN85, I haven't tried this myself, but perhaps this is what you are looking for:
[http://ubuntuforums.org/showthread.php?t=457318](http://ubuntuforums.org/showthread.php?t=457318)

---

