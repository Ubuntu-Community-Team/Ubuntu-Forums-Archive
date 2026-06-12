---
title: "old lubuntu not accesible with usb"
date: 2024-05-30
forum: Hardware
---

### Post by thorbs on 2024-05-30
I found an old laptop with lubuntu on it. I would love to get the photos and documents of it. However all usb is read only on it for some reason. Is there something I can do?

---

### Post by yancek on 2024-05-30
You could start by giving some  information on the hardware, manufacturer, age of device, etc.

>  However all usb is read only on it for some reason.

What does that mean?  Does the machine have a hard drive?  Does it have an OS on it?  If so, what is it?  Can you not boot it?  Can you boot any 'live' Linux OS from a USB or DVD drive?  You say you 'found' an old laptop and want to get documents and photos off it, why?  How do you even know there are documents and photos on it?  Is this someone else's computer?  You might explain the situation in a little more detail.

---

### Post by thorbs on 2024-05-30
Hi its a lenovo t61. Its mine. Havent used it for a long time, so the os is not updated. 

It boots. 

It runs lubuntu and I know the password..

for some reason when I take usbsticks, which in my daily laptop, is both read and write they are all read only. I have tried 5 different usbs, same result. 


Thank you.

---

### Post by guiverc on 2024-05-30
You've not provided Lubuntu release details..

If you want data off an old laptop, I'd not be booting the laptop internal system first... but boot *live* media and perform checks from there..  Does the system look healthy?  work reliably?  etc.. as if anything goes wrong as you're running a *live* system (off thumb-drive) there will be no damage to the installed system, which you can also explore & get clues from whilst the *live* system is being run.  If all looks good, you can also make copies from the installed system to another USB media which you know is functional.

The mention of RO you make is unclean, I wonder if its the result of problems being detected on media, as problem detected will *flip* a RW file-system to RO to prevent data-loss as a preventative media, but you've given no specifics as to Lubuntu release, what file-system(s) are involved, and what you're trying to do (*in what programs, what command etc*) and thus what the actual issue is... If you use GUI not all error message(s) will show but they'll be in system logs, but at terminal they usually appear on screen.  I'd explore that on the system, but in reading what you write, we're limited to details you provide where I don't know what you're trying to exactly do, nor what you're actually using.

---

### Post by thorbs on 2024-05-31
Thank you for the answer.

I am trying to get my files of to best of my technical abillities. From your answer I believe my abillities are lacking a bit here. 

So should I try to look at the laptop with a live media, or is that too late?

I am not sure what it means that my mention I make of the RO is unclean?

I believe the last sentence is instructions "I'd explore that on the system, but in reading what you write, we're limited to details you provide where I don't know what you're trying to exactly do, nor what you're actually using.". I am not sure how to understand this, or what to do next. I am sorry for my lacking of understanding here, it might be really clear. Is there something concrete I could do?

For my actions I have simply turned the laptop on, identified files I need. Used the standard filesystem copied the folders I wanted and tried to copy it to the usb, with the result of a pop up telling me the usbs all where read only. I only done this, because that what I usually do. 

I just tested and the usb is not read only when I use it on my everyday ubuntu laptop. So the usb is not permenently flipped. 

Is there anything I can do here or have I somehow ruined it?

Thank you

---

### Post by thorbs on 2024-05-31
I just went into grub, and I could see it was identified as ubuntu 13.04.

---

### Post by guiverc on 2024-05-31
Ubuntu 13.04... or a release that reached [*End of Life *back in January 2014]("https://fridge.ubuntu.com/2014/01/28/ubuntu-13-04-raring-ringtail-end-of-life-reached-on-january-27-2014/")....

That's a machine that has been *ignored* for a long time, so I'd not be trying to boot, or use it, until you've worked out how reliable it is.

Firstly, I'd likely open it up & visually check the machine, remove any dust etc carefully to ensure the system has proper cooling (ie. *whilst you're trying to get data off it with it on, you don't want the destroy the machine due to collected dust from years of neglect...*).

I'd visually scan it (*motherboard etc*), and ensure it all looks like it should, no signs of component failure (*swollen caps/capacitors etc*), no obvious signs of spilt drinks or other damage causing ruin...  ie. general housekeeping of the hardware

Next I'd boot it and go only to machine firmware (ie. BIOS of the machine)... If it has diagnostics I'd use them to get it to assess itself (*esp. RAM* *but I'd not check the health of disk, I'd do that later*).  

I'd then boot *live* media and perform RAM tests there... letting them run overnight, or at least 5+ hours... if you have no issues there, I'd restart the *live* system and explore disk health next.

FYI:  By *live* system, I mean an OS running purely from *thumb-drive *and operating using only RAM, ie. not installed. Ubuntu install media allows this; just select the TRY UBUNTU option (*or Try Lubuntu if using Lubuntu media*).

I'd run SMART checks next (from *live* media), which is really a process by which you're asking the drive electronics to report its own health..   I'll provide as link this page [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) but various tools allow you to get to that detail. I'm using Lubuntu *oracular* now, and I can run *KDE Partition Manager* and query the SSD health on this system.. but personally I usually do it from *live* media, and use the terminal tools myself.

This can be done anytime, but its what I'd usually do whenever I'm wanting to explore an unknown system, recently purchased second hand device, or any of my own device that I've ignored for years... I get clues as to the machine's health BEFORE I try and use it normally.

If the drive is failing.. this will give you clues of the health WITHOUT DOING ANY DAMAGE to it, meaning you've a greater chance to get data off, as you've only read data from the drive electronics thus far, thus can plan (*given results & indication of health*) the best approach to get the most data back before a *failing* drive finally *fails*.

If the drive looks good, I'd reboot the *live* system (*I may not if I know what I've done won't impact  what I'm about to do, but don't mind rebooting live systems*) and then try mounting the drive I want to get data from.

A Ubuntu 13.04 system will likely have an EXT4 file-system on it, but given I don't know your system, I'd look and see what is actually there and work from that. Terminal or GUI commands can be used, but I'd use terminal as I find it easier to see the result(s) OR any message(s) (including errors) following the command...  You may prefer a GUI tool on your *unstated live* system if you're using it.

I'm not sure how to help you with your situation further, as I'm unsure what you're doing & have done, or why the USB is RO (read only) as you've not made it clear how it was mounted (*was it mounted READ ONLY so you can't write to it?  or did it become RO because errors were detected?*) nor what exactly you tried to do.

Some drives can still work after 20 years.. yet others that operated in the same machine, or in different machines in the same room can last 2-3 years.. its hard to predict. All *spinning rust* drives eventually rust away though and will fail.

---

### Post by oldfred on 2024-05-31
You have never mentioned what format the USB flash drives are?
If NTFS, is it locked by Windows fast startup or hibernation?
Post this:
sudo parted -l

---

### Post by currentshaft on 2024-05-31
The solution to your problem is most likely:

sudo mount -o uid=1000 /dev/device /mnt

or simply

sudo chown -R $USER /mnt

To properly mount the USB drives.

---

