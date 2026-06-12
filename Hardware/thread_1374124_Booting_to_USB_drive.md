---
title: "Booting to USB drive"
date: 2010-01-06
forum: Hardware
---

### Post by Stevo0687 on 2010-01-06
Hey all!

I have tried to get my Logitech Webcam to work with Ubuntu 9.10 which I then wanted to share with my VirtualBox Windows 7 to use with a program in Visual Studio that I'm working on for a class project; however, that did not go well.

Anyway, I may give it another shot eventually, but for now I want to try something that I feel should work "smoother."  I have a 2.5" IDE to USB external enclosure with a 40GB external hard drive.  I would like to just install Windows on there and boot to that when I need to work on my project and use my webcam (currently, I don't need the webcam and may be able to work in the Virtualized Window, but eventually I'll need to use the webcam).

I have a Dell Inspiron E1405.  When I turn the computer on I can press F12 for other boot options, but I don't see anything for USB.  I read somewhere about possibly turning on USB settings.  I've never heard of that, but if I need to do that, could someone explain it to me?  I've also read about maybe being able to use GRUB to boot to USB.  If that is the case, can I use it to boot to a Windows hard drive (I would guess so because I've used GRUB to dual-boot before).  If I can, could someone guide me in how to do that or point me to a good tutorial explaining it.

Basically, I'm wondering what the best method would be for me to boot to my USB HDD.  

I know that if I don't end up using GRUB this isn't much of an Ubuntu or even Linux question, but I find the people on Linux forums to be more knowledgeable and since GRUB may be an option, I felt this was the best place to come to.

Any guidance would be greatly appreciated. Thanks in advance.

---

### Post by Danieljh75 on 2010-01-06
Stevo,

I'm not a linux pro but I do tinker and I did catch something in your description. You said that you looked at the boot options after you pressed f-12. Most of the times when you boot your computer, you'll see a dark screen with a logo or a message and something to the effect of push F-[some number] for boot option or push F-[some number] to enter set up.

Did you ever enter the set up and check your bios settings? On most modern computers (I presume in the past 2 years at least), you should be able to enter set up and then find the 'boot options, boot preferences, or boot order' within the bios set up. Sometimes you'll have to actually enable booting from USB devices before you can both see and select the USB device from the boot order. 

By going into the bios and enabling a boot from a USB device, you're basically giving permission to boot off of a hard disk or flash drive. I know for a fact that some motherboards have a bios that disables USB devices because it's a method that can be used to introduce malicious files onto an operating system (at least in the Windows world). For anyone else, that's not meant to start a flame war. I just know that I've worked with an admin in the past to disable that feature to 'further' secure multiple Microsoft environments. 

Point being, the boot options menu and the bios are two different places. You should be able to configure your bios, including the boot order for your devices. I typically would set it to boot in this order (just my personal preference): 

1. Floppy
2. USB device
3. CD
4. Internal HD.

I'm not a pro but maybe I just happened to catch one detail you may have overlooked. 

Best of luck to you Steveo,

Dan

---

### Post by Stevo0687 on 2010-01-06
Dan,

Thank you very much for the tips. I check that out and it is showing that it is set up to boot to USB; however, it still doesn't show up in "one-time-boot."  

Is it possible that it will only show if a properly formatted device is attached? I haven't set up a usb device with Windows yet to try that.  And I'd rather not do that and then have it not work. Is that a possibility or could I still be missing something?

---

### Post by Danieljh75 on 2010-01-08
Stevo,

I took some time to think about your second message with Windows on the external drive. I'm not sure why it will not boot from the second drive, but I did have a thought. Some USB drives requre a little extra power that the USB buss cannot deliver on some notebook computers as oppsed to a desktop box. Since the capacity of your external drive is 40GB, I am guessing that it could be around the time that most 2.5 HDs required that little bit of extra power to get the motor turning. Have you ever connected this drive with your system running from the Internal disk and been able to mount the drive that way (just to see that it works without a power adapter or the 'y' shaped USB plug)? 

That was the only thought that came to mind why it wouldn't boot from USB. As long as the computer can see that there is a drive there, I have another idea; however, I believe it will take an individual with more fluency in Linux than what I have. If you know that the drive is spinning up and is ready to be used, then perhaps you can do something to make grub recognize the drive. If I am to understand you correctly, you have Ubuntu on the internal disc currently and you should have Windows on the External. My idea is to somehow get grub to see that you have a Windows OS on an external disk. This would mean that when you start your computer, you would see a boot loader screen where grub would point to another disk and then you could pick which flavor of an OS that you would want to start up. Although, I think by the very nature of enabling USB in the Bios you would somehow bypass grub, which means that currently you may simply be having trouble with the USB device.

To tell you the truth, I think it would be easier to accomplish your task by doing the following:

1. Pop in a Live CD with Ubuntu
2. Make three hard drive partitions: 1st- large for Ubuntu, 2nd- small for ubuntu swap files, 3rd large for Windows.
3. Install Ubuntu on one partition and then also designate the small partition as the swap file.
4. Install Windows on the thrid partition. 

This way you should automatically start the system and you would be able to just use the arrow keys on the simple boot loader to pick your OS. I am using a notebook that was configured this way this morning but I finally wiped Windows and captured the entire disk with Linux today. If you are adamant that you want one system on the external and one on the Internal, you may consider Windows on the Internal and Ubuntu on the External as it seems that Linux is just more friendly that way. If you have the time and can afford a spare drive, I would put in the new drive and play with the steps mentioned above. You should be able to manipulate the partition sizes and the order of how you want everything to your liking without the worry of data loss. 

Again, I'm not an expert so I would encourage you to check with someone more experienced and wiser than I am. :)

Now, If only I could boot linux on my Macbook with my USB flash Drive without having to set up ReFit and reinstall everything, I'd really be happy!

Good luck Stevo,

Dan

---

