---
title: "HP PSC-1400  Drivers for Windows client"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by gpalmercableone on 2007-11-12
Hi all, I have been diligently trying to convert the majority of my machines to  Linux Ubuntu, love the features. Like many I am trying to get away from anything MS. Been searching various forums for a few days and can't seem to find and answer to this. 

     I currently have an Ubuntu print server setup and working using Samba, using an HP 1401 all-in-one. Print shares work, can print from other Linux machines no problem. I have one XP machine that is still required and I am attempting to configure it to print to the Ubuntu print server. When using the winxp Printer setup wizard, all goes fine, sees the printer on the server, it then tells me that the drivers provided by the server won't work and wants to install xp drivers.  I get the "select from a list", or "have disk". XP does not have a  driver base for this printer so I attempt to install drivers from the HP install disk, or downloaded drivers. It asks for the .inf file as normal, but all .inf files tried refer to operations that result in looking for various driver files that cannot be found on the CD.

     Tried HP live support extensively, finally got frustrated with the canned answers referring to an install for a directly connected printer. Sorry for such a noob question for a first post. The past few months I have found answers to just about all my issues on various forums, but this one is driving me nuts. Think maybe I am missing something obvious, any help or point in the right direction would be appreciated.

Thanks in advance.

---

### Post by MrFSL on 2007-11-12
Well this is what I would do. (If you already have then my apologies)

First I would download the driver from HP website. I see that there is a "HP Basic" Driver - this is probably the one i would download.

I would then install the driver on the XP machine.

Next I would go through the Windows network printer setup. It the drivers have been pre-installed on the XP box then it should not prompt for them.

---

### Post by gpalmercableone on 2007-11-12
Appreciate the response. Yes I tried that, the printer had been installed directly to the machine before. When it was moved way back when, the printer was only deleted, nothing was uninstalled. While trouble shooting I went as far as re-connecting the printer back to the xp machine, and watched it automatically re-install no problem, no additional driver installation. Thats why I figured they must be someplace, but file and manual searches have turned up nothing for me. 

I am not a files guru, but looking at the files contained on the CD, I see .DAT files labeled like driver files. The way the installation works it appears to be structured so the HP install utility has to install the drivers.  I have searched the Win32 Driver directories, and the "Temp" where the CD puts the extracted files from the installation, but no luck.

I figured someone out in the world has already come across this. As I said, I initially treated it like a proprietary HP issue, but HP was no help at all.

---

### Post by gpalmercableone on 2007-11-25
Silly me. Read the fine print from HP. No Network Support for this model. Will work sharing from Window machine to Windows machine, but thats about it. Been searching forums, but cannot seem to find a work-around.

---

