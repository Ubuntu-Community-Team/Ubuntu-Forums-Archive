---
title: "Ubuntu Dual boot problem Error 13"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by lefunker on 2009-07-19
Ok, I have a big problem.  I have been playing around with Ubuntu on my work laptop.  I made a new partition on my internal HDD, and I was dual booting between the systems.  Then I tried to clone the partition that had Ubuntu on it to a USB drive.  Useing these instructions to the "T"

[http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/)

After doing that I booted to XP and used Acronis to delet the partion that had Ubuntu on, and extend the XP partion to fill the unused space.  

After doing that I am getting "error 13 invalid or unsupported executable format" when select XP from my list of options. 

Also, I would like to be able to boot my system with out having to have to USB drive pluged in.  It thought I would be able to plug the USB drive into any computer that supports USB boot, and run Ubuntu off that drive.

Please help, I have to go to work soon, and I need my XP working!!!
Thanks

Matt

---

### Post by stlsaint on 2009-07-19
sounds like you jacked up your partitions during the clone to usb...i cant give a full assesment without more info but sounds like you need to correct your mbr on your xp partition..use acronis boot or hirens or try the xp disc...some have repair option for mbr thru cmd prompt!! but since the only os you have now is XP i would assume thats what you need to do then you can fix the ubuntu partition in which im not thinking the partition clone to usb was such a good idea without more experience and a larger drive such as ext hdd!!!

---

### Post by lefunker on 2009-07-19
I am not sure if I understand you right, but the ubuntu os of my USB HDD is working fine.  I dont care what happens to that os.  Its the XP os that is not working.  I am not sure if I have the install disks for my Toshiba Laptop or not I will check.  IF there is any info that I can post to help please let me know.

---

### Post by lefunker on 2009-07-19
One other thing.  When I boot with out the USB HDD attached I get something like the following:

Loading grub 1.5
grub loading 
error 17

Any thoughts?  I would love to just get rid of whatever it is that is making it dual boot, and just go straight to windows.

THanks

---

### Post by confused57 on 2009-07-20
Maybe this will work for you:
[http://members.iinet.net.au/~herman546/p18.html#Replace_GRUB_in_MBR_with_ms-sys](http://members.iinet.net.au/~herman546/p18.html#Replace_GRUB_in_MBR_with_ms-sys)

If you use your USB ubuntu(or the live cd), you might want to see how your Window's internal drive is recognized when booted into the USB ubuntu by running:
```
sudo fdisk -l
```
You want to make sure you're installing to the correct drive's mbr.

---

### Post by varun1786 on 2009-07-20
grub gives you the error 17 when it cant find a particular partition or the partition is not where it should be. 

When u removed the usb drive grub cannot find the ubuntu partition hence the error.

You should reinstall the windows boot loader on the mbr since u dont have ubuntu on ur hdd anyway. 

1. Put XP Disc in drive 

2. Startup PC

3. Let the PC boot from the CD

4. Choose the Recovery Console 

5. Type you XP admin username & pass if req

6. Once ur at the command prompt type

                       c:\> Fixmbr

             or if that doesn work try

                       c:\>fdisk /mbr

7. Restart the computer and eject the disk. It should work properly now

If u want to boot of the usb into ubuntu change ur boot options in the bios

---

### Post by lefunker on 2009-07-20
If fixed it using the XP Recovery Console.  Using the command fixmbr and fixboot.  Thanks for everyone's input.

---

