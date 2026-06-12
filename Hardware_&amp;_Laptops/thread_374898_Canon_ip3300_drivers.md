---
title: "Canon ip3300 drivers"
date: 2007-03-03
forum: Hardware &amp; Laptops
---

### Post by lotv on 2007-03-03
I bought a nice canon ip3300 printer yesterday, and cannot find drivers to make it work properly, i tried the canon ip4000 drivers but it does not print correctly. Can you tell me which ones i should try or where i can find specific drivers for this printer?

---

### Post by patrickfromspain on 2007-03-03
I have a canon ip3000.. and my experience is: use windows for printing. Had bad luck with any drivers that were out there. 

You could check turboprint, maybe. [www.turboprint.info](www.turboprint.info)

---

### Post by ellis rowell on 2007-03-03
I support Patrick's comment. I have a Pixma IP1600, CUPS doesn't want to know about it, I have a licensed Turboprint and can't get it to overide CUPS. The Gimp is a particular problem with this.

It's a good job I have an Epson Stylus C680, it works far better under GNU/Linux than it ever did under Windoze.

---

### Post by exactopposite on 2007-03-30
i have an ip3000 and i ahve used the info on this link with great success. it uses drivers from canon japan and it has step by step instructions for how to install.

[http://tinyurl.com/386y7b](http://tinyurl.com/386y7b)

---

### Post by ramjet_1953 on 2007-03-31
If you go here, it should help:

 [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP3300](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP3300)

ALWAYS check first about compatibility BEFORE purchase.

There are may Lexmark owners who have a paperweight.

Regards,
Roger :cool:

---

### Post by Rospo Zoppo on 2007-04-30
> **ellis rowell said:**
> I support Patrick's comment. I have a Pixma IP1600, CUPS doesn't want to know about it, I have a licensed Turboprint and can't get it to overide CUPS. The Gimp is a particular problem with this.

It's a good job I have an Epson Stylus C680, it works far better under GNU/Linux than it ever did under Windoze.

Hey man the ip1600 works here... 2200 drivers works...

---

### Post by Jim Connachan on 2007-08-26
I cobbled the following together from different threads and it worked for me.

How to install Canon ip3300 printer

            Install the alien conversion programme from the Synaptic Package Manager

           
Download the following files from [ftp://download.canon.jp/pub/driver/bj/linux](ftp://download.canon.jp/pub/driver/bj/linux)


cnijfilter-common-2.70-1.i386.rpm and cnijfilter-ip3300-2.70-1.i386.rpm

These should appear in the desktop.
Create a new folder e.g. canon in your home folder

            mkdir canon
            cd canon

Copy the rpm files to the canon folder

Install the following files using the commands

sudo apt-get update
sudo apt-get install alien libxml1 libpng12-0 libpng12-dev libgtk1.2 libgtk1.2-common

Convert the RPM packages to Debian packages using:

            sudo alien -c cnijfilter-common-2.70-1.i386.rpm cnijfilter-ip3300-2.70-1.i386.rpm

            Install the deb packages using

            sudo dpkg -i *.deb

            Make sure the library links are correct using the following

            sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

            sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.3

            sudo ln -s /usr/lib/libtiff.so.2 /usr/lib/libtiff.so.1

           

             Make the loader aware of the changes

            sudo ldconfig

             Restart cups

             sudo /etc/init.d/cupsys restart

             Go to System/Administration/Printing 

             Click on New Printer

             Chose Forward

            Select Canon from list of printers

            The printer should be in the Canon list as ip3300 Ver.2.70

             Select this option and click on forward.

             The printer icon for the ip3300 should now appear in the printer option

             It should now be ready to be tested.

             To access the maintainence functions on the printer use the following in the terminal

             cngpij -P iP3300-Ver.2.70

             N.B.  I also copied the file canonip3300.ppd from /usr/share/cups/model/ to 
                       /usr/share/ppd/pstocanonbj/ although I am not entirely sure this is necessary.                      
                       This method has been used to install the driver to an Acer Travelmate 4233WLMi 			        laptop and my other system. This method is a hotchpotch of different forum                                    threads about Canon printers. The Turboprint driver also works when printing but will 			overprint photos with their logo when used at high resolutions.

---

### Post by flyscan on 2007-09-03
Thanks for the instructions. Got it working as a network printer, with the windows box serving. Just used the synaptic package manger to get alien. 

Is is possible to access some of the other functions available on this printer. I followed something similar to [A.Lizard's guide]("http://www.crn.com/white-box/167600449?pgno=2") and [this similar guide]("http://ubuntuforums.org/archive/index.php/t-45609.html") for the iP1000 putting these values in the ppd file:
> *OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 4800/1200 dpi: "<</HWResolution[4800 1200]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality
Just printed out a two test pages, one with the high res. option select and the other in 600x600 with Economy. There was no noticeable difference between the two in quality; the hi res mode was slower. Not sure if the above code is just making drop down menus in the Gnome printer settings or if it is sending useful commands to the printer. 

Could not get duplex printing working... anyone have any ideas, other than Turboprint?

Thanks again for the good writeup, Jim.

---

### Post by ghettowarrior on 2007-09-12
got it working, the driver but still the dpi settings dont work

daniel

---

### Post by nohairleft on 2007-09-12
Had the same problems with my canon iP series printer, turbo print worked out to be the best option.

But to cut a long story short, My Linux box died and I am not in the mood to get another up and running at the moment, so here is an offer someone can not refuse.

I have a full paid up turboprint key sitting here doing absolutely nothing, the first person to PM me with legit printer probs can have it. It wont be given to anyone else, just the first person. I trust who ever gets it wont distribute it around...

Have fun folks, one day I may get another box up and running..

---

