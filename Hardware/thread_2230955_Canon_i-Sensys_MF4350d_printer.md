---
title: "Canon i-Sensys MF4350d printer"
date: 2014-06-22
forum: Hardware
---

### Post by Jean_David_Wurtz on 2014-06-22
Hi guys,

I've been trying to install my usb printer to my laptop for hours and hours but nothing seems to work. Your help would be greatly appreciated.

Printer : Canon i-Sensys MF4350d
Laptop : Toshiba Satellite Z930-17G
Ubuntu 13.10 64 bits

What I have done so far :

I couldn't install it via the normal procedure "printers -> add -> ..."
I went on the Canon website and downloaded the drivers for Linux and I got a .exe (??). I have no idea what to do with a .exe on linux.
Then I checked the older version for the pilot and it seems better. I got a Zip, but I am not sure what to do with it. When I go in the folder 64-bits, I find etc and usr folder in it. I don't know what to do with that, and the readme or manual is not helping. When instead I go in the folder "source", I find a whole bunch of files and folder, but at least there is a readme with instructions.
So I follow the instructions, open the terminal and ran some command with "make gen". Each time I have error because a soft is missing.

So basically for each error I installed the thing that was missing. I installed libcup2-dev, libgtk2.0-dev, libtool, glib, and maybe others that I forget.

Now I have 
undefined reference to `cupsGetDests'
undefined reference to `cupsFreeDests'
undefined reference to `cupsGetPPD'

And I don't manage to overcome this. I re install CUPS but no effects.

Why why why Linux?

I am really stuck with this printer, I have no clues.
Thank you for any help.

Best,
Jd

---

### Post by ajgreeny on 2014-06-22
Sometimes it is easier to install printers using the [CUPS Printing Webmin]("http://localhost:631/") page in your web-browser.

Go to the Administration tab ->Add Printer and follow the prompts and you may find that the system will search for and install what you need.

I don't know that printer but the webmin system has worked for me with other Canon printers in the past.

---

### Post by Jean_David_Wurtz on 2014-06-22
The printer model is not available, like when I tried to install it automatically from "printer -> add -> ...". Do you know how I can find the "closest" model available?

---

### Post by Jean_David_Wurtz on 2014-06-22
Update : I tried to convert the RPM file into a deb via alien. Error came ("Database environment version mismatch") , but I obtained a deb. After running this deb, I can see my printer in the printer application. But when I try to print, the "Document print statut" says : "Stopped : printer configuration error".

I guess the errors from alien must be solved before...

---

### Post by pdc on 2014-06-22
Hi Jean-David;

let's check if you have anything installed so far: can you copy and paste this into a terminal > [COLOR="#FF0000"]dpkg -l | grep cndrvcups[/COLOR]

please paste back what you get: 
______________________

as you have 64bit, you need some preliminary packages installed: they take a little while to install; a 32bit does not need these:
_______________________

so if you copy and paste these commands into a terminal

> [COLOR="#FF0000"]sudo apt-get install ia32-libs libjpeg62:i386 libxml2:i386[/COLOR]

_______________________________

assuming you didn't get anything in the top enquiry, if you have completed the above, the driver install is next:

______________________________

Canon supply the UFR driver for your device; I use the Canon Asia website for drivers: [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal) (Canon originally hail from Asia ................)

it takes me here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html) and it comes down as [COLOR="#008000"]Linux_UFRII_PrinterDriver_V280_uk_EN.tar.gz[/COLOR]

Can I suggest: 

you click to **Download** this file and select **SAVE** as it is being downloaded; (that way, it is saved to your Downloads directory, if english is the language of your system: in french, cd Téléchargements ....)

you copy and paste the commands (in red) I detail below to install the driver: you will need to open a terminal: use your Dash search function to open a terminal; and use your mouse and top line of the terminal to paste:

> [COLOR="#FF0000"]cd Downloads[/COLOR]          .............(*hit the **enter** key after each paste* ...........)

> [COLOR="#FF0000"]tar -zxvf Linux_UFRII_PrinterDriver_V280_uk_EN.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd Linux_UFRII_PrinterDriver_V280_uk_EN/64-bit_Driver/Debian[/COLOR]        .........if you type the command > [COLOR="#FF0000"]ls[/COLOR], it lists what is in that Debian directory and it should be [COLOR="#008000"]cndrvcups-common_2.80-1_amd64.deb[/COLOR] and [COLOR="#008000"]cndrvcups-ufr2-uk_2.80-1_amd64.deb[/COLOR]

now to install the two components

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-common_2.80-1_amd64.deb[/COLOR] and then > [COLOR="#FF0000"]sudo dpkg -i cndrvcups-ufr2-uk_2.80-1_amd64.deb[/COLOR]

________________________

that installs the 2 components of the UFR driver;

more commands:

> [COLOR="#FF0000"]sudo service cups restar[/COLOR]t

then to register: but first

what do you get: if you printer is plugged in; turned on ...........if you paste the command below 

> [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR]

______________________

I will be assuming it is the only printer connected by usb to your computer so the command to register is likely to be > sudo /usr/sbin/lpadmin -p MF4350d -m CNCUPSMF4350ZK.ppd -v usb:/dev/usb/lp0 -E

If I am correct, you can go ahead and paste the above command into a terminal and see how things stand

that should.................create an entry you can see in LibreOffice and you attempt to print

____________________

If you Subscribe to a a thread, you can follow it more easily.........subscribe area is below

---

### Post by Jean_David_Wurtz on 2014-06-23
Hi pdc,


> [COLOR=#FF0000]*dpkg -l | grep cndrvcups*[/COLOR]
> ii  cndrvcups-common                          2.80-2                                     amd64        Canon Printer Driver Common Module for Linux v2.80
ii  cndrvcups-ufr2-us                         2.80-2                                     amd64        Canon UFR II Printer Driver for Linux v2.80


Then I tried to install the package you said but 

> Package ia32-libs is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0


E: Package 'ia32-libs' has no installation candidate




Should I go for the proposed replacement packages?

---

### Post by pdc on 2014-06-23
thanks; so you have gone to the US Canon site; and it looks like the two files installed; even though you seemed worried they had not............. your alien conversion of rpm packages must have worked???

the US Canon folks name their files differently; so their ppds have a different names

> Should I go for the proposed replacement packages?         ...I would advise yes; reason I say that is 32bit install fine; but Canon have a big readme.txt and it reports various issues with differing distros; and 64bit systems. 

_______________

what does > [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR] give you please; with printer powered up and connected; ..........via usb........is that right?

the register command is now looking like > sudo /usr/sbin/lpadmin -p MF4350d -m CNCUPSMF4350ZS.ppd -v usb:/dev/usb/lp0 -E 

If you have only one printer; the MF4350d and it is connected via usb, the above should work

---

### Post by Jean_David_Wurtz on 2014-06-23
Hi pcd,

Thanks so much for helping.

So I installed the proposed package lib32z1, lib32ncurses5, lib32bz2-1.0. Then I installed the two other one that you asked (libjpeg62:i386 and libxml2:i386).

> [COLOR=#000000] your alien conversion of rpm packages must have worked??[/COLOR]
If you say so, but on the other hand I tried so many things before...

The command [COLOR=#FF0000]*/usr/sbin/lpinfo -v  *[/COLOR], with printer on and connected by USB gives
> 
network http
network lpd
network ipps
network ipp
network socket
network smb
network https
network beh
network ipp14
direct usb://Canon/MF4320-4350%20(UFRII%20LT)?serial=SJ3002070815G&interface=1
direct usb://Canon/MF4320-4350%20(FAX)?serial=SJ3002070815G&interface=2


> [COLOR=#000000]the register command is now looking like[/COLOR][QUOTE][COLOR=#000000]*sudo /usr/sbin/lpadmin -p MF4350d -m CNCUPSMF4350ZS.ppd -v usb:/dev/usb/lp0 -E*[/COLOR][/QUOTE]

Sorry I don't get it, should I put this command in terminal? Anyway I did it, and I didn't get any message back, so I guess it worked.

> [COLOR=#000000]If you have only one printer; the MF4350d and it is connected via usb, the above should work[/COLOR]
At work I have access to a printer on the network. I don't know the details, all I know is that I can print whenever I am connected to the university wi-fi or to the university ethernet.

My printer still is not working

After all the stuff I did before, I might have put too much stuff. When I go in "printers", I see one Canon-MF44320-4350-(UFRII-LT), one MF4350d, and the last one is the one from my work I think (HP-LaserJet-9040-9050-MFP). All have an exclamation point above the icon.
**Maybe I should clean the mess before trying a fresh install?** I am willing to remove all printers, even the one at work, because it is not that important for my laptop.

Thanks again

---

### Post by pdc on 2014-06-24
thanks Jean-David; we are not quite there yet ...

> Maybe I should clean the mess before trying a fresh install? ........... a fresh install of what ...... I didn't know what you meant ...........

when you get the result > direct usb://Canon/MF4320-4350%20(UFRII%20LT)?serial=SJ3002070815G&interface =1 Canon point out that can be used also to register the printer;

______________

so you have tried printing with all the MF4350 options that are now shown? One way to delete them is the CUP interface [http://localhost:631/printers/](http://localhost:631/printers/)

this should show all that are registered on your system; if you left-click on the left-most entry for enter printer, you then get to select the options and one is delete printer: that means delete the entry on CUPS: the drivers themselves are still there; so you could delete the entries there 

-____________

to register a new entry, if you use > [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p MF4350d -m CNCUPSMF4350ZS.ppd -v usb://Canon/MF4320-4350%20(UFRII%20LT) -E[/COLOR]

_________________

that should create an entry in CUPS; and you can see if it will print; you added the list from earlier: 

lib32z1 
lib32ncurses5 
lib32bz2-1.0 
libjpeg62:i386 
libxml2:i386

---

### Post by Jean_David_Wurtz on 2014-06-24
> [COLOR=#000000]........... a fresh install of what ...... I didn't know what you meant ...........[/COLOR]
I mean : remove all printer drivers, all the mess I possibly did with my previous multiple attempts, and re-install.

> [COLOR=#000000]so you have tried printing with all the MF4350 options that are now shown?[/COLOR]
Yes I tried with everything, nothing works. When I try printing, the job in the queue says "Stopped : printer configuration error"

Well......... I don't know what to do now. This evening I will try to remove everything, all printers, maybe re-install/re-initialize CUPS, or anything relating to printing, and try again. Unless you want me to do something before.

Thanks

---

### Post by pdc on 2014-06-24
Hi Jean-David;

one can delete the printer registrations from here [http://localhost:631/printers/](http://localhost:631/printers/)

If you want to delete the printer drivers: the command is > [COLOR="#FF0000"]sudo dpkg -P cndrvcups-ufr2[/COLOR] and then > [COLOR="#FF0000"]sudo dpkg -P cndrvcups-common[/COLOR]

_______________

there are various posts where it worked well for folks: 

[http://blogs.bu.edu/mhirsch/2013/07/canon-imageclass-mf4350d-ubuntu-64-bit-driver-install/comment-page-1/](http://blogs.bu.edu/mhirsch/2013/07/canon-imageclass-mf4350d-ubuntu-64-bit-driver-install/comment-page-1/) and this post 1) installed the drivers and 2) used CUPS to register; 

[http://www.openprinting.org/printer/Canon/Canon-i-sensys_MF4350d](http://www.openprinting.org/printer/Canon/Canon-i-sensys_MF4350d)

______________________

this ubuntu guide talks about printing problems: [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)  ......... what does

> [COLOR="#FF0000"]ls -l /dev/usb/lp* /dev/bus/usb/*/*[/COLOR] give please and also > [COLOR="#FF0000"]sudo usb_printerid /dev/usb/lp0[/COLOR]

_________________________

the guide also talks of > If a print job fails, a job viewer with the failed job ("Stopped" state) and pop-up window telling that the job has problems will appear. If you click the "Diagnose" button, the troubleshooting wizard will open. 

.........do you get anything like that?

---

