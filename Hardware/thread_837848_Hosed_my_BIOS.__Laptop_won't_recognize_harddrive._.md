---
title: "Hosed my BIOS.  Laptop won't recognize harddrive.  Help!"
date: 2008-06-22
forum: Hardware
---

### Post by mart0224 on 2008-06-22
After fixing my niece's laptop for the third time because of malware I tried dumping XP for Ubuntu.  Unfortunately the Compaq Presario V5206 OA laptop has a Broadcom wireless chipset, so I will install Windows XP for now.  

Anyway, I messed up and for some reason the laptop will not recognize the hard drive.  Not sure when the problem started but it was AFTER I tried restoring with the Windows recover partition on the hard drive.  (BTW, I got pissed so that partition is now gone.)

On startup the laptop won't recognize the hard drive so it tries to do a network boot.  I reinstalled both Ubuntu and XP several times as both single and dual boot.  Tried repairing the MBR with the XP Recovery mode.  I then installed a brand new hard drive on which I subsequently installed XP.  The laptop still would not recognize the hard drive.  I then installed a drive with a working Xubuntu setup.  Still no go.  Through out all of these attempts I reset the BIOS settings to default.  Also, boot to hard drive is listed before network boot.

In the BIOS under boot setup, the partition under harddisk has an exclamation point next to it.  Not sure what that mean but I doubt it's good.

I'm a Mac guy who knows very little about Windows other than deleting it.  I am fairly comfortable with Ubuntu though.  Please help.

---

### Post by Zorael on 2008-06-23
The exclamation mark, while I've never seen a BIOS that could actually show such a thing, seems alarming, but I don't know what it means. If it's simply the MBR being busted, that can be fixed. Pop in a live cd, enable universe repositories, install the **testdisk** package and use it to install a vanilla MBR. This *assumes* that the device shows up in '**sudo fdisk -l**'.

If the bios is not getting the signals it expects from the device, there's the possibility of hardware failure. Check with another IDE/S-ATA/SCSI/fluffy bunny cable, and try another input "port" on your motherboard/controller. If you have a friend with a PC, try it in his computer and do the fdisk thing in a live cd environment.

---

### Post by matt.taylor on 2008-06-23
Im affraid it sounds like a dead Hard Drive:(

---

### Post by mart0224 on 2008-06-23
> **matt.taylor said:**
> Im affraid it sounds like a dead Hard Drive:(

I've tried one brand new drive and an old drive.  Even with those, the exclamation point shows up next to the drive listing in the BIOS.

---

### Post by Odrodzona-Sarmacja on 2008-06-23
Can you tell your bios it deals with a non plug and play os and to reconfigure itself? It sounds to me like a bios issue and not hd.

---

### Post by ukripper on 2008-06-23
If you look at manufacturer's website you may find a way to update the BIOS firmware but can be dangerous if things go wrong.

---

### Post by matt.taylor on 2008-06-24
Yeah get a stable version of your BIOS and then flash it. What type or drive is it that your trying to use?

---

### Post by mart0224 on 2008-06-24
Problem solved.

I did 'sudo fdisk -l' at Zorael's request.  It did find the drive which thankfully ruled out motherboard issues.  I then tried Zorael's other suggestion of using testdisk to reinstall an MBR but without success though  testdisk did indicate a problem with the MBR.  Perhaps I just didn't know how to use the app.

Out of desperation I then pulled the drive and connected it to my Apple MacBook Pro and rebuilt the MBR with the built in OS X Disk Utility.  This solved the problem.


Everyones' help and suggestions are appreciated.

Now to make the  laptop dual boot and install Ubuntu.  Hopefully I have better success with the Broadcom wireless driver.

---

### Post by mart0224 on 2008-06-24
> **ukripper said:**
> If you look at manufacturer's website you may find a way to update the BIOS firmware but can be dangerous if things go wrong.

The drive is the original–a Seagate.

Thanks for the tip because I did have to download several drivers from there because my Windows CD did not include them.

---

### Post by cdtech on 2008-06-25
FWIW......

I had the same problem from my HP dv series laptop. It would not show up in BIOS. I reset the BIOS to factory defaults and did my setups and now it detects the drive.

I'm still looking for a BIOS update from HP.

---

