---
title: "Old Server PC.  Help with hardware."
date: 2012-03-09
forum: Hardware
---

### Post by jrisreal on 2012-03-09
My dad runs a small business and gave me his old server computer for use as a desktop.  So far, it is functioning great, but, since it is a custom-built server rather than a typical desktop, Windows 7 is failing to install the proper drivers for its hardware.  Any tests I've tried (think DXDIAG etc.) to figure out what soundcard and graphics card is inside it just turns up what Windows has installed for them.  The graphics card comes up as a generic graphics driver and the computer is unable to determine the appropriate resolutions and I cannot manage to get it to display at the right screen size.  The sound interface shows as non-existant and, since I am a music producer and am intending to use this server for production, this could be a problem.  Is my only option to disassemble the server and find out the hardware components that way?  Should I scrap Windows 7 and install Windows Server 2008 R2?  Or can I do it some other way?  I'd rather not open it up just yet, so please give me any advice.

Thanks,
~Syntax Music

PS:
I'm only using Windows on this because FL Studio is more difficult to run on linux.  Otherwise, I would be ubuntu all the way.

---

### Post by jerrrys on 2012-03-09
Servers usually come with crappy on board video and no sound.

In ubuntu open a terminal and enter:

sudo lshw

This will list all hardware.

---

### Post by jrisreal on 2012-03-10
Dang, that sucks.  I'll give it a try.  Atleast, for the sound issue, I  have some sound interface I can plant into it...I also have a Focusrite  Saffire 6 Interface for professional audio use.  The video issue really  is a bummer.  Any way I can get the system to output the right  resolution?  1400x1500 I believe...somewhere around that number.

---

### Post by jerrrys on 2012-03-11
> **jrisreal said:**
> Dang, that sucks.  I'll give it a try.  Atleast, for the sound issue, I  have some sound interface I can plant into it...I also have a Focusrite  Saffire 6 Interface for professional audio use.  The video issue really  is a bummer.  Any way I can get the system to output the right  resolution?  1400x1500 I believe...somewhere around that number.

You probably got pci-x slots which will accept regular pci cards.  If your running a HP server you probably got one pci-e slot.  I run an IBM server and no pci-e slots on mine, but I have added video and audio.  I find eBay a a good source for server parts.  good luck

---

### Post by gordintoronto on 2012-03-11
If you enter the command:
lspci
it should produce about 14 lines of output. One of them will contain the word "VGA," and that line describes the video adapter in the computer. At minimum, it gives you some words to put into Google.

---

