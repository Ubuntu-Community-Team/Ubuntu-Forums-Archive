---
title: "update to 11.04, recognizes printer, but won't print"
date: 2011-05-01
forum: Hardware
---

### Post by Arva1 on 2011-05-01
Upgraded to 11.04 from 10.10, recognizes my hp laser jet 1020, says it is ready, but will not print a test page, or from any program, no print que or icon on the top bar. Printer worked fine with 10.10

Any suggestions?

---

### Post by milduser on 2011-05-04
I am having the same problem here with my HP Laser P1006 printer. Installation went on smoothly but won't print. :confused: :(

---

### Post by dimeotane on 2011-05-04
same with upgrade from 10.10 to 11.04
printing on HP LasterJet 1020.  It worked great before this 'upgrade'. 

The printer is enabled. The document print status shows processing/pending but nothing happens on the printer end.

---

### Post by goutas on 2011-05-05
Had the same problem with my HP LaserJet 1020. I followed the directions found at [http://askubuntu.com/questions/38198/hp-laserjet-p1005-stopped-working-after-upgrade](http://askubuntu.com/questions/38198/hp-laserjet-p1005-stopped-working-after-upgrade) and worked out fine.

So, go to Ubuntu Software Center, search for hplip and install it. 

After installation, restart the computer and play around with the settings. After a couple of times I managed to print a test page and the document I needed.

Hope that helps.

---

### Post by Sampux on 2011-05-05
I have a similar problem but with a Epson Epl 6200L. Any suggestions?

---

### Post by mörgæs on 2011-05-05
As a first and easy step I would recommend a reinstall.

---

### Post by Sampux on 2011-05-05
> **mörgæs said:**
> As a first and easy step I would recommend a reinstall.

Just done it but nothing. Same problem. Second step?

---

### Post by Renato_A on 2011-05-08
I've uninstalled and reinstalled hplip-3.11.1 in Ubuntu Natty many times now. By typing hp-setup in terminal, the printer is recognized, the Laserjet 1020 plugin is downloaded and successfully installed and the printer works well.
The problem is, if I turn off the printer and on again, the printer stops printing. If i go to hplip's "Actions" panel and choose the "Download Firmware" option, the green and red printer leds flicker for some time and the printer starts working again. It seems that hplip driver (hijs) is not loading the printer's firmware anymore, when the printer is turned on.
It's going to be extremely disgusting if you have to load the printer's firmware every time you want to do a print  job.
This printer worked fine in Maverick. It's stopped working after Natty's clean install.

Any suggestions?

---

### Post by mörgæs on 2011-05-08
Since this happens for several machines after a fresh install and it worked in 10.10, I would open a bug report in Launchpad:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by EvilMaxWar on 2011-05-08
Same thing is happening with my HP laserjet 1000. I am a new ubuntu user and installed 10.10 two days before 11.04 was released and immediately updated. Did not have time to test if it worked with 10.10 . 

Printer is detected, i send a print job. Printer Status says "processing" then eventually says print job completed but nothing happened. I tried manually downloading firmware. Does not change anything. 
I also tried to "install required plugin"  in hplip but all it says is plugin install failed immediately after user agreement.

---

### Post by Markie_one on 2011-05-09
Hi I've had the same issue with printing since upgrading to 11.04, the  printer (HP laserjet 1020 connected to my desktop via USB) is found ok  the job will be sent to the printer but after a couple of min's the job  dissappears from the print queue and no printing has occured!

 I have now managed to sort the problem today hope this works with a  similar solution for your printers. I opened up the HPLIP imaging and  printing toolbox and selected 'download firmware' from the 'actions'  tab.

When I retried to print test page the printer now works fine. 

Not sure why this has happened printer worked just fine on ub'u10.10

yours 

Newbie

---

### Post by errenay on 2011-05-09
It appears that firmware for my Laserjet P1005 is not loaded automatically.

I think I managed to do it at last. Firstly I installed my printer via
```
sudo hp-setup
``` 
Then I added myself to group "lp", log-out, log-in and installed plug-in and firmware via
```
sudo hp-plugin -i
```
I will try if the firmware is still loaded automatically after shutting down the computer. I hope so...

EDIT: Sorry, but it doesn't work...

---

### Post by errenay on 2011-05-09
OK, it looks like it works.

Instead of hplip based driver, I used recommended by the distro foo2xqx driver for my Laserjet p1005. One more necessary step is to download firmware for your driver (in my case - P1005), using
```
sudo getweb xxxx
```
where xxx is your printer code (see [here for codes]("http://foo2xqx.rkkda.com/")).

---

### Post by Renato_A on 2011-05-20
> OK, it looks like it works.

Instead of hplip based driver, I used recommended by the distro foo2xqx driver for my Laserjet p1005. One more necessary step is to download firmware for your driver (in my case - P1005)

I"ve tried **errenay** suggestion but it didn't work for me.
The only thing that made my Laserjet 1020 function properly in Ubuntu 11.04 was to uninstall hplip and hplip-gui from Natty by issuing the command:
```
 sudo apt-get remove hplip
```
Never mind the many orphan packages it leave like gimp, xsane, and so on.
After that I downloaded from hplip's site the automatic installer hplip-3.11.5.run, which already supports Natty (instructions on how to install hplip from this file you can find in hplip's homepage).
After installing it,I don't have to download the printer's firmware manually every time I want to print something - it's being loaded automatically, as it would in Maverick.:D

---

### Post by Renato_A on 2011-05-22
False Alarm !!! After I turned off the computer and turned it on the following day, the printer sits before me without printing. :x

---

