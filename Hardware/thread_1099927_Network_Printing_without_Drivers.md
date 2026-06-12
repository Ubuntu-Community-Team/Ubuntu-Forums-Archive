---
title: "Network Printing without Drivers"
date: 2009-03-18
forum: Hardware
---

### Post by RealG187 on 2009-03-18
I have a Lexmark printer attached to a Windows PC and it's shared. I cannot use this printer in Ubuntu since there are no Linux drivers for it. However, would there be a way to have the Windows machine share it in a way so that Linux can communicate with it? I am reading about print servers at school and there is a blurb that says "A print server managing print jobs over a TCP/IP network uses the LPR/LPD protocol to receive print jobs from various operating systems (for example, Unix, Windows, and Mac) on the network" so could I have the Windows machine receive a print job from Ubuntu and then send it to the printer, therefore using the drivers on the Windows side since there are Windows drivers.

Even take that a step further, if I have a Windows Virtual Machine with the drivers installed and have a virtual network between the Linux host and it (as I do for sending files between the two) could I share the printer in the VM with the host. This way I would not need to have another computer on the network to print and as long as I have my VM running in the background I could print to this printer like normal.

---

### Post by veloce on 2009-03-25
There is a solution out there.  It uses ghostscript on the windows machine to emulate a postscript printer available to the unix machines.

Unfortunately, it's so long since I used it that I can't remember what it is called.  You could start searching from the ghostscript site...

---

### Post by RealG187 on 2009-03-26
So on Linux I would install Ghost script drivers, then print to the Ghost script virtual printer and thenit would send the job to the Windows machine which would take the ghost script data and then print it to the Lexmark printer usinig the Lexmark driver?

Or I could install the Lexmark printer in a Virtual Machine running Windows and the Ghost script print server and then print to a virtual printer in Ubuntu which would then send the job to the VM via VMWare's virtual network interface and then VM would send the data through the USB cable to the printer.

---

### Post by veloce on 2009-03-26
Aha! Found it! It's called RedMon.

[http://pages.cs.wisc.edu/~ghost/redmon/index.htm]("http://pages.cs.wisc.edu/~ghost/redmon/index.htm")

You set all of it up on the windows machine that can print (including ghostscript).  This creates a virtual postscript printer that can be shared over the network - via samba.

Your linux machines think they are printing to a postscript printer attached to the windows machine.

---

### Post by RealG187 on 2009-03-27
Do you install drivers for the Ghost script printer or something?

---

### Post by veloce on 2009-03-29
> **RealG187 said:**
> Do you install drivers for the Ghost script printer or something?

Yes, in cups you install a generic postscript printer driver such as an Apple LaserWriter,

---

### Post by verlyn13 on 2009-04-07
Is there confirmation that this works?

If it does, a slightly detailed guide to setting it up would be awesome for us linux newbies who have paperweight lexmark all-in-one printers laying around.

---

### Post by RealG187 on 2009-04-07
So do I install this under Windows (The Print Server)?

[ftp://mirror.cs.wisc.edu/pub/mirrors/ghost/ghostgum/redmon17.zip](ftp://mirror.cs.wisc.edu/pub/mirrors/ghost/ghostgum/redmon17.zip)

---

### Post by veloce on 2009-04-07
> **verlyn13 said:**
> Is there confirmation that this works?

If it does, a slightly detailed guide to setting it up would be awesome for us linux newbies who have paperweight lexmark all-in-one printers laying around.

It does work, I had it set up for a Brother MFC.  It was a little slower than direct printing but gave good output. 

However it was a couple of years ago and the machine running it died.

I will consider writing a short howto as I'd like to set it up again at home - hardware willing.

---

### Post by veloce on 2009-04-07
> **RealG187 said:**
> So do I install this under Windows (The Print Server)?

[ftp://mirror.cs.wisc.edu/pub/mirrors/ghost/ghostgum/redmon17.zip](ftp://mirror.cs.wisc.edu/pub/mirrors/ghost/ghostgum/redmon17.zip)

Yes, redmon needs to be setup on the print server.

---

### Post by cenzorrll on 2009-04-07
i have a similar question except it's somewhat the other way around.

i have linux box i want to setup as a file and print server, but there are no drivers in linux for my printer (canon mp470) is there a way to share this printer through the network and let the windows machines deal with the drivers?

---

### Post by RealG187 on 2009-04-08
> **cenzorrll said:**
> i have a similar question except it's somewhat the other way around.

i have linux box i want to setup as a file and print server, but there are no drivers in linux for my printer (canon mp470) is there a way to share this printer through the network and let the windows machines deal with the drivers?

You could get VMWare and run windows on the same computer and have the VM deal with the drivers and share the printer.

---

### Post by cenzorrll on 2009-04-10
> **RealG187 said:**
> You could get VMWare and run windows on the same computer and have the VM deal with the drivers and share the printer.

i'm using a fit-pc slim (500mhz geode processor = slllooooowwww) so virtual machines are pretty much out of the question. i was wondering if, since you have to install the drivers on the windows machine anyway that i could just choose a canon driver to connect it to CUPS and the windows machine drivers would override it. (I won't be printing directly from the server)

Edit: Yeah, this^^ doesn't work

---

### Post by RealG187 on 2009-04-10
Which computer are you plugging in the printer to? If it's the Windows machine there should be a way. If you plug into the Linux machine then you have to run a VM and have VMWare add the printer as a USB device in the virtual machine and then have Windows in the VM share the printer over the virtual network.

---

