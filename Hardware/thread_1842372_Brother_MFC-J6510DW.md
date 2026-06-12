---
title: "Brother MFC-J6510DW"
date: 2011-09-11
forum: Hardware
---

### Post by faramog on 2011-09-11
Does anyone know how to install this printer ... the instructions on the Bother website don't work (or make sense) ?

---

### Post by Shazaam on 2011-09-11
Which version of Ubuntu are you running?
If you search Synaptic for Brother you should find the cupswrapper and lpr drivers there. Make sure you install the Brother -extra drivers too then go to System-Administration-Printing and add the printer.

---

### Post by faramog on 2011-09-11
Tried following the instructions on Brother  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

Don't seem to work.

Version is 11.04

---

### Post by gleedadswell on 2012-06-02
I had a bit of trouble getting this one to work but I just got it.  At the moment I'm only using it with a direct usb connection because I wanted to first check that I had working drivers before attempting to tackle a wireless network setup.  I'll try setting it up for wireless next and post again once I do.  Then I'll try to get it scanning, which I've found to be a pain in the butt with other Brother multifunction printers.

Here's what I did.  I more or less followed the instructions at the Brother site at:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

1. I downloaded the drivers from 

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj6510dwlpr-1.1.1-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj6510dwlpr-1.1.1-1.i386.deb&lang=English_lpr)
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj6510dwcupswrapper-1.1.1-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj6510dwcupswrapper-1.1.1-1.i386.deb&lang=English_gpl)

2. I opened a terminal and did sudo -i

3. It said I had to do a few things for Ubuntu versions 8.04 through 9.04.  I'm running 11.10 but I did them anyway on the theory that they probably just haven't edited the webpage in a while.  So I tried to do

aa-complain

This failed saying I needed to install the apparmor-utils package.  So I installed it and then ran the command.

It said I had to create the /usr/share/cups/model directory.  It was already there but that's probably because I've installed a couple of other Brother printers on this machine before.

4. I installed the drivers using dpkg -i as outlined on the Brother site.  Installation of the lpr driver failed saying it couldn't create

/var/spool/lpd/mfcj6510dw

So I created the directory manually and tried dpkg again.  It was successful this time.  Then I did dpkg -i for the cupswrapper driver and that ran with no trouble.  dpkg -l | grep Brother showed both drivers.

5. I brought up the cups url in my browser

[http://localhost:631/printers](http://localhost:631/printers)

It showed the printer as an available queue.  But clicking into it to show more info I noticed that the url was wrong.  It was supposed to be

usb://Brother/(your printer's model name)

But it showed up as usb:/dev/usb/lp0

Printing a test page failed.  I now messed around for a while trying various things that didn't work.  Eventually I deleted the printer from cups and on the printer I did a network reset.  This rebooted the printer.  It showed up as a new printer in cups.  At first all of the options were unset but after a moment they filled in.  It now had the correct url but the listed driver was "Generic text-only printer".  A test page failed.  I modified the printer in cups to select the correct driver

Brother MFC-J6510DW CUPS

Now the test page printed successfully.  Hooray!  I also printed from another couple of applications and verified that things seem to be working well.

Hope that helps.

---

### Post by kurt18947 on 2012-06-02
It sounds like you have the printing in hand.  Once you have USB printing working, wireless printing should be pretty simple.  I assign the printer a static I.P. address then change the device URI for the printer from 'usb:/something' to 'socket:xxx.xxx.xxx.xxx:9100' where x=static i.p. address.  For future reference though Brother has an installer which seems to work pretty well and can configure several different network connections:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

And you're correct, getting a scanner to work is more of a pain than printers.

There seem to be at least two issues installing a scanner, perhaps a 3rd in 12.04.

Here is a recent post of mine, #2

[http://ubuntuforums.org/showthread.php?t=1988296&highlight=brother](http://ubuntuforums.org/showthread.php?t=1988296&highlight=brother)

I hope you find this of some use.

---

### Post by gleedadswell on 2012-06-03
OK, I've got scanning working...mostly.

I just followed the instructions at the Brother site

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html")

I didn't have any of the issues that kurt18947 mentions in his post because I'm running 32-bit (so I didn't have to copy all those files from /usr/lib64 to /usr/lib) and also, I've installed a Brother scanner on this computer before so the edit to /lib/udev/rules.d/40-libsane.rules was already done.

So now I can scan, but for some reason only in xsane.  When I try Simple Scan the scanner says "scanning" and makes all sorts of promising noises.  Then the whole process hangs.  Eventually Simple Scan reports "Failed to scan.  Error communicating with scanner".  The scanner remains hung with "scanning" on its display.  It is hung so badly it won't even turn off properly so I have to unplug it.

So this looks like an issue with Simple Scan.  That's OK for me.  Unlike a lot of people I actually like xsane's user interface.

OK, time to try to get wireless working.

---

### Post by gleedadswell on 2012-06-03
Getting printing working over wireless was very easy.  I just followed the printer manual to make the printer connect with my wireless router (via WPS).  Then in the cups admin page on my browser I did "Add printer".  It showed up in the list of detected network printers so I just selected it and everything else just worked.

Still working on getting scanning on the network.

---

### Post by gleedadswell on 2012-06-03
And now scanning works (but still only in xsane, not Simple Scan).  The only difficulty was that for some reason I thought I needed to use brsaneconfig3 but it told me "invalid model".  I finally figured out that this one wants brsaneconfig4.  So the command is

```
brsaneconfig4 -a name=SCANNER model=MFC-J6510DW ip=***.***.*.***
```

I found the ip by going to the admin page for my router and examining the DHCP client table.  There's also a utility available from Brother called BRAdminLight.  It is a little java program and among the things it does is list Brother devices on the network and their ip addresses.

Any idea how to assign a static ip address to this thing?  I figured it would be in the router admin page (I'm using a Cisco WRT54G2), but looking around I haven't seen anything that lets me do it.

---

### Post by kurt18947 on 2012-06-03
> **gleedadswell said:**
> 
 
<snip>
Any idea how to assign a static ip address to this thing?  I figured it would be in the router admin page (I'm using a Cisco WRT54G2), but looking around I haven't seen anything that lets me do it.

Assuming the MFC-J6510DW is similar to the MFC-J430W, you assign a static i.p. address at the printer.  This should be pretty close:


[LIST=1]
[*]press the 'menu' key
[*]arrow down to 'network' press 'ok'
[*]arrow down to 'TCP/IP'  press 'ok'
[*]arrow down to 'IP address'  press 'ok'
[*]enter your desired I.P. address  press 'ok'
[*]done.
[/LIST]

---

### Post by gleedadswell on 2012-06-03
Ah, this router doesn't support DHCP reservation.  Apparently according to 

[http://homecommunity.cisco.com/t5/Wireless-Routers/How-to-assign-static-ip-via-mac-address-on-LINKSYS-WRT54G2/td-p/242331]("http://homecommunity.cisco.com/t5/Wireless-Routers/How-to-assign-static-ip-via-mac-address-on-LINKSYS-WRT54G2/td-p/242331")

I can use a fixed LAN IP address by entering it into the printer.  A little more reading showed me that I could do this using BRAdmin.  So I did this.  Then I removed the printer from CUPS and re-added it which worked with no trouble.

When I tried to re-add it to brsaneconfig4 using the new ip it told me 

"SCANNER" is already registered.

I tried

```
brsaneconfig4 -r name=SCANNER
```

but then 

```
brsaneconfig4 -q
```

still showed it in the list and adding it with the new ip still failed.  Eventually I just added it with a new name (SCANNER2 very imaginatively).  This is slightly annoying because now when I load xsane it first asks me whether I want to use SCANNER (which is now nonfunctional) or SCANNER2.  But at least it works.

Any idea why brsaneconfig4 -r doesn't seem to work?

---

