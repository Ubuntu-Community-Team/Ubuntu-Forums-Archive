---
title: "Samsung ML-2010 Printer Setup"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by briguy on 2005-09-13
Okay, I had a heckuva time setting this printer up, but it works great so I thought I'd share my experience.  This is for Breezy, can't imagine why it wouldn't work for Hoary.

First off, don't bother with the driver disk from Samsung - the setup doesn't seem to work in the no-root user environment of Ubuntu, or at least I couldn't get it to work.

Second, make sure you have the cups and foomatic packages installed.

Plug 'er in, go to System > Administration > Printing and Add Printer.  Select Use detected printer, then select Samsung > ML-4500 and the default driver (gdi).

Finally - IMPORTANT!  [-X   If you are using letter sized paper (we don't use A4 paper in Canada) then do a 

    sudo gedit /etc/papersize & 

and change the "A4" to "letter".  If you don't do this and you use letter sized paper, you will have formatting nightmares that can't be solved with any gui setup!  Then reboot your machine, or if you know what daemon controls papersize, start that (maybe cups, I don't know I just rebooted).

Voila, prints like a charm!

Note to Ubuntu Development Team - it would be nice to have the /etc/papersize set up correctly based on the location information selected during the install.  Nice OS!

---

### Post by Dec on 2005-09-23
Thanks for you comments and inforamtion. I am thinking on getting one of this printers.. I wonder, is there anything you dont like or limitations tha you have found with it ( is been 10 days since you wrote this)? How many sheet per toner/drum so far?

Thanks again,

Dec

---

### Post by briguy on 2005-09-24
It prints fairly quickly - supposedly 22 sheets p/m however I haven't timed it.  Much faster than an inkjet however.  The cost of a cartridge is about as much as the printer - but I'm a home user and I don't expect to use it up in the next couple of years.  I picked it up for CAD$100 at Future Shop, for greyscale printing you can't go wrong.

---

### Post by swartzkb on 2005-09-27
Thanks for you help/hints.
I have a Samsung ML-2250 and using the same driver for the ML-4500 works. Do you know if for the 2250 this is the best driver to use for the ML-2250.
Thanks again for posting your solution.

---

### Post by briguy on 2005-09-28
The 2250 uses a postscript driver.  Do the same as I described above, but select the ml-2250 printer - the driver is a part of ubuntu already.

Cheers

---

### Post by elmo_md66 on 2005-09-28
Guys!
Since where on more or less the same topic, Iam having
trouble installing my HP1205 printer...

Can anyone help me!

Thanks!

Elmo:)

---

### Post by briguy on 2005-09-28
What kind of trouble are you having?  I'm also running a PSC1210, which installed without any difficulty.

---

### Post by jazee on 2006-02-03
I have to thank you so much for posting this. I spent so much time trying to get this to work. Came across your post and vwala. Thanks

---

### Post by nmarshall on 2006-03-16
[QUOTE=briguy]
Plug 'er in, go to System > Administration > Printing and Add Printer.  Select Use detected printer, then select Samsung > ML-4500 and the default driver (gdi).
...
Voila, prints like a charm!
[/QUOTE]

thanks for posting this info, I can print now. \\:D/ 

but I was wondering if you have gotten the Manual Tray to work, have you printed on anything but paper? made labels?

---

### Post by briguy on 2006-03-16
I haven't tried labels but I have done transparencies.  Can't see why labels wouldn't work - you can download templates for OpenOffice here [http://www.worldlabel.com/Pages/openoffice-template.htm](http://www.worldlabel.com/Pages/openoffice-template.htm)

---

### Post by qpackard on 2006-04-04
Hmm, I didn't have the same results you did.
I'm using Ubuntu 5.10 and a Samsung ML-2010 printer.

My path is a little different from yours:
I go to System>Administration>Printing>Printers>Printer>Add Printer. The screen options selected are Local Printer and when I select "Use a Detected Printer", as you suggested, the box says * No Printers Detected* (it says that without selecting Use a Detected Printer, too).
There is no option of Samsung or any brand.
I selected "Use another printer by selecting a port:" and tried every USB port listed (1-16), actually, I tried every option listed, but still the box reads No Printers Detected. I even went ahead and accepted the default (and I tried a USB port, too) and ended up setting up a  Samsung printer 4500 as you suggested but nothing comes out of the printer.
What do you think I have missed?

---

### Post by briguy on 2006-04-04
Is it plugged in? ;)

Seriously though, it sounds like it hasn't been recognized.  Go to a terminal and type:

<code>dmesg | grep usb</code>

The output should show something looking like a printer, look for Samsung or 2010.  (I can't get to that computer right now otherwi  If not, retry plugging it in and retry the steps.

---

### Post by jetpeach on 2006-04-11
Thanks for posting, I have set it up in Kubuntu as you suggested, but when printing a jpeg, I have found the image is very dark - much darker than the preview that is shown or how the image looks itself.  Have you had this same experience?  Maybe it's an application problem, but I tried printing from Gwenview and Krita (kde image viewing programs) with the same results...in Krita the image was also broken up pretty badly. 

Oh, I'm also running Dapper - maybe there are too many variables, but I'd be curious if you have the same results...

Do you know for sure that the driver for the ML-2010 is actually the same as the one?  
Thanks!
jet

EDIT: so i dinked around for a very long time trying to get the official Samsung drivers from their page to work, thinking this would solve my problem.  After fiddling too long with Cups administration junk, I gave up.  Then I found that you can adjust the brightness of something you're printing in KDE (in printer settings somewhere).  I made and it brighter, and it was that simple to fix it.  still using the 4500 drivers and my image looks good, not too dark anymore...

---

### Post by Flamekebab on 2006-06-09
Hi guys, I've got a similar problem.

I've got a Samsung ML-2251N on my network and I cannot for the life of me get the damn thing to print under ubuntu. I have a machine with Breezy but also one with Dapper. No luck with either!

I've tried adding the printer through gnome's printer menu, both as the 4500 and as the 2250 (using the PPD file included with the installer).

I've also tried installing their little proprietary thingy, which prompts me for a root pass, which I obviously don't have!

Could any of you kind souls help an ailing tech monkey?

---

### Post by go2dell on 2006-06-09
Proud owner of an ML-2250 here (same as your 2251N minus the installed network card) and I can help you with getting a root password, but I can save you the trouble by telling you it won't work. :rolleyes: 

```
sudo passwd root
```
**Don't do it.**  An Ubuntu developer might have some sort of convulsion from this, and we can't have that!  OTOH, if you're a heartless, selfish so-and-so, open your Terminal and...

Back to the printer, if you don't really care that much what the printing looks like, you can install the printer as a generic PCL6 and it will print just fine, although the halftoning is awful and you will lose support for some of the printer's specific toner density and resolution functions (everything looks as though it prints in 300dpi, no matter what you choose).  For plain black text, it's fine.  You might even be able to play with the settings and get excellent results.

The 4500 gdi *almost* works.  Print is actually quite good.  Again, the printer seems to ignore the options for toner save, etc.

If you look at the PPD for the ML-2250 it uses a filter called *ppmtospl2*, which converts everything to Samsung Printer Language 2 and flings it on to the printer.   That filter is provided by the Samsung Linux Print Package, which you obviously already have.  I've copied all the PPDs, filters, etc., to their correct CUPS locations, and I still can't get CUPS to respond with so much as an error message, even with the logging at "debug" level.

The only other thing the Samsung installer does is to install an extra "lpr" variant, called "llpr."  It doesn't replace lp or lpr, so CUPS printing to your other printers won't be broken.  I haven't yet discovered where, exactly, it tells CUPS to look for llpr.

It was all working beautifully under Gentoo, but then they switched several major configurations on me in the space of a week, so I decided I wanted to make my life easier by switching to Ubuntu. ](*,)  So far, this is the only thing I haven't been able to make work in under two minutes on Ubuntu.

Fortunately, I haven't deleted any Gentoo system files yet, so I'm digging slowly through them in a brave, Zen-like effort to get this sucker to work.  If I have any breakthroughs, I'll report them here.

---

### Post by GoalieCa on 2006-06-13
I have dapper and amd64 and ML-2251N. I managed to get something going through CUPS (for network). (ie: the cups test page) {hardly a feat for a printer that calls itself linux compatible!!!} Also got a photo to print out from eog at what appears to be 300dpi but it took a good 5 minutes (i wrote this post while waiting). I will test out duplex next (Which also doesn't appear in the windows or mac print options anywhere!! even on the usb)

I used this PPD untouched. 
[http://www.linuxprinting.org/show_driver.cgi?driver=pxlmono&fromprinter=Samsung-ML-2151N](http://www.linuxprinting.org/show_driver.cgi?driver=pxlmono&fromprinter=Samsung-ML-2151N)

I added cupsys to the shadow group. I also restarted the cupsd after that. 

Then i added the printer through cups webadmin. ie: [http://localhost:631/](http://localhost:631/)
My printer used app socket/HP Jet Direct with uri socket://<theIP>:9100 
For some reason it didn't work with the hostname... It automatically discovers it on my mac using bonjour so i might need to get avahi working. Oddly enough the printer doesn't work on my mac when connected over the network. In fact the north american samsung site doesn't have any drivers or anything for it. I had to use the german site (same story as with creative...)

edit:
hmm, it seems to accept the full hostname with the .local. It takes a few minutes to print each time. I must learn to be patient. Also the network printer has a web-conf site of its own. 
[http://samsung.local/index.html](http://samsung.local/index.html)

edit2:
Fixed the speed issue... it resolved itself it seems. Using that ppd and this way of setting it up seems to leave much to be desired. Not much apparent control. The toning looks good (for the image), the resolution can be set to 300,600 and 1200dpi but the duplex setting is once again missing (it appears when connected to usb, however via usb i fail to get anything to print.) At 1200 the cups test page radial lines and color wheel appear far worse than 600. The radial lines also do not appear evenly drawn. There are clear bands from -30 to 30 (and mirroed on the other side) with faint/non-existant lines until the vertical ones. 

edit3: DO NOT USE THE POSTSCRIPT PPD because it prints blank page after blank page. I have not deciphered why. The printer is supposed to support postscript level3.

edit4: I installed the afpl ghostscript and resorted to using the hp ppd. I used ljet4d for duplex. While atm it only shows up to 600 dpi it does print a lot more accuractely. The half-toning though (see color wheel) doesn't quite blend right. I just noticed the plxmono driver doesn't print the border lines for the ruler lines. Yarr... at least its "good enough" for the time being. Not too impressed though... 
Also tried haking up the ppd to make it print 1200 but the scaling seems to be off... I must admit i'm no guru :(

---

### Post by cu_ on 2006-07-05
Thank you for the post OP.  It was very useful.  I have upgraded to Dapper Drake by the time I got my printer.  So I had to use a slightly different method for my printer to work.  Just thought I will share.

On Dapper Drake,  when you connect Samsung ML-2010 printer and go to System->Administration->Printers, it will recognize the printer.  But it wont show any drivers available.  Even if you pick the ML-2010.ppd from the samsung install CD, it does not work.

So this is what I did.  I used cupsys web admin [http://localhost:631](http://localhost:631). 
If you are prompted for a username and password, you own username/password should work.
On this web interface, if you click on adminstration, it will show that ML-2010 is connection and you click on the "add this printer" button.
Now, it shows the list of all samsung printer.  And here, select ML-4500, GDI as suggested by the OP.
Print a test page and you are good to go.

---

### Post by go2dell on 2006-07-12
As of July 11, 2006, Samsung has released a new unified driver that is designed to work with all their printers and multifunction printers.  Using it on Ubuntu requires a few changes from the Samsung way, but it lets you continue to work in the Ubuntu way.

First things first:  turn on your printer so it can be detected.  Now go to Samsung's website to download the driver for your printer.  Extract the file anywhere you like; it will extract into a folder called "cdroot."  I extracted to my desktop, since it was convenient.  Since it's a unified driver, it's the same version for all printers.

To enable everything to work under Ubuntu, you'll need to enable Administrative access for CUPS.  The steps below are actually for Dapper (this thread is increasingly in the wrong location ;) ), so other versions may require changes to this process.  Open a terminal and type:
```
sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart
```

Now you need to actually install the driver:
```
cd ~/Desktop/cdroot
    *** NOTE: substitute the correct location where you extracted the driver ***
sudo ./autorun
```

The driver will install a few files, then it will begin a setup process for your printer.  You can either let the printer setup proceed or you can bypass it; either way, the Samsung process won't work.  This Is Not A Problem (TM).

Now go to *System > Administration > Printing*.  Double-click *New Printer* in the usual Ubuntu way.  When presented with the detected printer list, you may have more than one printer listed.  For instance, I had a printer with just the model name (ML-2250) and another with the full printer name (Samsung ML-2550).  Select the full model name.

At the Printer Driver screen, select SAMSUNG (it's in all caps now) and you'll see the full list of Samsung drivers.  The ones near the top, with just model names, are the CUPS drivers that shipped with Ubuntu.  The ones at the bottom of the list, with the full printer names, are the new Samsung drivers you just installed.  Select the correct one and finish the installation.

---

### Post by mrvw0169 on 2006-07-12
Thanks for the heads up and the guide for the driver... I found that I had to modify the first line of cdroot/Linux/install.sh from #!/bin/sh to #/bin/bash for it to actually work or it will complain of source command not found.

However, now I can't print - the jobs are sent to the printer and live for 10 seconds then change status to "paused"... Any help would be appreciated!

---

### Post by go2dell on 2006-07-12
If I understand your profile correctly, you're using Edgy, so all bets may be off. :rolleyes: 

That said, try removing all your Samsung printers (or maybe even all of them, period).  When you start to reinstall, be sure you select everything with the full name (Samsung ML-2010) instead of just model name (ML-2010).  The model-name-only port did exactly as you describe when I used it.

My only other thought is, did you do something like
```
sudo su -
``` when you installed?  That won't work.  You pretty much have to do just a plain ```
sudo <wherever>/cdroot/autorun
``` to make it work.

And as my uncle used to say, patience is a virtue, but if all else fails just bash the thing.

**edit:**  Forgot to add, I didn't modify anything at all in the autorun file.  I'm not really sure why it would be necessary on a default install, but maybe it's because you're running Edgy? :-k

---

### Post by mrvw0169 on 2006-07-19
Yup, I tried everything you said - thanks! I think it has to do with running Edgy since the printer worked fine in Dapper... I'm going to reinstall Dapper and try again to confirm (maybe even try downgrading my cupsys?) Oh well, thanks anyway.

EDIT: I forgot to mention that I've been configuring this from [http://localhost:631](http://localhost:631) and on the printer page, I see my 2010 detected on MFP_USB_PORT_0 and it successfully starts... However, when clicking Print Test Page or trying to print from any program, it says sending print jobs then quickly turns into this:

MFP_USB_Port_0 **"/usr/lib/cups/backend/mfp failed"**
	Description: ML-2010
Location: Local Printer
Make and Model: Samsung ML-2010 Series (SPL II)
Printer State: stopped, accepting jobs, published.
Device URI: mfp:/dev/mfp/4

As always, any help appreciated!

---

### Post by go2dell on 2006-07-20
I think Edgy and Dapper are currently using similar versions of CUPS.  Mine is 1.2.1 on a pretty much updated Dapper.

My port is usb://Samsung/ML-2250.  That means yours should probably be usb://Samsung/ML-2010.  There were two possible ports presented when I installed using the new driver; the other one (the MFP port) failed to print.

Have you tried ignoring the CUPS Web interface and using System > Administration > Printing?  Works flawlessly that way for me.

Another thing to note:  Samsung has posted a slightly more recent version of the driver.  I think it's just a minor revision for the installer difficulties.

---

### Post by mrvw0169 on 2006-07-20
I can't seem to see the connection at usb:// and the only one that shows up is the mfp:// one that fails all the time... The USB printer seems to be detected (dmesg) and properly loads usblp (checked lsmod)...
```
[17215179.188000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17215179.360000] usb 1-1: configuration #1 chosen from 1 choice
[17215180.096000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04E8 pid 0x326C
[17215180.096000] usbcore: registered new driver usblp
[17215180.096000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
```

My cupsys is 1.2.1-2ubuntu2 but I was thinking maybe because I've been messing around so much I could have broken something (I now have 10? copies of the Samsung 2010 driver showing up in the configuration and I've been running the uninstall.sh before every reinstall too)...

I ignored the CUPS web interface the first few times but no luck since no printers were detected but it shows up as mfp_port_0 or something... Strangely, I also have two other printers "detected" from Canon and Epson when I try to add printer with the web interface - which is weird since I don't have either model and this is my only printer...

Thanks for the tip - I'll go download the more recent driver now and give the whole thing another go since I really want the printer to work again! This time, I'll see if I can ignore the mfp:// port... and appreciate your help!

EDIT: Here's what dmesg is giving me:
```
[17218204.836000] ppdev0: registered pardevice
[17218204.884000] ppdev0: unregistered pardevice
[17218206.416000] ppdev0: registered pardevice
[17218206.464000] ppdev0: unregistered pardevice
[17218270.876000] parport 0x378 (WARNING): CTR: wrote 0x0c, read 0xff
[17218270.876000] parport 0x378 (WARNING): DATA: wrote 0xaa, read 0xff
[17218270.876000] parport 0x378: You gave this address, but there is probably no parallel port there!
[17218270.876000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17218271.028000] lp0: using parport0 (interrupt-driven).
```

Looks like it's trying to access the parallel port but not working...

---

### Post by mrvw0169 on 2006-07-21
After today's cups update, a reinstallation of the new updated printer drivers released a few days ago, and a restart, my printer works!! Thanks for all your help go2dell - much appreciated and now I can finally get some work done!

---

### Post by shanepardue on 2006-07-30
> **go2dell said:**
> As of July 11, 2006, Samsung has released a new unified driver that is designed to work with all their printers and multifunction printers.  Using it on Ubuntu requires a few changes from the Samsung way, but it lets you continue to work in the Ubuntu way.

First things first:  turn on your printer so it can be detected.  Now go to Samsung's website to download the driver for your printer.  Extract the file anywhere you like; it will extract into a folder called "cdroot."  I extracted to my desktop, since it was convenient.  Since it's a unified driver, it's the same version for all printers.

To enable everything to work under Ubuntu, you'll need to enable Administrative access for CUPS.  The steps below are actually for Dapper (this thread is increasingly in the wrong location ;) ), so other versions may require changes to this process.  Open a terminal and type:
```
sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart
```

Now you need to actually install the driver:
```
cd ~/Desktop/cdroot
    *** NOTE: substitute the correct location where you extracted the driver ***
sudo ./autorun
```

The driver will install a few files, then it will begin a setup process for your printer.  You can either let the printer setup proceed or you can bypass it; either way, the Samsung process won't work.  This Is Not A Problem (TM).

Now go to *System > Administration > Printing*.  Double-click *New Printer* in the usual Ubuntu way.  When presented with the detected printer list, you may have more than one printer listed.  For instance, I had a printer with just the model name (ML-2250) and another with the full printer name (Samsung ML-2550).  Select the full model name.

At the Printer Driver screen, select SAMSUNG (it's in all caps now) and you'll see the full list of Samsung drivers.  The ones near the top, with just model names, are the CUPS drivers that shipped with Ubuntu.  The ones at the bottom of the list, with the full printer names, are the new Samsung drivers you just installed.  Select the correct one and finish the installation.
i had reinstalled this printer every different way i could imagine, but i kept getting printouts with text being cut off on the bottom and the margins being off. i followed this thread and i was good to go...tell me, what does this command do "sudo adduser cupsys shadow"?

---

### Post by go2dell on 2006-07-31
As shipped in Ubuntu, CUPS has limited administration capabilities, primarily for added security.  By adding the *cupsys* user to the *shadow* group, you enable full administration, including from the web interface ([http://localhost:631)](http://localhost:631)).  This seems to be required for the Samsung installer to work, as it expects to be able to get full administrative access.

My guess is that you could probably remove *cupsys* from the *shadow* group once you're finished installing the printer, but I've never tried it; in fact, I enjoy the added possibilities for administration, including administration from another computer.  Just be aware that by making the initial change you've enabled another potential security hole for your system.  It's a non-issue if you're using a single-user (home) system, especially if you're behind some sort of firewall or other security system.  If there's any chance your system might be exposed to the Internet, or if you run a multi-user system, this could be a bad idea, so undoing it would be preferable.

---

### Post by mrvw0169 on 2006-07-31
What's interesting is this: had nothing to do and installed so much software that I felt I wanted to start over with the Edgy Knot 1 disk... This time I was determined to get the printer to work without Samsung's driver just because it seems to screw around with me...

So after installing & upgrading everything, all I had to do was System>Admin>Printing>New Printer and the ML-2010 showed up amazingly and all I had to do is select the Samsung ML-4500 model using GDI and, surprise, everything worked! No need to fuss with CUPS admin and stuff beyond that...

---

### Post by go2dell on 2006-08-01
You will likely have a LOT of margin shifting to do with that driver.  On the ML-2250 the image is shifted considerably up and left, meaning some print can be lost, and the margins are just ugly.  It also doesn't properly support settings for different media types well since it's the "wrong" printer (envelopes come immediately to mind).  I also noticed when I tried that driver that the print quality was noticably worse, especially on fine lines and photos.  However, if your needs are modest, using the Generic PCL 6 driver is an even easier way to go, and the print quality is better (although you'll still have margin problems).

---

### Post by Malta Soron on 2006-08-10
@ briguy: Thanks for the Howto! I spend some hours before looking here (*makes a mental note: always look at the forums when installing something!*).
On margins: on the test page the page is shifted upwards, but when I print from Firefox or Writer they're perfectly OK.

---

### Post by mrvw0169 on 2006-08-11
Actually, margins seem to be fine as is - the test page was fine and haven't had a problem printing (primarily) PDF's and documents... Quality is the same as before when it was working with the Samsung driver in Dapper... Not sure about envelopes though since I haven't needed to print on anything special other than "normal" paper...

---

### Post by xbruceyx on 2006-09-06
I am using Dapper Drake. These are the steps I took to get my Samsung ML-2010 printer working.

1) Download the updated Unified Linux Driver from the Samsung Website.

[http://www.samsung.com/support/productsupport/download/Model_Select.aspx?type=Printer&typecode=15&subtype=Laser+Printer&cmssubtypecode=1501&model=ML-2010&filetype=DR&language=]("http://www.samsung.com/support/productsupport/download/Model_Select.aspx?type=Printer&typecode=15&subtype=Laser+Printer&cmssubtypecode=1501&model=ML-2010&filetype=DR&language=")

2) Extract the gzipped tarball and run 'sudo ./autorun' from the cdroot directory. Follow the installation prompts. At 96%, it will ask you to proceed with autodetection of printer - I cancelled that and ended the installer.

3) Select Menu(s) System -> Administration -> Printing and double-click on the New Printer icon. Select 'Samsung ML-2010' and then click forward, select driver 'SAMSUNG' , and finally 'Samsung-ML-2010-Series-(SPL-II)' for the specific model driver. Apply the settings and the printer should be good to go.

---

### Post by ORiON2012 on 2006-09-15
Awesome, the Samsung ppd works without a hitch for me on Dapper with my ML-2010. Thanks for the tip. I've been without a printer for a while as I gave up on Samsung's drivers, now everything seems to work.

---

### Post by insub2 on 2006-09-27
I assumed using the Samsung go2dell suggested ([in post #18]("http://ubuntuforums.org/showpost.php?p=1244456&postcount=18")) would work best.  I was wrong.  My prints got an extra 1" of nothing at the top of the page which pushed everything down, cutting the bottom off.  So I used the ML-4500 driver and the other stuff briguy said.  Did a test page and the half tones have all kinds of lines through them.

What should I do?

**EDIT**

uuu i missed a step from go2dell's instructions:
```
sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart
```

cought it on a re-read and feel dumb - haste makes waste, so they say.

anyway, everything seems to be in order.

---

### Post by go2dell on 2006-09-27
I had problems with halftones and with the page being shifted to the left somewhat using the 4500 GDI driver.  Which version of the Samsung driver were you using?  They've updated it a few times now.  The latest version is producing some photo problems for me, but otherwise it works great.  The installer also seems to be fixed so it no longer requires the whole dog-and-pony show to get it installed, but it still requires installation, followed by Ubuntu installation.

---

### Post by insub2 on 2006-09-27
> **go2dell said:**
> I had problems with halftones and with the page being shifted to the left somewhat using the 4500 GDI driver.  Which version of the Samsung driver were you using?  They've updated it a few times now.  The latest version is producing some photo problems for me, but otherwise it works great.  The installer also seems to be fixed so it no longer requires the whole dog-and-pony show to get it installed, but it still requires installation, followed by Ubuntu installation.

Thank you very much, go2dell.  If you note the edit to my last post you'll see it was my fault.  Everything is beautiful (have yet to try a picture).  I am using the latest drvier from Samsung's site.

---

### Post by shanepardue on 2006-10-01
ok, i installed this printer on a new computer forgetting to check this guide and i didn't add the admin cups user before installing thus the margins are off. i tried uninstalling the printer drivers and removing it from cups and starting over after adding the user, but still no go. on a weird note, it prints perfectly on the network, just not on the local computer. please help me!! thanks

---

### Post by azidrane on 2006-10-25
> **xbruceyx said:**
>  and finally 'Samsung-ML-2010-Series-(SPL-II)' for the specific model driver

I spent two weeks on this one, ONLY BECAUSE I didn't SCROLL DOWN!!!!

Thanks for this one mate, you'll forever be in my good books.

Cheers!

---

### Post by shanepardue on 2006-10-25
i got the margins corrected by setting the page orientation to letter in the cups web-based utility. sweet!

---

### Post by factor on 2006-10-27
Hi, i enabled cupsys administration (shadow, restart...), but when i try to install samsung drivers i get the following error:

install.sh: 1230: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted

I'm using Edgy, with AMD64 processor and the generic kernel that comes bundled with Edgy.

Any idea on how to solve that? 

Regards.

---

### Post by factor on 2006-10-27
Btw my printer is a Dell 1100, it worked in dapper with ML-1000 driver but after upgrade it doesn't work anymore. I tried removing it and readding it but now it isn't even detected in cups as an usbport, thoug it is on /dev/usblp0.

Thanks in advance for your help.

Regards.

---

### Post by paran on 2006-10-28
> **factor said:**
> Hi, i enabled cupsys administration (shadow, restart...), but when i try to install samsung drivers i get the following error:

install.sh: 1230: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted

I'm using Edgy, with AMD64 processor and the generic kernel that comes bundled with Edgy.

Any idea on how to solve that? 


Best idea, that I have:"Install Dapper Drake."

I got same error with my Samsung clp-500 - driver, when I tried install in Edgy i386 and I'm not alone.

Driver works with Edgy, but it's hard to install.

I used: 20060711104257781_UnifiedLinuxDriver.tar.bz2 - file from Samsung's wep pages.

How I installed this driver (, and if you REALLY need Edgy and know how to do it) ?
First you must sure what you doing ?
principles:
2. Install Dapper Drake
3. Install Samsung's Linux drives
4. Upgrade to Edgy
I'm not sure does works upgrating tools, because I did different way (hard way, eq. I broke my X system)

I still recomend use Dapper don't upgrade to Edgy. I'm not sure does Samsung's driver work in 64bit version at all.

---

### Post by Scunizi on 2006-11-09
I found after installing the driver you still have to go to System/Admin/Printers and add the new printer normally.  The driver will show up now.

---

### Post by shanepardue on 2006-11-11
I have had so many bugs get fixed with my hardware that I can't afford to 
go back to dapper. I hope a fix for this comes soon!

---

### Post by SF100 on 2006-12-22
> **jazee said:**
> I have to thank you so much for posting this. I spent so much time trying to get this to work. Came across your post and vwala. Thanks

This did get me printing but when I print a test page it seems to be cutting off the bottom of the page even after:

sudo gedit /etc/papersize &

---

### Post by shanepardue on 2006-12-23
> **SF100 said:**
> This did get me printing but when I print a test page it seems to be cutting off the bottom of the page even after:

sudo gedit /etc/papersize &
What's your paper size is system > administration > printers? Should be letter there also.

---

### Post by M8M on 2006-12-30
Great info! I´ve had to refer back a few times. I like it b/c it´s straight forward and easy to follow.

M8M

---

### Post by Mungojerrie on 2007-05-17
> Okay, I had a heckuva time setting this printer up, but it works great so I thought I'd share my experience. This is for Breezy, can't imagine why it wouldn't work for Hoary.

First off, don't bother with the driver disk from Samsung - the setup doesn't seem to work in the no-root user environment of Ubuntu, or at least I couldn't get it to work.

Second, make sure you have the cups and foomatic packages installed.

Plug 'er in, go to System > Administration > Printing and Add Printer. Select Use detected printer, then select Samsung > ML-4500 and the default driver (gdi).

Thank you sooooo much for this - I have spent hours trying to set up my ML-2010 on Feisty, and failed miserably every time. Just followed your instructions, and now it prints perfectly!

Cheers, you have really made my day!!!!! Off to see if it works with my Epson inkjet now!
:)
Linda.

---

### Post by HereticPriest on 2007-10-26
oook. I tried doing it several ways now. i never actually got the printer to do anything. i have ubuntu dapper drake - the last way i tried actually at least printed something. but it still doesnt seem to be correct. i used that unified linux driver from the samsung page as before described. however after completing the whole script (there was no autodetection for me at 98% of the script) it did print a test page, only it wrote "INTERNAL ERROR - Please use the proper driver." on my test page. this is very strange since i really did select "SAMSUNG ML-2010 Series (SPL II) [English]" which appears to be my printer. Can anyone tell me what still might be wrong ?
By now i found out that i can even delete the printer in Menu(s) System -> Administration -> Printing and add it new, i will at least get a printing result as long as i use mfp:/dev/mfp/4 as URI and not usb://Samsung/ML-2010 as i used before, which didnt print anything at all. could anyone enlighten me at all ?

---

### Post by warjowuch on 2007-11-17
Well, yesterday I bought this printer with R, so it is the ML-2010R. Works out of the box on ubuntu 7.10.
Only, I had to really push the toner-cartridge until it 'clicked' and did not come out when I let it go... Now when it's stuck, I prints just fine on 7.10.

So, maybe you have to wait until Hardy, when you only want to use LTS-releases? But I sure hope you get it to work before that :)

---

### Post by hevimees on 2008-05-05
First post ever for me, hi everyone :)

I have the ML-2010R as well. It worked out of the box with 7.10, but stopped working after upgrading to 8.04.

I followed the instructions given in the first post and now it seems to work again.

---

### Post by Spartnova on 2008-05-06
The method in the first post also resolved my issue with a Samsung ML-2510 that worked out of the box on 7.10 but stopped working after the upgrade to 8.04.

---

### Post by Sabrage on 2008-05-15
> **Spartnova said:**
> The method in the first post also resolved my issue with a Samsung ML-2510 that worked out of the box on 7.10 but stopped working after the upgrade to 8.04.

Me too!

---

