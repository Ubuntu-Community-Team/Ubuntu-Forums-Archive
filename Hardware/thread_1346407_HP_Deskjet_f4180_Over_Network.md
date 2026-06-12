---
title: "HP Deskjet f4180 Over Network?"
date: 2009-12-05
forum: Hardware
---

### Post by MisterEx on 2009-12-05
**Please note: I have a ton of experience with computers [Windows], but very limited experience in Ubuntu. Keep the newbie-kid gloves on until I am more comfortable with UNIX/bash :P.**

I am having difficulties accessing my HP Deskjet f4180 printer over the network. It is attached to a Windows2000 [don't laugh] computer on my network.

I have preformed the following steps:

**1 **Used smb to access the printer over the network.

RESULTS: Was able to discover and authenticate with the printer -- great! Unfortunately, there is only a driver for HP f4100, which after installing, I was unable to print a test page or any regular page with this driver. The driver does identify itself as "HP Deskjet f4100 **series**", so hopefully i am the only one with the problem and that driver does work on an f4100, that would be a real shame.

**2 **Installed HPLIP from [this ]("http://hplipopensource.com/hplip-web/index.html") url.

RESULTS: Installation went relatively smoothly. Opened up to setup device... cannot find any printer. Went into advanced and tried to speficy network path via smb directly, still no dice. Maybe HP doesn't support smb, maybe Ubuntu can see something HP's software cannot.

Ubuntu **clearly** sees the printer, but the f4100 driver is not working with my f4180 printer.

HPLIP does not see the printer, but does support f4180 [I could definitely get it to work if I plugged it in via USB].

It is impossible given the current setup to move the printer to a non-windows machine, and it can currently ONLY be seen over smb.


Help!

---

### Post by Fidelio on 2009-12-06
Hi,
Not sure I can be much help, but I can tell you the f4100 is the correct driver and it works fine for me.
I've also just set my laptop up to print over the network via samba, although both the laptop and the desktop to which the printer is connected are running ubuntu.
(What worked for me was System>Admin>Printing>New Printer>Network Printer>Windows Printer Via Samba then Browse WORKGROUP to find the Desktop PC and the printer appeared under it.But I think that's just what you've tried)

---

### Post by MisterEx on 2009-12-06
> **Fidelio said:**
> Hi,
Not sure I can be much help, but I can tell you the f4100 is the correct driver and it works fine for me.
I've also just set my laptop up to print over the network via samba, although both the laptop and the desktop to which the printer is connected are running ubuntu.
(What worked for me was System>Admin>Printing>New Printer>Network Printer>Windows Printer Via Samba then Browse WORKGROUP to find the Desktop PC and the printer appeared under it.But I think that's just what you've tried)

Just to be clear - you are using an HP Deskjet 4180 with an HP Deskjet 4100 driver? 

When I attempt to print something, the printer "headers" spin, but it does not begin printing. I can print from this computer on the XP installation.

---

### Post by Fidelio on 2009-12-07
Yes. I bought the printer, about a year ago, and just plugged it in to my desktop, showing up as as series f4100. About 15 seconds later it worked perfectly. A couple of weeks ago my wife bought a laptop and (after removing Vista and installing 9.10) I set it up on the wireless network. I wasn't sure what driver to choose, but I went for the f4100 and it worked. I don't know enough about networking to choose anything else, but Ubuntu just defaulted to Samba, even though I don't have any windows machines on the network, and it just came up peachy.
Again, I'd stress that I'm working 2 ubuntu machines, but the f4100 driver works flawlessly for me on both machines.
Have you tried just plugging the printer into the linux machine to see if that works?
I'm really not very techy at this stuff, so I'm sorry I can't be more help, but I can confirm, that on my set up, the f4100 driver works with the f4180 on both the desktop via USB and the laptop via wireless.
Good luck.

---

