---
title: "BIOS Update DV6-3143 - can't update from DOS environment..."
date: 2012-07-17
forum: Hardware
---

### Post by jkn83 on 2012-07-17
I meant title to be: **BIOS Update DV6-3143 - can't update from FreeDOS environment...**Sorry for the confusion...

Hi everybody.  I am trying to flash a new BIOS update from F23 to F29 for my HP dv6-3143 laptop. I am having trouble executing the InsydeFlash.exe to load the F29 bin file.  Apparently it will not run in a FreeDOS environment.  I am a complete newb to ubuntu/linux coming from programming in windows the past years...Any ideas how to get this BIOS updated without installing windows or bricking my laptop? thanks in advance

I have followed instructions to extract my the driver I downloaded from the HP website 
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?cc=us&lc=en&dlc=en&product=4332734](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?cc=us&lc=en&dlc=en&product=4332734)

I downloaded the Win 64 bit...

The EXE could not be run from FreeDOS so I extracted the file using 7z

I got the following files...
01448F29.BIN  <==this is my BIOS, have no idea how to get it to run in FreeDOS
platform.ini 
xerces-c_2_7.dll
iscflashx64.sys
icsflash.sys
iscflash.dss
insydeflash.exe <===updates the BIN file but cannot be run in a FreeDOS environment
fwupdLcl.exe 
Flshookdll.dll
ding.wav
AtpTimerinfo.dll

I have tried the websites below
[http://jennyandlih.com/flashing-bios-exe-ubuntu](http://jennyandlih.com/flashing-bios-exe-ubuntu)
[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

i am looking at 
[http://hwoarang.silverarrow.org/2011/04/18/update-hp-insyde-bios/](http://hwoarang.silverarrow.org/2011/04/18/update-hp-insyde-bios/)
scratching my head

I have checked FLASHROM - and i dont think my laptop/motherboard is compatable so i am not going to try the lazy man's route
[http://op111.net/83/](http://op111.net/83/)

i have tried creating a bootableCD for the sp55299.exe (hp driver file name) and running the sp file within FreeDOS it will not execute
I have tried creating a bootable CD for all the files extracted from the sp55299.exe (hp driver file name) and running all exes. each exe when executed came back with nothing.  i tried insydeflash 01448F29.BIN   and nothing happened....

After more research i figured out insydeflash.exe updates the bios using the BIN file but will not do it in FreeDOS 

Is there anyway i can create a bootable CD in linux so i can update my bios??? i removed my windows partition when i did the install on the laptop =(
i would have to order a recovery cd to re-install windows to install the BIOS update...

---

### Post by ahallubuntu on 2012-07-17
You don't have to order a recovery CD from HP just to update your BIOS.  Instead, do a quick install of Windows 7 using a disc you can make from here:

[http://forum.notebookreview.com/windows-os-software/428068-legal-windows-7-download-links-just-like-vista-before.html](http://forum.notebookreview.com/windows-os-software/428068-legal-windows-7-download-links-just-like-vista-before.html)

You don't need a product key to install it and use it for 30 days.  That's plenty of time just to install your BIOS update.

But the other question is: why are you updating your BIOS?  What specific problem are you trying to fix?  If you can't answer that question, don't update your BIOS.

---

### Post by jkn83 on 2012-07-17
that link is dead...

do you have another link that is working or should i just look for a windows trial download?

i have a 				**AMD/Intel Hybrid Graphic card and i need my bios updated so i can choose dynamic...this way i can install the video driver correctly**
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

thanks!

---

### Post by jkn83 on 2012-07-17
i found 
[http://techpp.com/2009/11/11/download-windows-7-iso-official-direct-download-links/](http://techpp.com/2009/11/11/download-windows-7-iso-official-direct-download-links/)

the files are humongous like 3GB

---

### Post by ahallubuntu on 2012-07-17
Sorry - I think that link just died.  (Google's cache of it is still up for the moment if you google for the link itself; mostly the link is a short set of instructions and links to the downloads on DigitalRiver.) But yes, try the links from Softpedia.  Looks like the same thing.  Yes, Windows 7 DVDs are huge images.

There may be other ways to do the BIOS update with a boot floppy that are simpler and faster, once you figure them out.  But the Windows 7 install method will work for sure, even if it takes longer.

---

### Post by jkn83 on 2012-07-17
yea i think i am going to download the windows iso file 

use [http://www.isotousb.com/](http://www.isotousb.com/)
to create bootable usb and install windows
update bios 
then reinstall ubuntu
and install my video drivers
and finally be done with this ridiculous low graphics mode error i have been facing after installing the updated 12-6-x86 video drivers...

still got to resolve why i cant connect to some wireless networks using a broadcom STA 4313 

i can connect to my parents unsecured network, but not this coffee shops unsecured network

i can connect to this other coffee's shop's network that is in WEP - i found a fix but didnt save the link then did a reinstall of linux now i am all searching the same problem again 

i tried the fwcutter but it didnt resolve the issue...i think i can connect to WEP and not WPA any idea on that? lol - figure its a long shot

---

### Post by Niccola on 2012-07-17
My deal:

Install Windows again and update your BIOS through Windows.

Don't make things hard for you, you save time, save money and save your computer

---

### Post by ahallubuntu on 2012-07-17
I really feel for everyone who has to deal with a crappy Broadcom wireless card.  This forum is full of Broadcom wireless issues.  I always swap out those cards with Intel wireless cards whenever it's possible in a laptop, because they are so cheap on eBay, and Intel wireless cards seem to work much better in general in Linux.  Unfortunately, HP and Lenovo laptops lock down the list of compatible wireless cards in the BIOS with a "white list" - so if you plug in a wireless card that isn't on their list, you can't even boot up the machine!  I don't have this problem with Dell, Acer, Toshiba, etc.  One reason I won't be buying HP or Lenovo laptops any time soon.

---

