---
title: "HP Photosmart C4780 All-in-One"
date: 2009-11-04
forum: Hardware
---

### Post by SPARTAN-118 on 2009-11-04
Hi, while I'm waiting for a replacement part to fix my broken desk, I've been trying to use my dad's new wireless all-in-one from HP.

The printer says it's connected to the wireless network, and I believe it, because my dad's old Pent. 4 computer can connect to it using the wireless router.

However, I go into System -> Admin -> printing and the HP is not there.

The IP Address is 192.168.2.19 for the printer, but when I click "Trouble?" in the Printers window, it can't find what's wrong with it.

Let me explain this a little better.

This is an HP All-in-One wireless model C4780.

It is connected to an old XP machine via wireless network.

Ubuntu can't see it - it's unlisted in the Printing window.

I can't figure out how to do this correctly.

Ya see, I'm pretty sure my Vista would be able to connect, but the doc. I need is on Ubuntu, and it's a horror just starting up Vista on my laptop.

So, can anybody give me troubleshooting suggestions? Tips?

I appreciate any help,
SPARTAN-118

EDIT: I'll try connecting via USB for know. But I need help setting up wireless. I heard something about switching from USB to JetDirect to do that, but I don't even know what that is. pathetic, I know.

---

### Post by MicNanDec on 2009-11-09
Hi! I just purchase this exact printer.  To get it set-up for wireless it seems you need to configure it.  Here's what I did:

I went to [www.hplip.net](www.hplip.net) to get the newest version of HPLIP.
I followed the instructions on how to install HPLIP.  This required opening up a terminal and running the setup through that.  It's important not to have the printer connected to the computer at this point.  Once you've downloaded the newest version it will start the setup.
Select which option you want the printer to be configured too.  I chose the USB/802.11 option so I could connect it to my network.  You will need to connect first with USB and then configure the wireless after that.  This option allows you to enter your SSID and any security encryption key.  This will then take you through a few more screens that sets up the wireless feature.  

I did have a small issue where I installed the printer twice on my computer.  I simply deleted one and enabled the other printer.  I also had to change "Device URI" to recognize the "net" setting instead of the "Usb".  All in all it was a fast and pretty painless install.  All my features are working nicely.
Basically I followed the directions on the [www.hplip.net](www.hplip.net) website and the directions on the screen without having to many issues.  One point to make about the website is that the direction are for an earlier version of the package so make sure you change the 6 in the website's command to the 10 in the current version.

I hope this helps and that you got the document that you needed!  Good Luck!  :)

---

### Post by SPARTAN-118 on 2009-11-09
Thanks I will try this tomorrow. I am only using the wireless printer until I get colour ink for mine. (Which may be a while considering I get no allowance and I don't have a job :D)

-Matt

---

### Post by scr9268 on 2009-11-26
I have the same printer and already had it setup for wireless access from two windows PCs.  I used the recommended link from MicNanDec's posting and it tied my Ubuntu PC into the same printer.  Works like a charm.  Thanks!

bl

---

### Post by SPARTAN-118 on 2009-11-26
Yup I actually forgot about how I was supposed to tell you guys if it worked or not! :D

Well, it did, and it works perfectly. Thanks much for showing me this! HPLIP... wow. What a simple name (and the test sheet is pretty, too!).

---

### Post by jon-hhs on 2010-03-03
HI, Can you help me now, I have the same printer, i have the latest version of HPLIP, but its just a folder on my computer (jaunty) how do i get it running?

---

### Post by jonasbdotcom on 2010-06-29
> **jon-hhs said:**
> HI, Can you help me now, I have the same printer, i have the latest version of HPLIP, but its just a folder on my computer (jaunty) how do i get it running?

If you haven't already gotten the HP to work - then do this...


[LIST=1]
[*]download the hplip from the website
[*]copy the file .run file to a folder on your home area
[*]open terminal go to the location of the file and type "sh hplip-3.10.5.run"
[*]type "A" for automatic and confirm the distro you're using
[*]when it's done you either need to plug in the printer via USB and restart or if WIFI simply restart. (depends if you have already set up the printer on the network)
[*]Restart and go to System -> Adminsitration -> Printers and set it up...
[/LIST]
Easy as that! Takes perhabs 5 minutes or so.

Good luck

---

### Post by sgtslwilson on 2010-09-10
I run UNR 10.04.1

Mine ran perfectly out of the box. I didn't have to download anything. Am I missing something?

---

### Post by h4141 on 2010-11-19
> **SPARTAN-118 said:**
> Hi, while I'm waiting for a replacement part to fix my broken desk, I've been trying to use my dad's new wireless all-in-one from HP.

The printer says it's connected to the wireless network, and I believe it, because my dad's old Pent. 4 computer can connect to it using the wireless router.

However, I go into System -> Admin -> printing and the HP is not there.

The IP Address is 192.168.2.19 for the printer, but when I click "Trouble?" in the Printers window, it can't find what's wrong with it.

Let me explain this a little better.

This is an HP All-in-One wireless model C4780.

It is connected to an old XP machine via wireless network.

Ubuntu can't see it - it's unlisted in the Printing window.

I can't figure out how to do this correctly.

Ya see, I'm pretty sure my Vista would be able to connect, but the doc. I need is on Ubuntu, and it's a horror just starting up Vista on my laptop.

So, can anybody give me troubleshooting suggestions? Tips?

I appreciate any help,
SPARTAN-118

EDIT: I'll try connecting via USB for know. But I need help setting up wireless. I heard something about switching from USB to JetDirect to do that, but I don't even know what that is. pathetic, I know.

this hp photosmart C4780 printer [driver]("http://driverswin.com/hp-photosmart-c4780-printer-driver/") page
good luck

---

### Post by TheMadGeneral on 2011-12-16
[QUOTE=ArabAttack;9526644]If you haven't already gotten the HP to work - then do this...


[LIST=1]

[*]open terminal go to the location of the file and type "sh hplip-3.10.5.run"

At step 3 you will have to change the command to reflect the latest version of the hlip.  At time of writing this message it is 3.11.12.  This means that you would enter "sh hplip-3.11.12.run"

HP have a great article on how to install the hplip.  It can be found [here]("http://hplipopensource.com/hplip-web/install/install/index.html")

Hope it works for you.

---

