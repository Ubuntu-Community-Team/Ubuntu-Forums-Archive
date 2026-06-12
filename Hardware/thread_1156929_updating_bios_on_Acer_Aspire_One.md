---
title: "updating bios on Acer Aspire One"
date: 2009-05-12
forum: Hardware
---

### Post by symon1980 on 2009-05-12
ok.... this is probly not the best place to ask... but im asking everywhere else too....
basically, i have Opensuse 11.1 installed on my Acer Aspire Netbook... my netbook like many others has a fault where the battery stops charging after a while... fortunately it is not a hardware fault.... the fix is to update the bios with a patch from Acer....

problem is... its an .exe file...
i have read about a work around... and that is to install FreeDos on a usb stick... put the patch on the usb stick, and execute it through freedos.... So far i have managed to boot into freedos, access the bios folder.... but i can't execute the patch. The patch is named InsydeFlash.exe... everytime i try and execute it i get a bad command etc.... i read to execute you just type in the name.. but i tried everything... InsydeFlash.... InsydeFlash.exe ...... run InsydeFlash.exe.......... i've tried renaming it to a .bat file and executing that..... still get a bad command entered error........

anybody know where im going wrong?
kaddy

---

### Post by joshedmonds on 2009-05-12
Follow these instructions:

[http://www.techdc.com/aspire-one-bios-update-version-3304]("http://www.techdc.com/aspire-one-bios-update-version-3304")

I did this today to update to bios 3309.

Ignore the flashing utility included in the bios download, just extract and copy the folder as instructed, and run as instructed.

Download the latest bios zip file from 

[http://support.acer-euro.com/drivers/downloads_gd.html]("http://support.acer-euro.com/drivers/downloads_gd.html")

If you are having problems with unetbootin go to the sourceforge page and download the latest version:

[http://unetbootin.sourceforge.net]("http://unetbootin.sourceforge.net")

---

### Post by symon1980 on 2009-05-12
cheers for the info... but the particular bios update i recieved from acer to fix my battery charge problem does not contain any .bat files.... only .exe and dll files.... so this particular tutorial doesn't really apply to me......
also.... the bios update that i need to fix my battery problem for some reason isn't listed on their website.... that i can see.... they sent it to my email.... its a folder called AS1BIOS and it contains .exe's and .dll's.....

---

### Post by symon1980 on 2009-05-12
hmmmm actually, i must thankyou. I decided to ignore the patch acer sent me, which didn't contain any .bat files, and tried upgrading my bios using the link you gave me to see if it would fix my battery charging problem... AND IT DID! wooohooooo

now im happy!!!!!!!! :)

---

