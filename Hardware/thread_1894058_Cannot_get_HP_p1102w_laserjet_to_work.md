---
title: "Cannot get HP p1102w laserjet to work"
date: 2011-12-11
forum: Hardware
---

### Post by Maskedrose on 2011-12-11
I printed a test page for Ubuntu a few days ago... so I am really unsure of what is going on. Everytime I try to print something.. it just keeps on attempting to print and either reports as printed or print failed... right now I have 18 pages in queue, none of which are printing... I cant get a test page to print either.. I have the default printer management installed. 

What can I do?

---

### Post by BC59 on 2011-12-11
You have to install the app hplip from the Ubuntu Software Center

and check here:

[http://ubuntuforums.org/showthread.php?t=1479670](http://ubuntuforums.org/showthread.php?t=1479670)

---

### Post by Maskedrose on 2011-12-11
* I tried that app :(*

---

### Post by bluexrider on 2011-12-11
this is the recommended driver install 3.10.4

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_p1102w.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_p1102w.html)

Ubuntu docs 

[https://help.ubuntu.com/10.04/printing/C/printing.html](https://help.ubuntu.com/10.04/printing/C/printing.html)

if you have CUPS installed open your browser an go to [http://localhost:631](http://localhost:631)

---

### Post by Maskedrose on 2011-12-11
>_< I just tried the download from that link and when I get to the command prompt that tells me to unplug and re plug my printer.. the install fails..

---

### Post by bluexrider on 2011-12-11
> **Maskedrose said:**
> >_< I just tried the download from that link and when I get to the command prompt that tells me to unplug and re plug my printer.. the install fails..

unplug the printer.
run install again.
when prompted plug in the printer.

---

### Post by Maskedrose on 2011-12-11
I keep getting "PRINTER SETUP
-------------
Please make sure your printer is connected and powered on at this time.
error: hp-setup failed. Please run hp-setup manually. "

What do I do from there? >_<;;;

---

### Post by bluexrider on 2011-12-11
> **Maskedrose said:**
> I keep getting "PRINTER SETUP
-------------
Please make sure your printer is connected and powered on at this time.
error: hp-setup failed. Please run hp-setup manually. "

What do I do from there? >_<;;;


HP manual install instructions here

[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

---

### Post by Maskedrose on 2011-12-11
Ok.. so I went into Applications ... > system tools > printer and deleted and added the printer... and now it is printing again (for now..)

however what I have noticed is Applications(gnome drop down menu) > system tools> says reactivate hp laserjet 1018/1020 after reloading paper.

I don't have that kind of printer? and when I click on it I get an error box that says  

--------------------------
Could not launch 'Reactivate HP LaserJet 1018/1020 after reloading paper'
Failed to execute child process "wish" (No such file or directory)
-----------------------

O_O what happened? How do I get rid of that? X_X ugh I suddenly hate printers.

---

### Post by Maskedrose on 2011-12-11
So I went through the manual install you linked me too and that worked(I had to refresh a few times to find my printer) and I think it is fine now.. but no manual duplex printing support it seems. :( Ah can't have cake and eat it too eh?

thanks for your help so far though!

---

### Post by bluexrider on 2011-12-12
> **Maskedrose said:**
> So I went through the manual install you linked me too and that worked(I had to refresh a few times to find my printer) and I think it is fine now.. but no manual duplex printing support it seems. :( Ah can't have cake and eat it too eh?

thanks for your help so far though!
okay, well we got you going.

please mark this (SOLVED)

---

### Post by dooper on 2012-07-21
May i also suggest this excellent page which does work in getting this printer going..

[http://www.niftiestsoftware.com/2011/07/17/the-hp-laserjet-p1102w-printer-on-ubuntu-11-04/](http://www.niftiestsoftware.com/2011/07/17/the-hp-laserjet-p1102w-printer-on-ubuntu-11-04/)

Also,,when you do get it working....if you ever changed the SSID of your router either by simply changing it or swapping routers i would strongly suggest that you first login to the print server configuration page of the printer using your old router or SSID and manually enter the new SSID.If you dont then you may well find that you wont be able to connect again as the printer wont see your new SSID and it seems all but impossible to reset the printer to standard mode i.e purge the stored network details.

---

