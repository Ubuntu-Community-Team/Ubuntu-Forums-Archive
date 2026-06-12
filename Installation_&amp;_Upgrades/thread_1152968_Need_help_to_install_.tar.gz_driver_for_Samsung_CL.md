---
title: "Need help to install .tar.gz driver for Samsung CLP-310 printer"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by isa.k on 2009-05-08
Hello Fellow** Ubuntu**ans,


I made the big jump to Jaunty (AMD64) today.

I need to get a few things fixed, but at the moment, will take things one step at a time...

For now, I would like to install one of the [_official drivers_]("http://www.samsung.com/hk_en/consumer/detail/support.do?group=printersmultifunction&type=printersmultifunction&subtype=colorlaserprinters&model_nm=CLP-310&disp_nm=CLP-310&language=&cate_type=all&dType=D&mType=DR&vType=&prd_ia_cd=06010200&model_cd=CLP-310/XSS&menu=download") for my [_Samsung CLP-310 printer_]("http://www.samsung.com/hk_en/consumer/detail/detail.do?group=printersmultifunction&type=printersmultifunction&subtype=colorlaserprinters&model_cd=CLP-310/XSS").

Problem is, all Linux drivers there are tarballs, and I have absolutely no idea on how to do this.

Any help would be greatly appreciated.


**isa**

[SIZE=1]**PS:** I downloaded the [/SIZE][[SIZE=1]_Unified Linux Driver (ver.3.00.37)_[/SIZE]]("http://javascript%3Cb%3E%3C/b%3E:sendIt3%28%27/hk_en/consumer/detail/support.do%27,%27printersmultifunction%27,%27printersmultifunction%27,%27colorlaserprinters%27,%27CLP-310%27,%27CLP-310%27,%272031913%27%29") [SIZE=1]and once I get thos up and running, I would like to install the other apps as well :)[/SIZE]

---

### Post by Bachstelze on 2009-05-08
There are installation instructions on Samsung'w website. Did you try to follow them?

---

### Post by isa.k on 2009-05-08
> **HymnToLife said:**
> There are installation instructions on Samsung'w website. Did you try to follow them?
No, I must have missed it... I tried looking for it, but could not locate where it was exactly...

Could you please provide a link perhaps?

Thank you :)

**_ADDENDUM:_ I had a look at the pdf and it was based upon the win version of the installer... and it just shows what to do once the app is running, not how to extract and execute.**

---

### Post by isa.k on 2009-05-09
I found this on the installation disc (I never really looked until I saw another thread regarding the CLP-310):> **Samsung Unified Linux Driver installer**

 **Welcome**

 You are about to install Unified Linux Driver package. 
 Samsung Unified Linux Driver package is the accompanying software for Samsung printers and multifunction peripherals (MFP). The package supports printing with all devices and scanning with MFP on Linux platform.
 The primary goal of the package design is maximum convenience and ease of use. The package contains not only printer and scanner drivers themselves, that is, low level software providing a principal ability to print documents and to scan images. The package also delivers powerful applications for configuring your devices and further processing of scanned documents.

 **Dependencies**

 Unified Linux Driver package depends on printer and scanner services provided by Common Unix Printing System (CUPS - [www.cups.org]("http://www.cups.org/")) and Scanner Access Now Easy (SANE - [www.sane-project.org]("http://www.sane-project.org/")) system packages. These components are mutually necessary for the drivers to work properly. In addition, Ghostscript application ([www.ghostscript.com]("http://www.ghostscript.com/")) is required for correct functioning of the printer drivers.
 Installer tries to detect if the components are installed and have proper versions. In case necessary component is not installed, it is recommended to interrupt the installation by clicking *Cancel* button and to install the component from the Linux distribution disk, Web site of the Linux vendor or Web site of the vendor of missing environment component (see references above).
There is possibility to ignore absence of an environment component. In such a case press *Skip All* button to proceed to further installation stage. If environment components are skipped, please, do not forget to install them before usage of the Unified Linux Driver.
In any case **CUPS must be installed before Unified Linux Driver**, or printing will not be available. If you did installation without CUPS and would like to install CUPS later, you should uninstall Unified Linux Driver, install CUPS and then install Unified Linux Driver again. 

 **Samsung Unified Linux Driver installation**

 Samsung Unified Linux Driver package is being installed automatically displaying progress indicators for overall installation and for particular parts of the package.
 At the time of installation only *Help* button is available.
 In case of any error a message box is displayed to show the problem's origin. Possible problems can arise in case of absence of necessary environment components. In this case, please, exit the installation, set up the necessary environment packages and run installation of Samsung Unified Linux Driver package again. 

 **Success**

 Congratulations! Samsung Unified Linux Driver package is installed successfully.
 Enjoy using reliable Samsung Hi-Tech device!
 Click *Configurator* icon on your desktop to start.
I tried going to [http://www.cups.org](http://www.cups.org) to see what needed being DL'd before I should install the CLP-310 driver, and got even more lost  :confused:


(Why do I hear people :-({|= ??? LoL :D)

---

### Post by isa.k on 2009-05-09
***bump***

---

### Post by isa.k on 2009-05-13
***Bump0r***

---

### Post by tommcd on 2009-05-13
**linuxprinting.org** is a great reference site for how to set up printers in linux. For your printer:
[http://openprinting.org/show_printer.cgi?recnum=Samsung-CLP-310](http://openprinting.org/show_printer.cgi?recnum=Samsung-CLP-310)
Just downlaod the .tar.gz driver package from Samsung's website to your home directory. Then to untar the driver open a terminal and run:
```

tar -xvzf UnifiedLinuxDriver.tar.gz 

```
This will create a directory named **cdroot**. Inside it will be another directory called **Linux**. You will cd into the Linux directory:
```
cd chroot/Linux
```
Then run:
```
sudo install.sh
```
like it says on the page I linked to. Save the Linux directory, since there is an uninstall script there as well if you ever want to uninstall the driver.
You may need to install the build-essential package from the ubuntu repos for the driver to install correctly. Try it first without it though.

---

### Post by isa.k on 2009-05-13
> **tommcd said:**
> **linuxprinting.org** is a great reference site for how to set up printers in linux. For your printer:
[http://openprinting.org/show_printer.cgi?recnum=Samsung-CLP-310](http://openprinting.org/show_printer.cgi?recnum=Samsung-CLP-310)
Just downlaod the .tar.gz driver package from Samsung's website to your home directory. Then to untar the driver open a terminal and run:
```

tar -xvzf UnifiedLinuxDriver.tar.gz 

```
This will create a directory named **cdroot**. Inside it will be another directory called **Linux**. You will cd into the Linux directory:
```
cd chroot/Linux
```
Then run:
```
sudo install.sh
```
like it says on the page I linked to. Save the Linux directory, since there is an uninstall script there as well if you ever want to uninstall the driver.
You may need to install the build-essential package from the ubuntu repos for the driver to install correctly. Try it first without it though.
Thank you ever sop much for that bit of info... Now as soon as I can get my dual boot to work successfully, I will try that, I do not think I can install hardware whilst booted off Live CD?

Again, thank you for that. That bit of info seems like it is real spoonfed stuff, exactly what I need :D

---

### Post by tommcd on 2009-05-13
> **isa.k said:**
>  Now as soon as I can get my dual boot to work successfully, I will try that, I do not think I can install hardware whilst booted off Live CD?

Yes, wait untill you have Ubuntu installed to install the printer driver.
Actually, try to setup the printer first without installing the driver. There is a chance that Ubuntu may recognize the printer with drivers present in the linux kernel.

---

### Post by isa.k on 2009-05-13
Nope, can't do it.

I have tried installing the 315's driver, and can now print b&w, not colour.

Will let you know how it goes once I have got through the issues...

Again, thank you :)

---

### Post by phuki on 2009-05-13
Hello,

on my 8.10 version, just pluging the usb did the trick for me. The printer was immediatly recognized and could be used at once.

Haven't tried yet on jaunty though. Let me try and i'll give you some feedback

---

### Post by isa.k on 2009-05-13
Yeah, that would be great...

Mine was 'recognised' as well, however, the drivers closest to it were the 300 and 315 models.

I use the 315 driver at the moment, and print in b&w... Better than nothing I guess?

---

### Post by phuki on 2009-05-13
Just tried it and you're right, the printer is not really recognised, altough I'm pretty sure it was in 8.10. Maybe because Jaunty is still too recent...
Then I tried the way suggested by tommcd but it didn't work either.

Something else i tried: in the "cdroot" folder there's an "autorun" file , inside which is a command saying:
"*exec sh $BASE/Linux/install.sh*"
 so i did in the terminal: ```
sudo exec sh /home/*USERNAME*/cdroot/Linux/install.sh
```a line appeared saying some "lib..." files were not found but I couldn't read for the terminal immediately disappears.

so now, I'm stuck at that point.

---

### Post by isa.k on 2009-05-13
> **phuki said:**
> /...snip.../a line appeared saying some "lib..." files were not found but I couldn't read for the terminal immediately disappears.

so now, I'm stuck at that point.

Perhaps a finger hovering above the PrintScreen button just before you expect it to pop up and disappear, and if you are quick enough, you may be able to hit the key on time, so as to be able to give us all a glimpse of what it is exactly?

Just an idea...

... ok, wishful thinking :oops:

---

### Post by phuki on 2009-05-13
in progress...

edit: sorry, that's the best I could get


[IMG]http://img15.imageshack.us/img15/7555/capture3b.png[/IMG]

it says: "cannot create a temporary cache file" and "permission not granted"

I quickly searched on google but haven't found anything relevant yet

---

### Post by phuki on 2009-05-13
A little off topic but may I ask you: does your printer have a fan ejecting the air out of it? There are ventilation grids on both side but no fan behind them. Thus no air is blown, and that makes my printer very hot (especially when printing in colour). Plus the smell.

It seems weird to me and I wonder whether my printer is defective? thank you

---

### Post by isa.k on 2009-05-14
> **phuki said:**
> A little off topic but may I ask you: does your printer have a fan ejecting the air out of it? There are ventilation grids on both side but no fan behind them. Thus no air is blown, and that makes my printer very hot (especially when printing in colour). Plus the smell.

It seems weird to me and I wonder whether my printer is defective? thank you
LoL! Yeah, mine gives off a peculiar smell...

I haven't delved in depth with the how and why of it, as it is only a week old, if that. And half of that time, I was not able to use it.

But it did smell rather peculiar when it did its first print job (test print).

Again, I do not know if it is particularly only when colour jobs are being done, or when any print job is being done.

As for the fan, I dunno about that? How could I tell?

---

### Post by phuki on 2009-05-14
Good news  :D

I finally got it working, in colour and everything!

Forget about the "lib..." files. The answer was right in front of me but I just didn't use the right command (or did I?). It's so simple, actually.
Just do the following: download the file to whatever location (let's say */home/USERNAME/ *to make it simple) and extract it by right-clicking on the tar.gz, then "*extract here"*.

Open a terminal, and browse into the extracted folder named *cdroot* :
```
*cd /home/USERNAME/cdroot/*
```There's an *autorun* in it which we are going to run:
```
*sudo ./autorun*
```and... that's it!!! A window will pop up and everything goes smoothly :)

Another method, which will also be used to install the other 2 files (smartpanel + psu), you don't need to browse into the folder, simply execute the *install.sh*:
```
*sudo /home/USERNAME/cdroot/Linux/install.sh*
```Source: [http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

It's as simple as that, but come to think of it, it's exactly the same way Tommcd explained in the first place :oops: But I still couln't do it even with the typo corrected (c**d**root, not c**h**root). Anyway, thank you very much Tommcd ;)

As for the fan, I'd be grateful if you could just tell me whether or not you can feel some air blown out from the printer at some point. Thank you!

---

### Post by isa.k on 2009-05-14
Thank you **phuki** for that great bit of research :)

I am still waiting for a one on one session with a great deal of knowledge in Ubuntu, in getting me to Install Jaunty alongside with Vista, and am now using Vista till that happens.

I just pressed the power button for a few seconds and let go, so it would print a test page.

I ran my hands around the printer's vent slots whilst it was printing, and I don't know if it was an illusion, or reality, but I think I may have felt an ever so soft breeze brush against my hand at one point...

But then again, I am quite serious, it could have just been my imagination as well?

Put it this way, if someone said, "Would you bet your life on the printer blowing out any air whilst it was printing?"

The answer quite simply would be, "No."

If there was any air being blown out, it was extremely subtle, that is for sure.

I hope that answered your query :)

---

### Post by phuki on 2009-05-14
Thank you very much for your precious help on this. I don't know anyone around me that owns this printer, so I couldn't ask. Now I know my printer is in good state.

I hope you'll be able to install these drivers properly and enjoy your shiny colourful printed documents. If ever you need help installing a dual boot vista/ubuntu, you can PM me.

Thanks again isa.k ;)

---

### Post by sampsung on 2009-11-19
Hi, thank you for the info. They now have Ubuntu specific installation instructions here:
[_Samsung CLP-310 printer_]("http://www.samsung.com/hk_en/consumer/detail/detail.do?group=printersmultifunction&type=printersmultifunction&subtype=colorlaserprinters&model_cd=CLP-310/XSS"). 

But could somebody please, please tell me is it possible to print using the WLAN connection in Ubuntu?

I prepare this printer to be used in a public library. Currently, the customers can't print at all. So, any help would be really appreciated.

And please keep it simple and stupid to us noobs :).




[]("http://kaannos.com/sanastot/haku/englanti-suomi/appreciated")

---

### Post by isa.k on 2009-11-19
> **sampsung said:**
> Hi, thank you for the info. They now have Ubuntu specific installation instructions here:
[_Samsung CLP-310 printer_]("http://www.samsung.com/hk_en/consumer/detail/detail.do?group=printersmultifunction&type=printersmultifunction&subtype=colorlaserprinters&model_cd=CLP-310/XSS"). 

But could somebody please, please tell me is it possible to print using the WLAN connection in Ubuntu?

I prepare this printer to be used in a public library. Currently, the customers can't print at all. So, any help would be really appreciated.

And please keep it simple and stupid to us noobs :).




[]("http://kaannos.com/sanastot/haku/englanti-suomi/appreciated")
Thank you so much for that :D

Will definitely come in useful for next time ;)

---

### Post by dibuntux on 2010-01-14
I would like to add on a possible problem that happened to me:
I've connected my CLP-310 to my Ubuntu 9.10 AMD64 PC, and immediately the printer was recognised by the system. I tried printing with it, but a page with SPL error came out - install the specific Samsung driver. OK, I did using the provided instructions, and everything went fine except when finding the USB port. The installation could not find automatically the printer. Of course I deleted the previous finded one in the panle. So I tried disconnecting & reconnectiong again the USB cable, and Ubuntu just added again automatically the printer with internal driver.
So I just completed the Samsung installation manually giving a port; it did not work.
What did work was to take the Device URL: of the Ubuntu Auto recognised printer from Properties/Settings in the panel, and copying it to the Samsung installed printer in the same place:
Device URL: usb://Samsung/CLP-310%20Series

That worked OK!

---

