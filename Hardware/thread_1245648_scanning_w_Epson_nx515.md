---
title: "scanning w/ Epson nx515"
date: 2009-08-20
forum: Hardware
---

### Post by Bio Leo on 2009-08-20
I'm in the market for an all-in-one printer-scanner-etc and the Epson nx515 looks interesting.  Does anyone know if it will scan under Ubuntu?  I've googled about and not found anything one way or the other, only that Epson scanners are *generally* well supported under linux.  I don't mind a bit of trouble to get scanning working, but I've been burnt by scanners that "just don't work in linux" (I'm looking at you Visioneer 8100) so I'm not going to pull the trigger on a purchase w/o knowing it will work.  Thanks!

**(edit: it works, mostly, see post below)**

---

### Post by JoelTheMole on 2009-08-20
I was just about to order one.  I came across this posting while doing the same kind of research.  From what I have read, the printing works fine (using the default nx400 Ubuntu driver).  The instruction manual on the Epson website seems to imply that the card-slot is accessible by CIFS/SMB (which should be accessible through Samba), and the scanning can, in the worst case, be accessible through email.

It should be here by next week.  I'll post my experiences once I've had some.

---

### Post by Bio Leo on 2009-08-26
I picked the printer up and it does print and scan in Ubuntu.  There are (semi?)official print and scan drivers at
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do")
The scanning works when the unit is connected via USB, not networked.  The print driver didn't work out of the box for me, I instead used the stock NX400 one which seems to work fine.  I'm running Jaunty 64 bit, haven't tried it on 32 bit.

---

### Post by Gotit on 2009-08-28
I just picked up an NX515 but I don't see the NX400 print driver in my Ubuntu printer driver list.  Where did you get the NX400 driver?  Could it be because I'm on HH?  Thanks!

---

### Post by Bio Leo on 2009-08-28
> **Gotit said:**
> I just picked up an NX515 but I don't see the NX400 print driver in my Ubuntu printer driver list.  Where did you get the NX400 driver?  Could it be because I'm on HH?  Thanks!
It was in the standard printer list for me (Jaunty).  You could try the actual NX515 driver from the link I posted above, you might have better luck with it than I did.
  I don't know the ins and outs of upgrading the gutenprint drivers but the NX400 should be supported in the current version;
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX400]("http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_NX400")
Good luck!

---

### Post by Gotit on 2009-08-29
**Just an update:**
I elected to use the the drivers from Avasys (link in post #3, thanks Bio Leo!) and I now have printing and scanning abilities.  I have the NX515 attached locally via USB. 

The only words of wisdom I can offer in using the Avasys drivers is to be sure to download the "Epson-Stylus_NX515-pipslite-en.ppd" file along with the "pipslite.deb" installer.  If you follow the README for pipslite.deb, when you get to step 6.3 for creating a ppd file, trying to run ```
pipslite-install
``` will fail.  That's why you need the .ppd file :).  Just copy it to the /usr/share/cups/model/ directory like it says in the "Instructions on use of PPD files". 
 

My next effort in a few weeks or so will be to attempt getting the NX515 networked.  Has anyone else tried that yet?

---

### Post by Gotit on 2009-08-30
**Another update:**

I got network printing working!  I couldn't wait a couple of weeks (ya, I know, it's a sickness :))  Anyway, if anyone's interested, here's what I did:

_IP Address:_
1. If you don't know it, log into your router/WAP and get get your IP address range from your routers admin screens.

_Printer set-up:_
1. Follow the LAN > Advanced set up from the manual on the printer's keypad (I don't broadcast my SSID)
2. Set up the security parameters for you network
3. Go back to LAN > Advanced > Manual and enter a high IP address from your range that shouldn't get assigned in normal use by your router. 
[U]
Wireless Printing set-up on you system:[/U]
1. Go to System > Admin > Printing and select "New Printer"
2. In the Select Connection Devices list select "AppSocket/HP JetDirect"
3. In the Host: block enter the IP address from above and press Forward
4. In the next form select "Provide PPD file" and browse to the location where it's stored (/usr/share/cups/model remember YMMV)
5. In the next form give it a name etc.
And you are done!

---

### Post by regeya on 2009-09-22
> **Gotit said:**
> **Another update:**

I got network printing working!  I couldn't wait a couple of weeks (ya, I know, it's a sickness :))  Anyway, if anyone's interested, here's what I did:

_IP Address:_
1. If you don't know it, log into your router/WAP and get get your IP address range from your routers admin screens.

_Printer set-up:_
1. Follow the LAN > Advanced set up from the manual on the printer's keypad (I don't broadcast my SSID)
2. Set up the security parameters for you network
3. Go back to LAN > Advanced > Manual and enter a high IP address from your range that shouldn't get assigned in normal use by your router. 
[U]
Wireless Printing set-up on you system:[/U]
1. Go to System > Admin > Printing and select "New Printer"
2. In the Select Connection Devices list select "AppSocket/HP JetDirect"
3. In the Host: block enter the IP address from above and press Forward
4. In the next form select "Provide PPD file" and browse to the location where it's stored (/usr/share/cups/model remember YMMV)
5. In the next form give it a name etc.
And you are done!

I'm not currently running Ubuntu as my main machine, but rather Arch (long story), and I also got networked printing working.  I edited printers.conf to replace the printer IP with the broadcast name.  I've got my router set to revoke IPs a little too often. ;-)

But for setting up the printer, your Ubuntu setup should be able to discover the IP on its own (or am I completely mistaken?)

---

