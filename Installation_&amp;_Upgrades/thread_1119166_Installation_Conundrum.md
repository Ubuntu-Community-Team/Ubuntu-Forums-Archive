---
title: "Installation Conundrum"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by coldphyre on 2009-04-07
Hey folks,

I don't post much because I can usually find what I need either on the forums or on Google. 

Here's a whopper for you though:

I have a gateway solo 2000 notebook that came pre-installed with Windows 98 (I think).

The machine has none of the following:
CD Drive
USB Drive
Network Card


Now, to business.

I need to install linux on it (via Floppy would work), It needs to have a PDF reader as well. It is being used simply as basically a dumb terminal to read flight-charts on while a friend is doing flight-school online. 


Any thoughts on how to do this w/o an internet connection/network access?

Funds to purchase new hardware to finagle some sort of solution are **very** limited.


Thanks!

---

### Post by ronparent on 2009-04-07
Is a 4 Gb usb memory stick out of reach? Could you could borrow the use of a friends computer or usb cd drive to install to the stick?

---

### Post by coldphyre on 2009-04-07
Again, no USB ports (I said drive in the previous post.. been a long day, lol).


To reiterate:

NO CDROM
NO USB
NO NETWORK CONNECTION

I've got a few 4GB flash drives laying around, but it doesn't help in this scenario.

I've looked into a couple distros that are made to fit on several floppy diskettes, but that doesn't include  GUI or the ability to install a pdf reader like foxit or something. I'm almost at a loss on this. I think it MAY have a PCMCIA 1.0 slot on it..which could theoretically give me access to USB, but those are runnin like $20-$30 that I really don't want to spend.

---

### Post by larytet on 2009-04-07
Any OS is installed already there ? Windows 98 or Windows XP - can be important.

Less than 256MB RAM can be important - graphical desktop needs RAM. You probably want to load a small Linux distro (xubuntu ?).

If you have another PC you could cross connect serial ports of the machines and copy ISO image to the target PC hard disk. After that  mount the ISO and install.

Another way is RAR (arj also does the trick and may be 7zip) - create 1.4M archives from the ISO image, copy the files (about 30 files) one after another to the floppy disk and to the target machine. Run unrar to uncompress the ISO image on the target machine. 

After that mount of the ISO and WUBI should do the trick

---

### Post by coldphyre on 2009-04-08
No, there's no OS on this box, like I said.. it's like a typical run of the mill windows 98 laptop. It might only have 128ram. it doesn't need anythign extavagent for the GUI, just has to be able to show PDF files.

---

### Post by coldphyre on 2009-04-09
So, here's the specs on this box:

120Mhz Pentium
46MB RAM
I'm guessing like a 4GB HDD
NO CDROM
NO USB

Installation can only happen from floppy

Any distros fit the bill?

---

### Post by Iusedtowearatie on 2009-05-13
Wow, that's an old machine...
You need to be looking at distros such as DSL ([http://distrowatch.com/damnsmall](http://distrowatch.com/damnsmall)) or Puppy ([http://distrowatch.com/puppy](http://distrowatch.com/puppy)).
Regarding how to get the distro on to the box, well... I'd try putting the HDD in another computer *with* CD drive and install from CD as normal. Then various things may happen when you put the HDD back into the original box, but you might be able to work out the side effects.

---

