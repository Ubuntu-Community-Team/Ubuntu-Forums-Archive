---
title: "Sierra AC860 problems"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by holyowned on 2006-12-17
I have a Sierra Wireless AC860 card.  I can't get online with it.  I emailed Sierra, and got their disclaimer about "We don't support Linux, but here's a fix".  

[http://mycusthelp.com/sierrawireless/supportfaq.asp?sSessionID=&lstFilter_a=19&txtCriteria=linux&submit=Search&lstFilter_b=26&optCond=1&lstFilter_c=-1](http://mycusthelp.com/sierrawireless/supportfaq.asp?sSessionID=&lstFilter_a=19&txtCriteria=linux&submit=Search&lstFilter_b=26&optCond=1&lstFilter_c=-1)


Downloaded the tar file, and hit a wall with step 1......it says locate the file serial_cs.c, and make sure the card info is there.  No such file on my system.  The closest I have found are serial_cs.ko, which I can't open in a text editor.  If I run pccardctl info, it recognizes the card, but dmesg |grep tty returns nothing, just the command prompt (sorry for DOS terms).  I have KPPP installed, and got my ISP to help me try to configure it.  But the modem is busy when it is assigned to ttyS0, not found on the others I have tried.  Running wvdialconf create shows no modem.
TIA

---

### Post by jhudson on 2006-12-18
> **holyowned said:**
> I have a Sierra Wireless AC860 card.  I can't get online with it.  I emailed Sierra, and got their disclaimer about "We don't support Linux, but here's a fix".  

[http://mycusthelp.com/sierrawireless/supportfaq.asp?sSessionID=&lstFilter_a=19&txtCriteria=linux&submit=Search&lstFilter_b=26&optCond=1&lstFilter_c=-1](http://mycusthelp.com/sierrawireless/supportfaq.asp?sSessionID=&lstFilter_a=19&txtCriteria=linux&submit=Search&lstFilter_b=26&optCond=1&lstFilter_c=-1)


Downloaded the tar file, and hit a wall with step 1......it says locate the file serial_cs.c, and make sure the card info is there.  No such file on my system.  The closest I have found are serial_cs.ko, which I can't open in a text editor.  If I run pccardctl info, it recognizes the card, but dmesg |grep tty returns nothing, just the command prompt (sorry for DOS terms).  I have KPPP installed, and got my ISP to help me try to configure it.  But the modem is busy when it is assigned to ttyS0, not found on the others I have tried.  Running wvdialconf create shows no modem.
TIA
Hi, I just gotmy card to workon a Dell D820 machine and I think if you use the first support file  and save it to your home directory and unzip it with archive manager ( i am using gnome) on Edgy.
I found a couple of errors in his setup. One is the phone number. I use Cingular and the phone number is *99***1#.
I also added SW_8xx_SER.dat to /etc/pcmcia/cis and then my wvdialconf create, or wvdialconf wvtest worked.
I then used gppd to confiure my login and passwd to connect .
I haven't fooled around with my chat script but it still logs in and connects.
After about 10-12 hours I finally got it to work. Woopie
I hope this helps.

---

### Post by holyowned on 2006-12-19
I am not sure of the terms for the versions of Ubuntu.  I purchased The Official Ubuntu Book, with the disc, installed, and then updated.  My service is with Cingular, and when I called them, I asked for help installing this card under Linux.  None of the leaping through hoops for tech support - went straight to a Linux user who has this card.......and hasn't gotten it installed yet.  We spent a couple hours trying to set it up in KPPP.  I will take a look at GPPD when I can get access to my office LAN, in case I need to update/download something.  I have tried both of the workarounds listed by Sierra, but as I say, when I run wvdialconf create, it says I have no modem.  And dmesg |grep tty returns nothing at all. I have copied the DAT file you mentioned mentioned to that directory.  I know it is something very simple I am missing somewhere.  Thanks for the encouragement.  At least I know it IS possible to use this card under Linux.

---

### Post by Makyver on 2007-01-04
[http://makyver.blogspot.com/2007/01/ac860-and-linux-udev.html](http://makyver.blogspot.com/2007/01/ac860-and-linux-udev.html)

 AC860 and Linux UDEV

Ok so go get the SW_8xx_SER.dat file from Sierra wireless and then copy it (renaming it in the process to) /lib/firmware/SW_7xx_SER.cis this tells the Kernel what the card is and sets it up as a serial device you can then use as a modem for the rest of the steps on Sierra's Linux how-to page ... you don't need to mess with any card utils for this card after that ... just deal with the pppd stuff and it will all go well ... Oh make sure it's not flashing orange it will not function properly when orange. Pull and re-insert it if it's orange it make even take a reboot with the card already inserted make sure you have used the card at least once under windows somewhere or it will still be locked and there isn't a way to unlock it under linux yet. Oh and it won't work until a reboot the first time if you stuck it in before you copied the file.

---

### Post by holyowned on 2007-01-05
Makyver, have yourself a drink of your favorite beverage on me.  That worked beautifully, and so easily.  First time Ubuntu has recognized my card.  It logged on, and dropped immediately, with an error code 1, but I feel much closer to telling Windows 'Buenos Tacos, burrito'.  Thanks a bunch.

---

### Post by holyowned on 2007-01-05
Edited my /etc/ppp/peers/kppp-options file to remove the # on the noauth line, and solved the error code 1 issue.  Now it connects, sends 78 bytes, receives 129 bytes, and just stops.  Says it's active, and the timer shows I am connected, just no data transfer.

---

### Post by Makyver on 2007-01-08
Well I'm using KPPP and didn't edit anything in my etc for it just set up KPPP to do the dialing when every I need to use the card which lucky for me isn't to often but works great when ever I need it to ...

---

### Post by holyowned on 2007-01-08
After editing the kppp-options file, my card would connect, but stop.  I rebooted, and the card was not recognized (booted with it inserted).   I popped it out, re-inserted it, and it picked up fine.  After that one incident, Ubuntu does not seem to care if the card is in or out when I boot, it just grabs it and goes when I launch kppp.  Thanks again for a super-simple help.

---

