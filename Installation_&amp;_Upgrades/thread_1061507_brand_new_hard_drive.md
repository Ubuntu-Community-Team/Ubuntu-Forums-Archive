---
title: "brand new hard drive"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by Saraslife on 2009-02-05
I just got a new hard drive for my laptop and I need some help on how to get ubuntu back on my computer. I am starting completely from scratch. I had ubuntu before and my friend that installed it onto my computer the first time told me that i need a new hard drive and is now too busy to help me out. please help. thanks!

---

### Post by Partyboi2 on 2009-02-05
You can follow [[COLOR=Blue]this[/COLOR]]("http://www.ghacks.net/2008/12/12/an-illustrated-guide-to-installing-ubuntu-desktop/") guide to install ubuntu if you want ubuntu as your only operating system. If you are wanting to dual boot you can follow [[COLOR=Blue]this[/COLOR]]("http://www.psychocats.net/ubuntu/installing") guide.
If you get stuck post the problem and someone should be able to help.

---

### Post by Saraslife on 2009-02-06
my friend said something about drivers. That I might need a driver so my computer can read the cd. Do you have a link where i can find these incase the cd dosnt work. I have a dell inspiron 6000. thanks!

---

### Post by logos34 on 2009-02-06
You may want to get the Dell custom image (8.04):

[http://ubuntuforums.org/showthread.php?t=762770](http://ubuntuforums.org/showthread.php?t=762770)

---

### Post by Saraslife on 2009-02-06
so i downloaded ubuntu put it on a thumb drive and a cd and started my computer and i get an error. so i open up the setup and i look at device info, Primary hard drive: none. what did i do wrong?

---

### Post by taurus on 2009-02-06
You mean the BIOS doesn't even detect your new harddrive?

---

### Post by Saraslife on 2009-02-06
I dont think it does. when i exit the setup it says no bootable devices.

---

### Post by Therion on 2009-02-06
Okay, so you've installed this new, blank, and totally unpartitioned hard drive in your tower, correct?

You need to enter your BIOS setup and do a couple things.

1.  Make sure the new drive is being recognized and is listed in the boot chain.

2.  Set the boot sequence to boot from the optical (CD/DVD drive) drive first and the primary hard drive second.

You will not need to install drivers for your CD/DVD drive.  The BIOS will deal with it as a generic device initially.  I would suggest trying to boot/install from an Ubuntu CD if possible.

Booting from USB may, or may not, be an option for you.

---

### Post by Saraslife on 2009-02-06
i get internal hard disk drive not found. internal hdd hard error.

---

### Post by Therion on 2009-02-06
> **Saraslife said:**
> i get internal hard disk drive not found. internal hdd hard error.
Okay, that tells me nothing.  

Have you entered your BIOS setup to see if the drive is listed or not?

Please don't make me extract information out of you.

---

### Post by taurus on 2009-02-06
It means there is either something wrong with your new harddrive, the settings are wrong, or the cable is not securely plugged in.  You may want to open your computer and have a look.

---

### Post by Saraslife on 2009-02-06
yes i changed the boot sequence to
1. cd/dvd/cd-rw drive
2. internal hdd
3. USB storage device
4. diskette drive

---

### Post by Therion on 2009-02-06
Since you've set up your boot chain correctly, I am assuming your drive is being recognized by the BIOS. It is, however, possible to set your boot sequence and NOT have the hard drive be recognized by the BIOS, which is why I keep asking you if the BIOS is, in fact, recognizing your newly installed drive.  

So, once again, is the BIOS *correctly* identifying the new hard drive?

If so, attempt to boot from the Ubuntu LiveCD.

---

### Post by Saraslife on 2009-02-06
how do i figure out if it recognizes it?

---

### Post by Therion on 2009-02-06
Somewhere in your BIOS menu you're going to see something about "Standard CMOS Features".  All your drives will be listed there.  

See this screenshot: [http://www.bcot1.com/bios03.jpg](http://www.bcot1.com/bios03.jpg)

In that picture the "IDE Primary Master" is being identified; there is a brand name (Sanyo) and a model number (SP0411N).

What you see might differ slightly. If your drive is SATA, you won't see IDE Primary Master, you'll see SATA listed instead.  The important thing is that you see make and model information listed.  This indicates the BIOS is in communication with the device.

---

### Post by Saraslife on 2009-02-06
Primary hard drive: none. is that what im looking for?

---

### Post by Saraslife on 2009-02-06
i for got a piece of the hard drive and just added it on. now it says
Primary hard drive - 137 gb hdd

now i exit the setup and it says

no boot sector on internal hard drive.

---

### Post by Therion on 2009-02-06
> **Saraslife said:**
> i for got a piece of the hard drive and just added it on. now it says
Primary hard drive - 137 gb hdd

now i exit the setup and it says

no boot sector on internal hard drive.
Now we're getting somewhere.  Did you forget to attach the power connector?  It's happened to the best of us.

You're getting that error because there is no Operating System on the hard drive yet; you need to install one.

Put a LiveCD in the tray and restart the PC.  Your PC should boot from the LiveCD and allow you to install Ubuntu to the hard drive.

---

