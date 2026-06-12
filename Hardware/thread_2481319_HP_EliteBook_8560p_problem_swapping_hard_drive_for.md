---
title: "HP EliteBook 8560p problem swapping hard drive for ssd"
date: 2022-11-25
forum: Hardware
---

### Post by jgw on 2022-11-25
I have a HP EliteBook 8560p  which Is a bit elderly.  I thought I would try to replace the hard drive with an ssd to speed it up a bit. I currently have ubuntu installed on the hard drive and it works fine.  I have 22.04 on a memory stick that I use when I am installing ubuntu.  Never had a problem.  I swapped out the drive with a 1tb ssd chip.  The machine had a sata connection so I figure it was work.  I then used the built in tests.  I was able to test the ssd I had and it told me is was just fine.  I also had it tested for started and, again, it said it was fine.  I then plugged in the memory stick with 22.04 Ubuntu and chose to start with the usb stick.  It had no problem doing that and I installed ubuntu onto the ssd.  There were no strange notifications and no problem.  I told it to erase the ssd and install ubuntu 22.04.  There were no problems and then it told me it was done and to restart the computer.  I removed the usb stick and did a re-boot.  during the initial boot I pressed esc and told it to boot from the system hard drive.  After some time I was told that I had to have a boot program on the hard drive.  I removed the ssd and took a look to see what was there and it looked good to me.  All the stuff had been put on the ssd.  

So, I think I am missing something but have no idea what it might be.  I have reinstalled the 33gb drive (it was a really small one) and turned on the machine and its working fine, but I failed with the ssd.

I would appreciate any thoughts on this one as I have no idea what I might have done wrong.

Thank you....................

---

### Post by yancek on 2022-11-26
>   I swapped out the drive with a 1tb ssd chip

When you installed Ubuntu to the SSD, had you removed the original drive?
How old is the computer, meaning is it a Legacy install or a UEFI install?
Did you accept the default install of the bootloader during the installation of Ubuntu?
When you rebooted, did you have only the SSD attached?


>   during the initial boot I pressed esc and told it to boot from the system hard drive   

Do you see any other options to boot when you are in the BIOS?

---

### Post by jgw on 2022-11-26
Thank you for the reply!

Yes, I removed the existing hard drive and replaced that with the ssd.  Oh, in case I forgot, the existing hard drive had ubuntu 22.04 on it already.

How old is the computer, meaning is it a Legacy install or a UEFI install?
This is a pretty old laptop but it runs good.  I bought it on ebay about 5 years ago.  
I have no idea what the difference between legacy and UEFI.  
What I did was put the gps install stick in and booted from it and then choose to install rather than try.  I assume that was the default install.  I also choose to delete everything that might be on the ssd (I suspect nothing was on it).  I also had it test the ssd to see if it was OK and it thought it was.  

When you rebooted, did you have only the SSD attached?   The ssd was plugged in where the hard drive once was.  

I am not sure that I have ever even been in the bios.  I will have to check on that one.  This machine is different that others in that it has some stuff that's just questions to be answered.  I have now put it back together with the drive I removed and that worked fine.  Would still like to try the ssd but the machine thinks that it has no boot on it.  The ubuntu installation was complete and I got the not about no boot message  on the ssd (I think) when I let it re-start after I took out the usb stick.  I am not even sure what it was booting from.  The only thing in that machine was the ssd, however, and there was no other place for it to go when booting up.  I have done this with 2 other machines and everything was, and is, dandy. 

Its a mystery to me.  I could take that usb stick and put it into another machine and give that a try.  I just thought about that, I'll give that a shot tomorrow just to see what happens - can't hurt anything (I think).  I have also tested my gps install stick just to make sure nothing happened there.  They are pretty easy to make.  I could make another just to make sure as well. 

Thanks again!

---

### Post by jgw on 2022-11-27
I tried the offending ssd on another system.  The system was an hp but desktop not a laptop.  Anyway, it booted up just fine! So, I suspect I have some kind of a bios problem.

I am now in the bios and the boot options

fast boot is turned off
boots checked:
cd rom
sd card
pxe internal NIC boot
upgrade bay hard drive boot
eSATA boot

Legacy Boot Order
usb cd-rom
notebook upgrade bay
notebook hard drive
usb floppy
usb hard drive
notebook ethernet
sd card
eSATA Drive

One would think that means that one of those have to be the ssd.

Just tried again got:
bootdevice not found
please install an operating system on your hard disk
hard disk (3F0)
f2 system diagnostics
For more information, please visit: [www.hp.com\go\techcenter\startup](www.hp.com\go\techcenter\startup)

Suggested I goto f2 and test the hard drive.  I went there and it immediately started a memory check.  I will finish that and move on.......

This laptop is 11 years old!!

The machine went through 4 or 5 tests, including the hard disk and then gave options to run any one of them.  I choose the hard disk test and its running right now.  Oh, it just said that its now doing test 2 (comprehensive).  I think the automatic tests were the quick ones.  The comprehensive test also passed.  The tests that were run:
start-up
run-in
hard disk

So the hard disk is dandy 

When booting it gives the client address
While trying to boot I saw a message - it went fast but:  "px3w5e no boot filename received" 

in he system configuration I do not see the ssd/hard disk.  The connection for the ssd looked to be a sata connect the sata device mode is AHCI

I have no idea what the 3F0 means on the hard disk: hard disk (3F0)

I have tried all sorts of stuff but nothing is making any difference!  As far as I can tell everything is fine in that all tests were passed.

On the boot list I moved the hard disk and the sata disk to the top - no difference. 

I suspect I am going to have to give up.

I did a search in the forum and found "https://ubuntuforums.org/showthread.php?t=2476367&highlight=HP+EliteBook+8560p" where somebody had the same problem and they then installed ubuntu 20. and that worked!  That will be my next adventue.

---

