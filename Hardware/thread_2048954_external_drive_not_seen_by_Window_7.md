---
title: "external drive not seen by Window 7"
date: 2012-08-27
forum: Hardware
---

### Post by Calcrest on 2012-08-27
Good afternoon;

I have a Toshiba Satellite A200 TJ6; 2gb RAM; Intel Core2 Duo 1.5ghz; 32 bit OS 7 Pro.
I've downloaded Ubuntu 10.04 to CD. I checked the CD contents and it  would seem, to the best of my knowledge, all the files are there. What I did is install 10.04 on an external 160gb usb hd which has been formatted NTFS using the window 7 Pro. As of late, I've upgraded Ubuntu to 12.04 and have been using 12.04 for approximately a month. 

My network is high speed ADSL and I'm using wireless access through my internet provider high speed modem.  

I was downloading data, using Ubuntu 12.04 and had the 160g hardwired to the wireless modem, which was connected to the Toshiba Satellite.  I usually do my data downloads wireless; however, this time I tried the hard wire approach, hoping to get a faster download.  The next sequence is a step by step of what I remember I did prior to the issue that is present.  I shut down Ubuntu and disconnected Ubuntu from the computer.  All I needed was Windows to do some on line work.  The 160g is still hardwired to the modem and running.  When the 160g is running it has a led that lights as blue; when the drive is being accessed and therefore, transferring data either to or from the internet or accessing applications within Ubuntu, the led shows as a different colour to demonstrate that the drive is being active.  When the drive is hardwired to the modem, the led is showing that the drive is being constantly accessed and therefore, somehow data is being transferred on the drive even though Ubuntu has been shut down.

A day or two later I came back to the main floor room to recover the 160g and found that it had been unplugged.  To clarify, the 160g is not connected to a computer over those couple of days. So now an issue has occurred; Windows doesn't see the 160g drive at all.  


My questions:
1. Is the 12.04 OS corrupted because of sequencing evens?
2. Should I have, shut down Ubuntu, shut the drive off and then disconnect the modem, or shut down Ubuntu, shut down the drive and then disconnect the drive from the wireless modem?
3. Why, when the 160g is hardwired to the wireless modem it appears that its drive is being accessed on a constant basis, even though the 160g isn't connected to a computer?
4. If Ubuntu is corrupt, is there a utility that might recover the environment, or do I have reinstall 12.04?
Thanks for your time.
Calvin

---

### Post by ajgreeny on 2012-08-27
I really don't understand anything you say, I'm afraid, as none of it makes a great deal of sense to me.

Firstly, you can not install Ubuntu to an ntfs partition; it has to be a linux file system format such as ext#, ext4 is the default.  An ext# formatted partition can not be seen by windows, which may explain why your external drive is no longer seen by Windows 7, as it will have been formatted to ext4 when you installed Ubuntu
> I was downloading data, using Ubuntu 12.04 and had the 160g hardwired to  the wireless modem, which was connected to the Toshiba Satellite.  I  usually do my data downloads wireless; however, this time I tried the  hard wire approach, hoping to get a faster download.  The next sequence  is a step by step of what I remember I did prior to the issue that is  present.  I shut down Ubuntu and disconnected Ubuntu from the computer.   All I needed was Windows to do some on line work.  The 160g is still  hardwired to the modem and running.  When the 160g is running it has a  led that lights as blue; when the drive is being accessed and therefore,  transferring data either to or from the internet or accessing  applications within Ubuntu, the led shows as a different colour to  demonstrate that the drive is being active.  When the drive is hardwired  to the modem, the led is showing that the drive is being constantly  accessed and therefore, somehow data is being transferred on the drive  even though Ubuntu has been shut down.You certainly have lost me with this paragraph.  How did you hardwire a USB drive to a wireless modem, and what OS were you running when you saw this strange sequence of coloured lights?

PS:  A sudden thought!   Did you install Ubuntu to the usb drive using wubi, ie, were you running Windows 7 and installed Ubuntu as if it were a windows program, choosing the usb drive to install to?

---

### Post by Calcrest on 2012-10-01
Good evening ajgreeny and my apologies for the lateness of this.   However, I figured it might be best if I trouble shoot my issue as best  as possible before replying to your answer.  What I found was that the  case that housed the external drive was faulty.  Something with the  internal board within the external case.  I took the external drive and  case to a local computer shop and had them do some investigation on the  hardware and sure enough it was the case itself, not the drive.  Consider this solved.

So  I apologize for the confusing message above, and for my tardiness on  this reply and at this point I have bought another external case,  installed Ubuntu 12.04  drive into the case and voila it works likes a  charm.  So... thanks again, Calcrest.

---

