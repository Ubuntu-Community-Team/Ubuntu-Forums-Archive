---
title: "HOWTO:  Lexmark Z600 series printer."
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by zerhacke on 2006-04-13
Here is a howto to get a Lexmark Z600 series printer working.

Go to [http://www.autostatic.com/linux/lexmarkz605-suse93.html](http://www.autostatic.com/linux/lexmarkz605-suse93.html) . Download the drivers found at [http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz) . Save this file to disk, preferably in your home folder.  Open a terminal.

In the terminal, type ```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
```

This will extract the file.

In a terminal, type ```
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz

```

This will create a new tar file named install.tar.gz.  In a terminal type ```
tar -xvzf install.tar.gz
```

This will create many files, as it extracts the contents of the install.tar.gz file you just created with tail.  You're interested in the two RPM files.  If you don't have alien installed on your computer, in a terminal type ```
sudo apt-get install alien
```  You will need your Ubuntu install CD for this.

After you have alien installed, you want to issue the following commands.

```
sudo alien filename.rpm
```

Since you have two RPM files you will need to alien twice, once for each RPM file.  Replace filename with the name of the two RPM files.  Do one then the other, do not try to do both at the same time.

Alien creates two DEB files, one for each RPM file.  Install both DEB files by issuing in a terminal ```
sudo dpkg -i filename.deb
```  Do one then the other.  Do not try to do both at the same time.

Once you have dpkg'd both files, the drivers are installed.  There is a little bit more work to do though.

In a terminal, enter ```
sudo ldconfig
```  This will get the system ready for the drivers.

Now, reboot.  If you do not reboot the drivers will not show up on the list of available drivers on the printer installation wizard.  So, reboot.

Once you've rebooted, enter Gnome.  This may work with other window managers, but I have only tested it in Gnome.  Click System - Administration - Printing.  Choose Lexmark for the manufacturer and the Z600 V 1.0-1 will be available.

Happy printing!  By following this tutorial you can also print to SMB shared printers so long as the printer shared is a Lexmark Z600 series.

---

### Post by zerhacke on 2006-04-13
I knew I forgot something.  I'd like to state that this method will allow a Lexmark Z611 printer to work.  I had better include the Lexmark Z611 printer part for others who may be searching for a howto on this particular model.

I do not know personally if the other Z6XX series printers will work.  I fyou have a Z6XX series printer and this howto has helped you, please post your model number.

Thanks.

---

### Post by giddy1945 on 2006-04-15
Hello, and thanks for the HOW TO; however, I just cannot get my printer to respond.  Everything on the screen looks normal.  I have the driver set up.  It just will not print.  Am I not loading the paper correctly?  Too much paper?  I did everything right.  Please help again. Thanks

---

### Post by Sef on 2006-04-15
Giddy, you should start a new thread and state what the make and model of the printer you have.

---

### Post by giddy1945 on 2006-04-16
I should have specified.  It is the Lexmark Z611.  I successfully printed a test page, but the page was not from my computer.  It was a test page I initiated from the printer itself, so I know it is working.  My box is just not comunicating with the printer other than detecting it at printer setup.

---

### Post by zerhacke on 2006-04-16
How is the printer connected?  Is it connected directly to the USB port on the Linux computer, or is it shared over the network via SMB?

---

### Post by giddy1945 on 2006-04-16
It is connected directly via USB.  Thank you.  Any help would be appriciated.  I do not know what the code above is.  Nothing will work.

---

### Post by zerhacke on 2006-04-17
[QUOTE=giddy1945]I successfully printed a test page, but the page was not from my computer.  It was a test page I initiated from the printer itself, so I know it is working.[/QUOTE]
Er, I'm afraid that's not quite possible.  The Z611 does not have a test page functionality other than the operating system issuing it.  Did you mean you printed it from Windows?  Windows has a test page functionality on all printers.  There's no button on the Z611 to print a test page.

---

### Post by giddy1945 on 2006-04-17
Disconnect the power source.  Hold down the power button.  Reconnect the power source.  Release the power button, and there you have it.  Test page.  And no, I have never used Windows at all.  Only Linux.  I will never run windows.  Only linux.  Linux rocks.  I just need to learn how to use it. (only been into computers for five months).  Thanks for the reply.

---

### Post by zerhacke on 2006-05-18
Sorry for dredging up an old thread, but I have some new information.

Since the posting of this Howto, I have finally gotten my wife to accept a dual boot solution for her computer.  We're gradually moving her off Windows day by day.  The SMB shared printer was on her computer, therefore now the printer in question (Lexmark Z611) is on a dual boot setup.

We can print to it in Windows.  However, following this howto to the letter, we cannot print while in Ubuntu, even though the drivers are showing and the printer is setup according to CUPS.

It would seem that my method only works for Lexmark X611 printers shared via SMB on a Windows host.  On a Linux host, it does not function at all, though it will tell you it does.

---

### Post by giddy1945 on 2006-05-18
Thank you .

---

### Post by Balder on 2006-11-24
I have had serious problems getting my Lexmark X1170 to work in Edgy Eft. Following the above Howto made it work right away. Great Howto. Thanks a lot.

---

### Post by netgooroo on 2006-12-18
OK, I've done everything exactly like it says to do on the howto and still I get "job stopped"..  here..  this is it..  Stopped:job-stopped  ](*,) 

If anyone can shed some light on this, I would really appreceate it.   I'm running 6.10 Edgy. 

thanks in advance..

P.S. I got a Lex Z611 as well  ;)

---

### Post by ssavelan on 2006-12-26
Well.... I would like to say, as a fresh green noob,

the install instructions posted on this thread were spot-on for my Lexmark Z600 (direct USB connect)!

one of the smoothest installs I've had short of a video walk-through (those are super sweet).  Brilliant directions.

I had messed with some instructions that were meant generally for debian and was getting close....

     $ tar -xvzf install.tar.gz

The other instructions that I was fiddling with left out this key interlude that seemed crucial to the smooth execution.  I am excited to get one step closer to THE PERFECT CONFIGURATION FOR MY HARDWARE!!8) 

Sorry about that... got a little carried away.

oh... if you could put together the ubuntu-specific directions for getting the ALSA tarballz to configure --with layla24......  the ALSA ./configure looks for the kernel in /sys/linux/ I believe (which I suppose is a common path in which linux kernels are located).  I am such a beginner that I don't know where the kernel is.... where "version.h" is.

But I digress........... should start a new thread or something.

Thanks for the fire instructions!!!!!  One less reason to pop into Winslows:D

---

### Post by ssavelan on 2006-12-26
oh yeah.... BTW, I'm running 6.06-i386.  I've played around with Edgy and the 64-bit versions of 6.06 and 6.10.  After careening out of control with a couple of installs with some wild stabbing at conflicting packages, I have recently installed 6.06-i386 fresh to help me feel more stable and carefull.  

Sure, I still go into the synaptic sometimes.... late at night.... when somethings not working...  grab about 30 packages that I have no business with... but I have it under control...  I can stop whenever I want.


No really, sometimes things work a lot better when you remove a few key packages....

Would any experts concur?

---

### Post by ssavelan on 2006-12-26
Sorry to be a bore; but, I think I found the ubuntu-specific ALSA directions that I've been looking for.

[https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard?highlight=%28ALSA%29](https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard?highlight=%28ALSA%29)

If you have multiple soundcards/pro or quasipro sound and are having problems with drivers/modules/headers/kernels/lins/permissions......

sorry to get so far off topic....... I was just on a bit of a roll.

---

### Post by slew on 2006-12-26
I'm using Ubuntu Edgy and have had absolutly no luck getting the Z611 printer to work using these directions. Does anyone have a link or a how-to on getting this printer to work?
Thanks!

---

### Post by ss0007 on 2006-12-26
hi ,
I am using Lexmark Z603 printer connected to USB port . I dont see anything like "Z600 V 1.0-1 " as you said in the post during the "Step 2: Install Priter driver" dialog . I got two auto-detected printer listed in Step 1 of Add printer wizard  ,in which both are Lexmark . When I tried to give a sample test page , I see the "job-stopped"  instantly in the printer dialog before printing could even start . 

Any solutions ,pls?

---

### Post by netgooroo on 2006-12-30
So, since no one has replied to my post particularly and anyone else's in addition, I'm guessing that if were running 6.10 edgy and the like that we are on our own..  :???: 

Well, anyone who browses this forum and knows of any walk through helps online, please point them out OR if you have had this same problem and found a solution, please post that as well..   

Hoping to see some help..  :-k

---

### Post by decatett on 2007-01-02
i have the smae problem and i resolve with:

¨
Following up on Frostmourne, I suggest these instructions:

Code:

$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the package $ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # put the needed files into a tar file $ tar -xvzf install.tar.gz # extract the tar file $ sudo alien -i z600cups-1.0-1.i386.rpm # install the printer driver $ sudo alien -i z600llpddk-2.0-1.i386.rpm # install misc. printer libraries $ sudo /etc/init.d/cupsys restart # restart the cups daemon $ /usr/lib/cups/backend/z600 # check that the printer backend works (I get no output but it works fine)

Ldconfig is not needed since the drivers were installed through dpkg nor does the printer driver have to be gunzipped.

Go to System - Administration - Printing and choose the printer driver Z600 v1.0-1 under Lexmark (or, if it's not there, go to Install Driver and choose /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz), and enjoy!

For some resaon I have to go through the printer dialogue twice to get the printer to show up but it works nonetheless.
Reply With Quote
¨

from: [http://www.ubuntuforums.org/showthread.php?t=49714&page=19](http://www.ubuntuforums.org/showthread.php?t=49714&page=19)


:D

---

### Post by sully311 on 2007-01-15
fantastic how-to ... very well written. thx to the author:KS :D

---

### Post by ssavelan on 2007-01-22
Seems that every time that I go to install the drivers to my Lexmark z600 printer I come to this page first and spend an hour with these directions before I remember that they do not work and that I need to go to the second or third hits for "ubuntu lexmark z600":( 

Seems that it has worked for some, though.;)

---

### Post by kevanr on 2007-02-13
i have a problem with the alien part. see this:
[http://www.geocities.com/whitehat4u/Screenshot.png](http://www.geocities.com/whitehat4u/Screenshot.png)

---

### Post by Gray Fox on 2007-04-25
> **decatett said:**
> i have the smae problem and i resolve with:

¨
Following up on Frostmourne, I suggest these instructions:

Code:

$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the package $ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # put the needed files into a tar file $ tar -xvzf install.tar.gz # extract the tar file $ sudo alien -i z600cups-1.0-1.i386.rpm # install the printer driver $ sudo alien -i z600llpddk-2.0-1.i386.rpm # install misc. printer libraries $ sudo /etc/init.d/cupsys restart # restart the cups daemon $ /usr/lib/cups/backend/z600 # check that the printer backend works (I get no output but it works fine)

Ldconfig is not needed since the drivers were installed through dpkg nor does the printer driver have to be gunzipped.

Go to System - Administration - Printing and choose the printer driver Z600 v1.0-1 under Lexmark (or, if it's not there, go to Install Driver and choose /usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz), and enjoy!

For some resaon I have to go through the printer dialogue twice to get the printer to show up but it works nonetheless.
Reply With Quote
¨

from: [http://www.ubuntuforums.org/showthread.php?t=49714&page=19](http://www.ubuntuforums.org/showthread.php?t=49714&page=19)


:D

Thank you very much!  I followed all the above steps and the z600 model was still not showing up but now I just printed a successful test page!  Yahoo!

---

### Post by jonick on 2007-04-26
Thanks for all the help, I managed to get everything installed after using the "install driver" option and pointing to the PPD file, I then ran a test print which worked perfectly. However, after that I tried to print a page from my evolution mail client but it failed to print.

I went back into the install printer application and deleted, and re-installed the printer, this time I notice that two printers had been detected, 

one was just called LexmarkZ600, the second was called LexmarkZ600usb#1 (I only have 1 printer connected to my machine)

inturn I selected both printers and installed the drivers as before using the PPD, I can't print a test page on either.

Can you help?

---

### Post by nitewing98 on 2007-04-30
> **zerhacke said:**
> It would seem that my method only works for Lexmark X611 printers shared via SMB on a Windows host.  On a Linux host, it does not function at all, though it will tell you it does.

Not exactly.  I've got a Z611 connected to my Dad's Ubuntu box and am able to print to it from my Mac running OS X (it uses CUPS also).  I have the Ubuntu box running Netatalk (the AppleTalk service).  The only problem I have is that I can't print landscape from the Mac (don't ask me why, I don't know).

However, the CUPS configuration file in Ubuntu is (by default) set to not allow most things.  I found that to get the printing working I had to "gut" the config file (in [http://localhost:631/admin](http://localhost:631/admin)) and have it use what CUPS likes as a default script.  It's different than the one Ubuntu loads.

---

### Post by ffalconi on 2007-07-28
Great ! It's work fine for my z603 with ubuntu 7.10 but only after install libstdc++5 with sudo apt-get install libstdc++5

---

### Post by Sale on 2007-07-28
Ok...The Instructions shown in this thread worked for me on 32bit relieses of Ubuntu...What about 64bit feisty?

after:

```
sudo alien -i z600cups-1.0-1.i386.rpm
```

I keep getting this error message:

```
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
```

Has anyone installed Lexmark z6xx on 64bit Feisty?

---

### Post by theozzlives on 2007-12-14
I followed the how to to the letter! ubuntu 7.10 Gutsy Gibson wont print to my z611 printer

---

### Post by Jored on 2008-02-11
> **zerhacke said:**
> Here is a howto to get a Lexmark Z600 series printer working.

Go to [http://www.autostatic.com/linux/lexmarkz605-suse93.html](http://www.autostatic.com/linux/lexmarkz605-suse93.html) . Download the drivers found at [http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz) . Save this file to disk, preferably in your home folder.  Open a terminal.

In the terminal, type ```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
```

This will extract the file.

In a terminal, type ```
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz

```

This will create a new tar file named install.tar.gz.  In a terminal type ```
tar -xvzf install.tar.gz
```

This will create many files, as it extracts the contents of the install.tar.gz file you just created with tail.  You're interested in the two RPM files.  If you don't have alien installed on your computer, in a terminal type ```
sudo apt-get install alien
```  You will need your Ubuntu install CD for this.

After you have alien installed, you want to issue the following commands.

```
sudo alien filename.rpm
```

Since you have two RPM files you will need to alien twice, once for each RPM file.  Replace filename with the name of the two RPM files.  Do one then the other, do not try to do both at the same time.

Alien creates two DEB files, one for each RPM file.  Install both DEB files by issuing in a terminal ```
sudo dpkg -i filename.deb
```  Do one then the other.  Do not try to do both at the same time.

Once you have dpkg'd both files, the drivers are installed.  There is a little bit more work to do though.

In a terminal, enter ```
sudo ldconfig
```  This will get the system ready for the drivers.

Now, reboot.  If you do not reboot the drivers will not show up on the list of available drivers on the printer installation wizard.  So, reboot.

Once you've rebooted, enter Gnome.  This may work with other window managers, but I have only tested it in Gnome.  Click System - Administration - Printing.  Choose Lexmark for the manufacturer and the Z600 V 1.0-1 will be available.

Happy printing!  By following this tutorial you can also print to SMB shared printers so long as the printer shared is a Lexmark Z600 series.

Although this is an old thread, I just wanted to feed back my experience and thank Zerhacke for an excellent Howto.

I'm running Gutsy 7.10, followed each and every step in the above Howto and my Lexmark Z602 worked perfectly, first time round.

Some learnings to share:

1.- I'm using Xubuntu on a Dell Latitude LS400 (PIII, 256MB, 40GB HDD). If you try to install the printer (after installing the drivers as outlined in the Howto) from Applications-->Settings-->Printing you will be asked for your root password, which most of us don't have and don't want. So, in the terminal, type:

sudo system-config-printer

You the enter your sudo password and the setup screen pops up, from where you follow the steps as described in the Howto, except this time you will not be prompted for a root password.

2.- This printer is not bad for the price. The problem is that ink cartridges dry up very quickly and cost too much. I don't print every day, so I remove the cartridge and cover the inkjets with a piece of cellotape. The downside is that you need to recalibrate it when you next use it, but it is only a 5 minute job that uses very little ink. I have an Epson and same problem. I also have an HP Officejet 4255, whose cartridges just never dry up. In the future I will only buy printers from HP.

---

