---
title: "USB Driver issues..."
date: 2009-01-21
forum: Hardware
---

### Post by Excedio on 2009-01-21
Hey Everyone,

Last Friday I was playing with Skype, testing it out with my brother and such. Afterwards I tried to access a USB Memory Card Hub to transfer some pictures to my External Hard drive. During the process USB would stop working.

At first I thought whole computer was freezing up since my wireless mouse and keyboard are also USB, not the case. I plugged in and older mouse and keyboard that I had lying around and they worked fine.

Then I thought, maybe this is a hardware issue. Maybe I shorted out something. I popped in an Ubuntu Live CD and tested out my USB, worked perfectly.

This leads me to believe that the problem is my USB driver. Possibly one of the Linux Updates altered my Kernal or USB Driver.

I use many USB devices at one time, for one reason or another...

[I]*Dynex (DX-4P2H) 4-Port USB Hub
*Dynex All-In-One Card Reader (DX-CR121)
*Logitech Quickcam Pro 4000
*Western Digital WDH1U5000N 500GB My Book Essential Edition USB External Hard
*Canon Pixma MP460
*Logitech Cordless Desktop® S 510[/I]

I'm running 8.04. Any help please...

---

### Post by Excedio on 2009-01-22
Help.....please...

---

### Post by Excedio on 2009-01-23
If anyone knows anything about Linux USB Drives...please respond

---

### Post by birddog165 on 2009-01-26
Hey man I'm feeling your pain. I've got the same problem:
[http://ubuntuforums.org/showthread.php?t=1049488](http://ubuntuforums.org/showthread.php?t=1049488)

And nobody has been able to help me yet which sucks because all my music is on my external HDD.

I'm gonna keep checking this post because I want to figure out what's going on too.

---

### Post by Excedio on 2009-01-26
Thank God I'm not the only one out there with this problem. I'm on the verge of formatting my hard drive and re-installing Linux. I really don't want to do this, but the problem is quite bothersome.

Anyone out there have any idea how to resolve this problem?

---

### Post by birddog165 on 2009-01-26
uh, I wouldn't try that. I mean unless you really really really want to. There has to be a solution.

I found this thread right before I went to sleep yesterday, and it may be of some assistance, however, I have yet to try it myself:
[http://ubuntuforums.org/showthread.php?t=778136](http://ubuntuforums.org/showthread.php?t=778136)

The 5th post is something I'm interested in. It talks about some sort of standby mode.

---

### Post by Excedio on 2009-01-26
Trust me...a re-install is an absolute and complete last resort.

I'll try this out tonight when I'm with my tower. Normally I could do this remotely, but I just happened to leave my Linux powered laptop at home today.

Thanks for the referral.

---

### Post by birddog165 on 2009-01-28
Just a quick question? By any chance do you have any virtualization software (ie. Parallels, VirtualBox, etc) installed?

---

### Post by Excedio on 2009-01-29
I do. I have the Sun xVM VirtualBox.

---

### Post by birddog165 on 2009-01-29
> **Excedio said:**
> I do. I have the Sun xVM VirtualBox.

I think that the problem might be related. But I don't know how or why.:(

---

### Post by Excedio on 2009-01-30
> **birddog165 said:**
> I think that the problem might be related. But I don't know how or why.:(

What makes you think that it's related? If it is...i have no problem removing the program.

---

### Post by birddog165 on 2009-01-30
> **Excedio said:**
> What makes you think that it's related? If it is...i have no problem removing the program.

See that's the problem. I woke up and found that I had jotted that down on a post-it right before I fell asleep. I wrote "The problem is virtualbox." And it's funny because that was suppose to remind me why it was the problem and I don't know why.

Let me check my internet history and see if I ever came across something....
I just can't believe that I can't remember why.

---

### Post by birddog165 on 2009-01-30
You know, the more I look into this, the more the virtualbox thing makes no sense. And I don't remember doing anything to it. This is probably related to me changing the kernel. I'm gonna look for a way to find the exact changes that I made.

---

### Post by birddog165 on 2009-01-30
Ah ha, my entire logic behind blaming VirtualBox was simply because I didn't have the problem before it! So I don't know what has fixed my problem. Go figure.

---

### Post by theozzlives on 2009-01-30
Try using your old kernel.

---

### Post by birddog165 on 2009-01-30
> **theozzlives said:**
> Try using your old kernel.

Lolz, I could do that... give me a few hours to get out of class ;)

---

### Post by Excedio on 2009-01-30
> **birddog165 said:**
> You know, the more I look into this, the more the virtualbox thing makes no sense. And I don't remember doing anything to it. This is probably related to me changing the kernel. I'm gonna look for a way to find the exact changes that I made.


I love having you on the case dude. When I read this and the post before it, it really makes me laugh.I do the same kind of thing all the time. Figure something out when it's 4am and I'm tired as all hell, then I wake up the next day without a clue of what I did the night before to fix it!


[QUOTE=birddog165]

Quote:

Originally Posted by theozzlives
Try using your old kernel.

Lolz, I could do that... give me a few hours to get out of class [/QUOTE]

Let me know when you have tested this out.


[QUOTE=birddog165]...This is probably related to me changing the kernel... [/QUOTE]

How did you change the kernel? by removing your VirtualBox?

---

### Post by Excedio on 2009-01-30
> **theozzlives said:**
> Try using your old kernel.

Holy moly! Thank the Linux gods that someone else is actually reading this thread, and ACTUALLY POSTED! :D

---

### Post by Excedio on 2009-02-05
So how did you change your Kernel? I would really love to get my box fixed...

---

### Post by birddog165 on 2009-02-07
Just look on google for "how to compile a custom kernel in ubuntu"

---

### Post by xinman on 2009-02-07
I too am having this same issue, and I also have virtualbox installed.  Has anyone confirmed a fix for this?  I am about to put XP back on my desktop and continue to leave linux for server use as this has really created some issues for me.  Any help would be appreciated.

Thanks,
Dan

---

### Post by birddog165 on 2009-02-08
So I changed the kernel, just by clicking on the old one in GRUB when it loads up. Everything works fine. I have to say, leave them kernels alone for now. I think that virtualbox was the problem. Everything works great for me now. I wish I knew why, but it just does.

---

### Post by whitej125 on 2009-02-11
What kernel version introduced the problem?  I recently ran into the same issue with Intrepid (had it working for a week, then USB died).

Switching to older kernel versions in grub doesn't help me though.

---

### Post by Excedio on 2009-02-11
I personally have not got a clue what kernel version introduced the problem, but I do know that I currently run kernel 2.6.24-23-rt. I added a new repository today that produced some new updates for me including these two...

linux-ubuntu-modules-2.6.24-23-generic (2.6.24-23.36) to 2.6.24-23.37
linux-ubuntu-modules-2.6.24-23-rt (2.6.24-23.36) to 2.6.24-23.37

I'm going to test now to see if the problem persists....*crosses fingers*

---

### Post by Excedio on 2009-02-11
Well....2.6.24-23-rt didn't solve the issue...

---

### Post by whitej125 on 2009-02-16
Crud, just booted with the 8.10 live CD and USB is still not working.  Either the problem persists with this version or my usb ports are all dead?

Odd thing is, looking at my dmesg, it appears as if the USB hubs are detected... but none of the attached devices (such as my Microsoft Intellimouse)

$ dmesg | grep usb
[    2.723139] usbcore: registered new interface driver usbfs
[    2.723188] usbcore: registered new interface driver hub
[    2.723630] usbcore: registered new device driver usb
[    2.796250] usb usb1: configuration #1 chosen from 1 choice
[    2.900800] usb usb2: configuration #1 chosen from 1 choice
[    3.004735] usb usb3: configuration #1 chosen from 1 choice
[    3.108704] usb usb4: configuration #1 chosen from 1 choice
[    3.212930] usb usb5: configuration #1 chosen from 1 choice


$ dmesg | grep hub
[    2.723188] usbcore: registered new interface driver hub
[    2.796314] hub 1-0:1.0: USB hub found
[    2.796329] hub 1-0:1.0: 8 ports detected
[    2.900854] hub 2-0:1.0: USB hub found
[    2.900867] hub 2-0:1.0: 2 ports detected
[    3.004784] hub 3-0:1.0: USB hub found
[    3.004801] hub 3-0:1.0: 2 ports detected
[    3.108764] hub 4-0:1.0: USB hub found
[    3.108778] hub 4-0:1.0: 2 ports detected
[    3.212978] hub 5-0:1.0: USB hub found
[    3.212994] hub 5-0:1.0: 2 ports detected


$ dmesg | grep mouse
[    1.942394] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.948235] mice: PS/2 mouse device common for all mice


$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by xinman on 2009-02-23
Ok, well this make work for you, it did work for me.

In my dmesg output it said:
```

[   47.070084] irq 20: nobody cared (try booting with the "irqpoll" option)
[   47.070089] Pid: 3379, comm: modprobe Tainted: P        2.6.24-23-generic #1
[   47.070097]  [<c0169214>] __report_bad_irq+0x24/0x80
[   47.070104]  [<c01694eb>] note_interrupt+0x27b/0x2c0
[   47.070108]  [<f88b8ccb>] usb_hcd_irq+0x2b/0x60 [usbcore]
[   47.070124]  [<c0168710>] handle_IRQ_event+0x30/0x60
[   47.070127]  [<c0169ea6>] handle_fasteoi_irq+0x86/0xe0
[   47.070130]  [<c0106f0b>] do_IRQ+0x3b/0x70
[   47.070133]  [<c01929a1>] sys_read+0x41/0x70
[   47.070137]  [<c0105403>] common_interrupt+0x23/0x30
[   47.070143]  =======================
[   47.070144] handlers:
[   47.070145] [<f88b8ca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   47.070157] Disabling IRQ #20

```

so in grub I added irqpoll to the end of my kernel line.  That's it, it worked.  

Boot options howto: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

gsocker helped me out, I take no credit.

---

### Post by Excedio on 2009-02-24
Awesome thanks. I'll try this out and see if it works. Will post here with results.

---

### Post by Excedio on 2009-02-24
Unfortunately I don't have that message in my dmesg output. Sigh...

---

### Post by whitej125 on 2009-02-25
irqpoll is already turned on for me

Quick question to the forum.  One would expect that when I plug the USB mouse into the machine... a message would appear in dmesg.  Well, nothing does.  

What service is responsible for detecting USB devices connecting and disconnecting?

---

