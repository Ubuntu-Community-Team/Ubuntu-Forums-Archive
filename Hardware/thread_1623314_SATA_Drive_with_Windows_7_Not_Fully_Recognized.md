---
title: "SATA Drive with Windows 7 Not Fully Recognized ?"
date: 2010-11-16
forum: Hardware
---

### Post by vangelists on 2010-11-16
Hello,

I'm a new user in Ubuntu and this is my first post here in the forums.

Well... right into the point! (because I'm in a hurry, I need my laptop for school)

My Windows 7 laptop is full of viruses (very weird for Windows... :P), so, in order to clean it up a bit, I decided to take the HDD off of my laptop and connect it to my PC which runs Ubuntu 10.10 Maverick.

Although I have done this many times before, when I had Windows XP installed in my PC, this time with Ubuntu there is a problem:

The system recognizes the drive, the manufacturer, the model and says "250GB" in it's name, but along that there is a "System Reserved" label next to the name. When I go into Properties it says 100MB space, but in Disk Utility I can see all the partitions, but labeled as "Unknown".

Here are some screenshots, that will definitely help you understand what I mean:

Disk Properties: [http://i756.photobucket.com/albums/xx209/vangelists/3dfd1ecc.png](http://i756.photobucket.com/albums/xx209/vangelists/3dfd1ecc.png)
Disk Utility: [http://i756.photobucket.com/albums/xx209/vangelists/52381e32.png](http://i756.photobucket.com/albums/xx209/vangelists/52381e32.png)

I would really appreciate it, if you would help me as soon as possible! 

Thank you very much, in advance! :-)

---

### Post by wilee-nilee on 2010-11-16
Back up the W7 important stuff scrub it clean and reinstall W7. Personally I'm not going to click on any links from a first time post that mentions virus problems. I could quite safely but you can post that information straight as a .jpg

---

### Post by vangelists on 2010-11-16
> **wilee-nilee said:**
> Back up the W7 important stuff scrub it clean and reinstall W7. Personally I'm not going to click on any links from a first time post that mentions virus problems. I could quite safely but you can post that information straight as a .jpg

Sorry for the links, I think it's better now. They are just screenshots (PNG FIles) uploaded to Photobucket, you can safely open them. I just use Google Shortener to make them look better.

It's impossible to format Windows 7 because I use my laptop a lot and I have some hundred GigaBytes of files that fit nowhere else.

That's why I ask for a way to completely read the whole drive.

---

### Post by wilee-nilee on 2010-11-16
Open gparted in Ubuntu right click on the drive partitions and look at the info, you probably have multiple problems, viri, and more then likely a chkdsk is needed to get it back in shape for reading.

I just bought a 2 terrabyte external drive for 130$, do your self a favor and get a external drive. For a couple of reasons. If you had backed up the original install the whole thing to begin with all you would have to do is slip that back in. You would also have a gigantic area to store stuff.

That is about the limit of my help, sorry for not being more helpful.;)

---

### Post by vangelists on 2010-11-16
I have to agree that external hard drives and, first of all, backups are a real life-saver, for the user and for the computer, too.

However, I abandoned the previous method, so I returned the disk back to its place (laptop). So, I would like to ask you something else, if you know:

I downloaded BitDefender for Unices for free personal use, as a *.deb package. Is it possible to create a live CD from it that would boot and directly run the program? Even if it is possible to update or not.

---

### Post by wilee-nilee on 2010-11-16
Sorry I had to get a nap in so I'm back now. What I would use is exactly what your thinking a live cd or this.
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

This has bitdefender and Kapersky on it or the ability to get both on a thumb. You download the latest definitions and scrub away.  

There are live cd versions for many AV software so just look around.

One thing that many who use a MS setup are not aware of at least the people I meet is that using a limited account as your regular operating space wipes out about 90% of the danger, also a password that is strong enough. You can right click from the limited and install things like the admin account. Using a limited keeps the root protected much better, and why Linux in general or open source platforms require this to start with.

Personally I would be worried about undetectable rootkits there are some out there so always wear a hat when you go out in the rain.;)

---

### Post by wilee-nilee on 2010-11-16
I just found this link.
[http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/](http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/)

---

### Post by vangelists on 2010-11-17
Thank you very much for your time and your patience, I'll try all of these!

I hope that some day I'll be able to help you, too!

First post here and I can confirm all the rumors that Ubuntu users and the community are really helpful!

Thanks, again!

---

