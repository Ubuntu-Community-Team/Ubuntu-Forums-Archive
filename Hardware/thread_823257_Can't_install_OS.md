---
title: "Can't install OS"
date: 2008-06-09
forum: Hardware
---

### Post by ronti69 on 2008-06-09
Hello,
I have a laptop that has no CD, no floppy, only one IDE and a couple of USB port. This thing used to boot from a ROM that it no longer has. The BIOS doesn't allow booting from USB. The IDE is used by a hard drive with no OS. I can't even boot. I tried putting the hard drive in another computer, installing Puppy or Xubuntu, then re-installing the drive in the laptop. Didn't work. 
Can anybody please help?

---

### Post by jespdj on 2008-06-09
Do you have a manual for the laptop? If not, try finding a manual online. There must be a way to install an OS on the laptop, and the manual most likely explains how.

Don't the BIOS settings offer a way to boot from something else than the harddisk?

What brand and model is the laptop? The more information you provide, the more likely it is that there's someone who might be able to help you.

---

### Post by ronti69 on 2008-06-09
The machine is one of those touchscreen terminals that they use at self checkouts in some stores. I bought it from craigslist and had no hard drive in it. It is basically a laptop board with a Celeron processor and 256 Mb RAM.
It used to boot XP from a ROM, which it no longer has. It has a serial port, 2 USBs, an PS/2 keyboard port and an ethernet port.
The board has one IDE, to which I connected a laptop hard drive.
I tried installing Puppy linux on the drive in another machine, then swapping the drive, but it didn't work. The graphical interphase didn't start, but I am not sure whether puppy booted or not. It gives me an error message saying "pup400.sfs not found" and "running into ramconsole mode". Then I get what I think is a command prompt (#) but since my knowlege of Linux = 0 I don't know what to type. If I read the drive in another machine, pup400.sfs is there, though.

Hope someone can help. Thanks a lot for reading

---

### Post by WhyAreWeRunning on 2008-06-09
This might be a stupid question but is there a slave channel for the IDE, cause if there is hook that up to a cd drive.

---

### Post by ronti69 on 2008-06-10
No, unfortunately it doesn't have a slave channel

---

### Post by ugm6hr on 2008-06-10
> **ronti69 said:**
> I tried putting the hard drive in another computer, installing Puppy or Xubuntu, then re-installing the drive in the laptop. Didn't work. 

Did you try this: [http://ubuntuforums.org/showpost.php?p=3956118&postcount=6](http://ubuntuforums.org/showpost.php?p=3956118&postcount=6)

---

### Post by ppc_guy on 2008-06-10
More to the point. What is the make/model of the POS system you are dealing with. Having some experiance in this area, there are some that are really stand alone computers. While other depend on the os contained on the inbedded rom and never really "boot" from the hd. The internal drive is only there for saving needed data and what not. So you might have a unit like this and in that case you'd be looking @ one hell of a hack to get linux or any other os on it.

---

### Post by haylun98 on 2008-06-11
Each IDE port should support upto 2 devices. You might need a standard IDE cable like those supplied with motherboard. Set the jumpers on your hard disk as master and on IDE CDROM drive as slave.

Hope this get you started booting CD to install OS

---

### Post by ronti69 on 2008-06-13
OK, thanks to all the help I got from all of you I have been making what I consider some serious progress! The system still doesn't boot...but I've been learning a lot. So here's the situation now:

I installed Xubuntu by popping the hard drive in a Dell Inspiron 6000 laptop. Installed OK, booted without a glitch. Then I took the hard drive and put it in my target machine. Got the Grub screen and choose the first option. Got several screens of text quickly scholling up, then a black screen, then the nice Xubuntu screen with the progess bar... my heart pumping out of my chest...progress bar actually making progress...yes I did it... progress bar is done... black screen! Nothing but a blinking cursor. Waiting a "long"time. still nothing.

So I rebooted and now chose the second option (Recovery mode). Again all the text too fast to read and then a system prompt. Great! Only that... I don't know one single linux command!! There was an error message:

*unable to start xserver*

So I went on line, read a lot, understood a little, and after 2 days went back and proudly typed:

*startx*

There you go! Take that, Xubuntu!

In less than 2 nanoseconds it spit back:

*Fatal server error. No screen found*


So what do I do now? As far as I understand, the Xfce thing (is it called a graphic window server?) is not working. I am not surprised, it is expecting the nice video card and widescreen in the Dell. How do I make it realize it is not in the Dell anymore?

Well this is quite a long post. Sorry about that. Thanks for reading, any help appreciated.

---

