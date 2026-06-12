---
title: "[SOLVED] Lexmark Driver Insanity"
date: 2008-04-28
forum: Hardware
---

### Post by Neo Adventist on 2008-04-28
Hello, everyone.  I really love my brand-new Hardy Heron install, but I'm having problems with my Lexmark z715, and it's driving me nuts.  Yes, I know this is not Ubuntu's fault.  I'm blaming Lexmark's near-nonexistant support of Linux systems.  I am a total noob at Linux/Ubuntu, but I can follow directions, so installing the z600 driver from Lexmark's website was fairly painless. 

Here's what I did in the command terminal:

> 
superuser@linuxAMD64-desktopPC:~$** mkdir lexmark**
superuser@linuxAMD64-desktopPC:~$ **mv /home/superuser/Desktop/CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark**
superuser@linuxAMD64-desktopPC:~$** tar -xvzf /home/superuser/lexmark/CJLZ600LE-CUPS-1.0-1.TAR.gz**
COPYING
README
z600cups-1.0-1.gz.sh
superuser@linuxAMD64-desktopPC:~$ **tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz**
superuser@linuxAMD64-desktopPC:~$ **tar -xvzf install.tar.gz**
globals.tcl
install
lexinstall
lexinstall.tcl
license
setup.tcl
testpage
usb.tcl
xlexinstall
xlexinstall.tcl
z600cups-1.0-1.i386.rpm
z600llpddk-2.0-1.i386.rpm
superuser@linuxAMD64-desktopPC:~$ **sudo alien -t z600cups-1.0-1.i386.rpm**
[sudo] password for superuser: 
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
z600cups-1.0.tgz generated
superuser@linuxAMD64-desktopPC:~$ **sudo alien -t z600llpddk-2.0-1.i386.rpm**
Warning: Skipping conversion of scripts in package z600llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
z600llpddk-2.0.tgz generated
superuser@linuxAMD64-desktopPC:~$ **sudo tar xvzf z600llpddk-2.0.tgz -C /**
./
./usr/
./usr/lib/
./usr/lib/liblexprinter.a
./usr/lib/liblexprintjob.la
./usr/lib/liblexz600core.a
./usr/lib/liblexprinter.la
./usr/lib/liblexprintjob.so.0.0.0
./usr/lib/liblexprintjob.a
./usr/lib/liblexz600core.la
./usr/lib/liblexprinter.so.0.0.0
./usr/lib/liblexz600core.so.0.0.0
./usr/include/
./usr/include/lexmark/
./usr/include/lexmark/alignmentdata.h
./usr/include/lexmark/portmonitor.h
./usr/include/lexmark/cartridgeuserinterface.h
./usr/include/lexmark/clock.h
./usr/include/lexmark/cleaningdata.h
./usr/include/lexmark/mediamanager.h
./usr/include/lexmark/printjobmanager.h
./usr/include/lexmark/linuxinkjetprinter.h
./usr/include/lexmark/errorcommunicator.h
./usr/include/lexmark/printerdevice.h
./usr/include/lexmark/cartridgemanager.h
./usr/local/
./usr/local/z600llpddk/
./usr/local/z600llpddk/utility/
./usr/local/z600llpddk/utility/lxbccln.out
./usr/local/z600llpddk/utility/bnsi2.lut
./usr/local/z600llpddk/utility/lxbcalgn.out
./usr/local/z600llpddk/utility/bnsi1.lut
./usr/local/z600llpddk/utility/bnsi3.lut
superuser@linuxAMD64-desktopPC:~$ **sudo tar xvzf z600cups-1.0.tgz -C /**
./
./usr/
./usr/share/
./usr/share/cups/
./usr/share/cups/model/
./usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz
./usr/lib/
./usr/lib/cups/
./usr/lib/cups/filter/
./usr/lib/cups/filter/rastertoz600
./usr/lib/cups/backend/
./usr/lib/cups/backend/z600
superuser@linuxAMD64-desktopPC:~$ **sudo ldconfig**


In "System--->Administration--->Printing" my printer was automatically detected, and I changed the driver from "generic text printer" to the newly-installed "Lexmark Z600 v1.0-1" driver.

So...I clicked on "Print Test Page"...it started printing... and it made an absolute mess.  The Ubuntu logo was superimposed over the word "Ubuntu", and the test fields were all scrambled up, and were literally falling off the left edge of the page.

I really can't think of what to do. And the z600 driver seems to be the only "official" Lexmark driver in existence, though it *supposedly* works with z715 printers.

Any help will be joyously appreciated.

---

### Post by Neo Adventist on 2008-04-29
*bump*

---

### Post by Neo Adventist on 2008-04-30
I realized I needed to download and install "libstdc++5", so I did, but the z600 driver still refused to work. So, I downloaded the z700 drivers I recently discovered from [http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/) and performed this in the command terminal:

> 
superuser@linuxAMD64-desktopPC:~$ **cd /home/superuser/Z700**
superuser@linuxAMD64-desktopPC:~/Z700$ **sudo alien -t z700llpddk-2.0-1.i386.rpm**
Warning: Skipping conversion of scripts in package z700llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
z700llpddk-2.0.tgz generated
superuser@linuxAMD64-desktopPC:~/Z700$ **sudo alien -t lexmark-z700-cups-driver-1.1.1-1.i586.rpm**
Warning: Skipping conversion of scripts in package lexmark-z700-cups-driver: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
lexmark-z700-cups-driver-1.1.1.tgz generated
superuser@linuxAMD64-desktopPC:~/Z700$ **sudo tar xvzf  z700llpddk-2.0.tgz -C /**
./
./usr/
./usr/lib/
./usr/lib/liblexprinter.a
./usr/lib/liblexz700core.a
./usr/lib/liblexz700core.la
./usr/lib/liblexprintjob.la
./usr/lib/liblexprinter.la
./usr/lib/liblexprintjob.so.0.0.0
./usr/lib/liblexprintjob.a
./usr/lib/liblexz700core.so.0.0.0
./usr/lib/liblexprinter.so.0.0.0
./usr/include/
./usr/include/lexmark/
./usr/include/lexmark/alignmentdata.h
./usr/include/lexmark/portmonitor.h
./usr/include/lexmark/cartridgeuserinterface.h
./usr/include/lexmark/clock.h
./usr/include/lexmark/cleaningdata.h
./usr/include/lexmark/mediamanager.h
./usr/include/lexmark/printjobmanager.h
./usr/include/lexmark/linuxinkjetprinter.h
./usr/include/lexmark/errorcommunicator.h
./usr/include/lexmark/printerdevice.h
./usr/include/lexmark/cartridgemanager.h
./usr/local/
./usr/local/z700llpddk/
./usr/local/z700llpddk/utility/
./usr/local/z700llpddk/utility/brch2.lut
./usr/local/z700llpddk/utility/brch3.lut
./usr/local/z700llpddk/utility/lxblcln4.out
./usr/local/z700llpddk/utility/brch1.lut
./usr/local/z700llpddk/utility/lxblaual.out
./usr/local/z700llpddk/utility/lxblalg4.out
superuser@linuxAMD64-desktopPC:~/Z700$ **sudo tar xvzf lexmark-z700-cups-driver-1.1.1.tgz -C /**
./
./usr/
./usr/share/
./usr/share/cups/
./usr/share/cups/model/
./usr/share/cups/model/Lexmark-Z700-lxz700cje-cups.ppd.gz
./usr/lib/
./usr/lib/cups/
./usr/lib/cups/filter/
./usr/lib/cups/filter/rastertoz700
./usr/lib/cups/backend/
./usr/lib/cups/backend/z700
./usr/local/
./usr/local/z700cups/
./usr/local/z700cups/system/
./usr/local/z700cups/system/7b.ps
./usr/local/z700cups/system/Lexmark-Z700-lxz700cje-cups.ppd.gz
./usr/local/z700cups/bin/
./usr/local/z700cups/bin/rastertoz700
./usr/local/z700cups/bin/z700
superuser@linuxAMD64-desktopPC:~/Z700$ **sudo ldconfig**
superuser@linuxAMD64-desktopPC:~/Z700$ **cd /usr/share/cups/model**
superuser@linuxAMD64-desktopPC:/usr/share/cups/model$ **sudo gunzip Lexmark-Z700-lxz700cje-cups.ppd.gz**
superuser@linuxAMD64-desktopPC:/usr/share/cups/model$ **sudo /etc/init.d/cupsys restart**
 * Restarting Common Unix Printing System: cupsd                                                                                                      [ OK ] 


Under "System--->Administration--->Printing", I selected "New Printer", selected the "lexmark z700-p700 series printer USB 1", and selected the z700 driver. 

IT WORKS NOW !! YAY!

---

### Post by Neo Adventist on 2008-05-01
It seems my Lexmark z715 is working as well as it should be, with the exception that it has trouble printing in "landscape" mode.  All else seems normal.

Solved by MYSELF !!   :lolflag:


...and a hearty "Your Welcome" to **rotarychainsaw** for the thank-you note.   XD


EDIT:  Ummm....how do I mark as "solved"?

---

### Post by Umenzi on 2008-08-08
It appears that I am in the same boat you were in a few months ago, trying to get a Z715 to print. I followed the instructions and commands only from your post that solved the problem for you, not any of the ones before it. 

Now I have installed libstdc++5 (from [here]("http://packages.debian.org/stable/base/libstdc++5")), and the printer is responding. Hooray!
 However, I printed the test page only to find that there is a small mechanical problem with the feed and that I am out of ink :(. Grrrr. I did manage to print half of one openoffice doc, but the top margin wasn't there.
Your help has been invaluable, but now I have a host of other problems to deal with.:mad:

---

### Post by Neo Adventist on 2008-08-08
Hello!  Welcome to the Ubuntu forums, Umenzi.  I'm thrilled that my own personal triumph over the Lexmark Z715 have helped you!  :biggrin:

------------------------------------

For all Lexmark Z715 users out there, here is a general guide to conquering your printer troubles on Ubuntu 8.04 Hardy Heron, whether 32-bit or 64-bit:

**STEP ONE:**
Please use Synaptic or apt-get to install both "Alien" and "Libstdc++5" on your Ubuntu machine.  Lack either of these, and your attempts to install your printer will fail.

**STEP TWO:**
Go to [http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/) and download *both* binary drivers for Z700 printers.  They should near the top of the page.  Save them to your Home folder.  

**STEP THREE**
In your Home folder, create a new folder to store your new drivers. For example, I named it "Z700". Move the two binary drivers into "Z700"

**STEP FOUR:**
These next steps will all be in the command terminal.  Open the command terminal and type:

```
**cd /home/<yourusername>/Z700**
```

This should ensure any extracted files don't go all over the place and make a complete mess. Replace <yourusername> with your *actual* user name. (duh)

```
**sudo alien -t z700llpddk-2.0-1.i386.rpm**
```

Enter your user password.  This will transform the binary from a RedHat package to a Debian package.  Ignore the warnings it gives you.

```
**sudo alien -t lexmark-z700-cups-driver-1.1.1-1.i586.rpm**
```

Again, ignore the warnings; they're meaningless.

```
[B]sudo tar xvzf z700llpddk-2.0.tgz -C /
sudo tar xvzf lexmark-z700-cups-driver-1.1.1.tgz -C /[/B]
```

These commands extract the necessary files so Ubuntu can talk to your printer. Don't forget the slash marks!

```
**sudo ldconfig**
```

Essential step:  ldconfig "activates" these files!

```
[B]cd /usr/share/cups/model
sudo gunzip Lexmark-Z700-lxz700cje-cups.ppd.gz[/B]
```

This file is still "zipped" and should be "unzipped"

```
**sudo /etc/init.d/cupsys restart**
```

This will restart the Common Unix Printing System, or CUPS for short.

**STEP FIVE:**
If you wish, copy-and-paste everything in your command terminal to "Text Editor" or "Open Office" and save it for future review.  Close the terminal.

Under "System---> Administration---> Printing", select NEW PRINTER.

Select "lexmark z700-p700 series printer USB 1" and then select the Z700 driver.

Print Test Page

--------------------------------------

Your Lexmark z715 printer should now work.  

Be forewarned, however, that your printer *may* have issues printing in "landscape" mode, and beware that your printer *may* have issues with the application-defined top margin. 

HAPPY PRINTING!!!  :biggrin:

---

### Post by N00bB00b on 2008-08-26
Crap.  Total N00b here trying to get this done.  I'm having trouble with using Synaptic to download the Libstdc++5 package.  I'm getting an error:

[I]libstdc++5:

Package libstdc++5 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list[/I]

Alien is ok, but do I need version 5 of the C++ compiler or can I use some other version?  Others have mentioned that 6 doesn't cut it.

---

### Post by coffeecat on 2008-08-26
> **N00bB00b said:**
> [I]libstdc++5:

Package libstdc++5 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list[/I]

Curious. Have a look at my Synaptic screenshot (Ubuntu 8.04). Which version of Ubuntu are you running, by the way?

I don't remember installing libstdc itself. I think it came in with the package 'build-essential'. Try installing build-essential and see if that brings it in.

---

### Post by N00bB00b on 2008-08-27
I'm also in 8.0.4.  I'll try this later.

---

### Post by matildamd on 2008-10-07
> **Neo Adventist said:**
> Hello!  Welcome to the Ubuntu forums, Umenzi.  I'm thrilled that my own personal triumph over the Lexmark Z715 have helped you!  :biggrin:

------------------------------------

For all Lexmark Z715 users out there, here is a general guide to conquering your printer troubles on Ubuntu 8.04 Hardy Heron, whether 32-bit or 64-bit:

**STEP ONE:**
Please use Synaptic or apt-get to install both "Alien" and "Libstdc++5" on your Ubuntu machine.  Lack either of these, and your attempts to install your printer will fail.

**STEP TWO:**
Go to [http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/) and download *both* binary drivers for Z700 printers.  They should near the top of the page.  Save them to your Home folder.  

**STEP THREE**
In your Home folder, create a new folder to store your new drivers. For example, I named it "Z700". Move the two binary drivers into "Z700"

**STEP FOUR:**
These next steps will all be in the command terminal.  Open the command terminal and type:

```
**cd /home/<yourusername>/Z700**
```

This should ensure any extracted files don't go all over the place and make a complete mess. Replace <yourusername> with your *actual* user name. (duh)

```
**sudo alien -t z700llpddk-2.0-1.i386.rpm**
```

Enter your user password.  This will transform the binary from a RedHat package to a Debian package.  Ignore the warnings it gives you.

```
**sudo alien -t lexmark-z700-cups-driver-1.1.1-1.i586.rpm**
```

Again, ignore the warnings; they're meaningless.

```
[B]sudo tar xvzf z700llpddk-2.0.tgz -C /
sudo tar xvzf lexmark-z700-cups-driver-1.1.1.tgz -C /[/B]
```

These commands extract the necessary files so Ubuntu can talk to your printer. Don't forget the slash marks!

```
**sudo ldconfig**
```

Essential step:  ldconfig "activates" these files!

```
[B]cd /usr/share/cups/model
sudo gunzip Lexmark-Z700-lxz700cje-cups.ppd.gz[/B]
```

This file is still "zipped" and should be "unzipped"

```
**sudo /etc/init.d/cupsys restart**
```

This will restart the Common Unix Printing System, or CUPS for short.

**STEP FIVE:**
If you wish, copy-and-paste everything in your command terminal to "Text Editor" or "Open Office" and save it for future review.  Close the terminal.

Under "System---> Administration---> Printing", select NEW PRINTER.

Select "lexmark z700-p700 series printer USB 1" and then select the Z700 driver.

Print Test Page

--------------------------------------

Your Lexmark z715 printer should now work.  

Be forewarned, however, that your printer *may* have issues printing in "landscape" mode, and beware that your printer *may* have issues with the application-defined top margin. 

HAPPY PRINTING!!!  :biggrin:
I have followed all of your steps, but my printer will not work. I have actually done it at least three times. I am learning as I go...this is my first use of any linux system. Beginning with the step sudo ldconfig the terminal states that it is not found in archive, so when writing in the next two lines the terminal states that there are no such files. help?

---

### Post by Neo Adventist on 2008-10-19
Welcome to the Ubuntu forums, Maltidamd  :)

I will try to help you as best I can.  However, I'm rather puzzled that ldconfig did not work.  Are you using Ubuntu 8.04?  Any additional details would be helpful.

---

### Post by Xcerca on 2008-11-16
I think I'm close to something: 
I installed the z600 driver first, and it worked, but the left margin was wrong, going right off the edge of the page. 

So then I installed the z700 driver, and it worked, but the top margin was right at the very top of the page.

so i just used the .pdd files to see what was going on, and when i switch the .pdd file from the z600 to the z700 i still get the same problem.

z600: top margin good, left margin bad
z700: top margin bad,  left/ right margin's bad

so I looked at the z600.pdd and z700.pdd side by side to see if there was something in either one of them that i could copy to the other to make all of the margin's good.

this is what i found:

the two files are almost identical except for these lines (excluding the names and titles that say z700 and z600)

[SIZE="3"]z600.pdd[/SIZE]:
*PageSize L/L: "<</PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageSize 2L/2L: "<</PageSize[360 505]/ImagingBBox null>>setpagedevice"

*PageRegion L/L: "<</PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageRegion 2L/2L: "<</PageSize[360 505]/ImagingBBox null>>setpagedevice"

*ImageableArea L/L: "18 36 234 355"
*ImageableArea 2L/2L: "18 36 342 500"

*PaperDimension L/L: "252 360"
*PaperDimension 2L/2L: "360 505"

*%MediaType Automatic/Media Sense: "<</cupsMediaType 6>>setpagedevice"

*PrintQuality Best/Best (2400 dpi): "<</HWResolution[600 600]/cupsCompression 3>>setpagedevice"

[SIZE="3"]z700.pdd:[/SIZE]
*%PageSize L/L: "<</PageSize[252 360]/ImagingBBox null>>setpagedevice"
*%PageSize 2L/2L: "<</PageSize[360 505]/ImagingBBox null>>setpagedevice"

*%PageRegion L/L: "<</PageSize[252 360]/ImagingBBox null>>setpagedevice"
*%PageRegion 2L/2L: "<</PageSize[360 505]/ImagingBBox null>>setpagedevice"

*%ImageableArea L/L: "18 36 234 355"
*%ImageableArea 2L/2L: "18 36 342 500"

*%PaperDimension L/L: "252 360"
*%PaperDimension 2L/2L: "360 505"

*MediaType Automatic/Media Sense: "<</cupsMediaType 6>>setpagedevice"

*PrintQuality Best/Best (4800 dpi): "<</HWResolution[1200 1200]/cupsCompression 3>>setpagedevice"

so as you can see the only difference is that some lines have a % sign and the print quality line, so if i knew which lines to take the % signed off of in the z700.pdd then maybe that would change the top margin (which works fine the file with no % sign)

I'm not incredibly familiar with unix so I'm not sure if the % sign has any special meaning but i really think that editing these .pdd files will solve the problems with the margins, then i can post the .pdd with insructions

or i could be way off

---

### Post by Barbalras on 2009-11-19
Did anyone solved the margins' issue?

thanks!

---

