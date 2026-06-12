---
title: "printer install request"
date: 2010-10-29
forum: Hardware
---

### Post by azhermit on 2010-10-29
Before asking my question my hat is way, way off to all Linux contributors. Awesome, absolutely awesome progress/product since I last checked into Linux for desktop use about 2004 !!!

I'm a Linux newbie (2 weeks) and have only used a terminal window in Windows and Mac about 10 times since the Mac 128K.  I not completely sure if this is the right place in the forum to ask my question. So please be gentle and dumb your much appreciated response way down to "Step 1, Step 2", etc.  so I can understand and execute it please.

I'm running a dual boot 32bit and 64bit Ubuntu 10.10 along with Win XP  and 7 respectively on two machines (32 bit XP and 64 bit Win 7 - not that it matters except that my question will involve both 32 and 64 bit distributions of Ubuntu 10.10 for our two laptops). I want to be able to print wirelessly through my DSL modem router on my "all-in-one" Brother MFC-8480DN  laser which works fine with XP and Win 7 after running the install disks included with the machine. But I'd like to completely migrate away from Windows as I am able to learn and do so.

Synaptic Package Manager does not list my "all-in-one" Brother MFC-8480DN. Drats! A newbie's bummer. I tried installing a model # scary-close to mine, but no banana for the monkey.
I tried going to Brother's web site and do, in fact, see a link to drivers for Linux listed. However, I've read on the forums that they are for 32 bit systems (fact or conjecture? Brother says the drivers work for both), and, being a stupid newbie the directions are all Greek to me since there are lots of variables in the directions and FAQ's that I can't figure out. Then I wrote and asked Brother if they had an installer like they did for Windows.
Brother's answer to me was "
We have a Linux printer driver installation utility located at:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090) 


The directions say to enter the URI as part of the installation. I don't seem to be able to find out what that is in forums or search engines.

My request to the Ubuntu update folks:
1) Is it possible that you could please add my printer to the SPM so I could just push the button and install the printer? I know, try not to gag...   or,
2) Could one you kind, forum hand-holding-types please give me a "Step 1, Step 2, etc" without assuming I know anything more than how to open a terminal window? (which should be fairly obvious by now).

I'm sure your very detailed, "start-from-scratch" answer will benefit lots of other "dumb-and-dumber" folks like me.
Thanks so much.

---

### Post by IcarusR on 2010-10-30
> My request to the Ubuntu update folks:
1) Is it possible that you could please add my printer to the SPM so I could just push the button and install the printer? 

If you want that level of hand holding go back to windows !!!

That said...

> The directions say to enter the URI 

Device uri it's IP address.

URI for my printer attached to my server is ipp://aaa.bbb.1.65:631/printers/Stylus-COLOR-600

You should be able to find URI by looking on your windows install.

Once you have installed the two .deb files from the brother site you should be able to go to System > Administration > Printing > Add & Ubuntu should find the printer.

Attached is screen shot with URI examples.[ATTACH]173957[/ATTACH]

---

### Post by azhermit on 2010-10-31
> You should be able to find URI by looking on your windows install.Brother tech rep says
 > Brother MFC-8480DN does not look for a URI in Win 7. Therefore it will not be on an install log. Contact Linux rep. 

Would it exist if Brother does not use it? OR Is there a way to find it in my distro of Linux (Ubuntu 10.10)?

---

### Post by IcarusR on 2010-10-31
Go to this page & download the two .deb files for your printer & install them by double clicking on them. This will launch gdebi, which will tell you of any missing dependencies which you will have to install.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN")

Then go to System > Admin > Printing > Add & see if it finds your printer.

---

### Post by azhermit on 2010-10-31
Ubuntu Software Center says:

Wrong archetecture 'i386'

I have a 64 bit system.

---

### Post by azhermit on 2010-11-01
> Go to this page & download the two .deb files for your printer &  install them by double clicking on them. This will launch gdebi, which  will tell you of any missing dependencies which you will have to  install.
[http://welcome.solutions.brother.com...html#HL-3040CN]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN")
Then go to System > Admin > Printing > Add & see if it finds your printer.

It  found my printer before ANY drivers had been installed, and before I  started this thread. But it would not print and no drivers were  available in the SPM. I did not know which types of files from the above  mentioned page (I already knew about) were the proper ones to install.  Thanks Icarus for pointing me to the .deb files. But...

Since  these drivers did not work for my 64 bit system (despite Brother saying  they were compatible with either architecture) I went to a 32 bit XP  machine of mine. I tried to use the so-called "installer" Brother  provided at  [FAQ-installer tool]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090")  > "I'm finding it difficult to install my printer driver." which did  not work. The "installer" just yielded a page of code in text form no  matter how I tried to download it (which I later tried entering manually  into a terminal window -- which also did not make the printer print).

So  I tried the above quoted method from Icarus on the 32 bit machine. The  LPD  .deb file from the Brother downloads page downloaded fine. The  cupswraper .deb file would not. The Ubuntu Software Center tried to  download it, but after the progress bar finished the system paused and  returned to an active "install" button - more than once. So I tried  something different.  From  System>Admin>Printing>Server  tab>New>Printer>Network Printer>Find Printer I noticed some  time ago (before attempting to install any drivers) that my printer  showed up, but would not print (as I said above). I clicked on the  printer and waited until recognized and listed in the "Host" box as  BRN001BA954790A and in the Queue box as BINARY_P1

Clicking on the  "Forward" button  comes to "Searching fo drivers" box for the correct  printer. Not finding them brings me to "Choose Driver" box with 3  selections. "Select printer from database" and "search for a printer  driver to download does not work" (can't find the right printer or  drivers) so I tried downloading the PPD file listed on the same Brother  page as the .deb files. It downloaded and installed fine - but still  nothing will print.

Thats when I went to the terminal and tried  entering the code from the "installer." (just the code,not the junk  before it).That also did not make it print. Test page just sits in  queue. Troubleshooter's suggestions (Printing-localhost>Printer  tab>Properties>Settings or Policies/Enabled also did not make it  print.

I'm stumped - but have learned a lot of ways to make it  NOT work. Yes printing still works from Windows over the wireless  network, so printer is ON and woking. I don't know if that means  Brother's drivers are out of date or broken (I notice there is nothing  later than Ubuntu 8.something  listed in their FAQ's and special  instructions. I continued anyway because usually developers design  backwards compatible later versions.  I also noticed that Brother's 64  bit instructions mention only AMD64. Mine is Intel.

[COLOR=Red]Don't  know where to go from here. Does anyone? Has anyone ever installed this  printer (MFC-8480DN) on Ubuntu10.10 - or any Brother laser networked  printer?[/COLOR] ((The drivers for the MFC8440 (which I thought might be close enough to at least print) do not seem to work either.))

[COLOR=Red]If forums go unanswered how about one of you mods passing this along to the developers to see if they have an answer.[/COLOR]  I'm sure they've gone through this with other Brother products - or  perhaps there is a bug in Ubuntu 10.10 that is keeping networked  printers from working, even while being able to recognize them on the  network. I say this because of the failure of the Software Center to be  able to download the .deb cuppswrapper file.

Would appreciate anyone's knowledge - and thanks Icarus for you response so far.

---

### Post by IcarusR on 2010-11-01
Try installing the .deb files manually using the 'force-architecture' option. Has been done before & works.

```
dpkg -i --force-architecture /path/to/the.deb
```

May need to run as sudo, not sure.

---

### Post by azhermit on 2010-11-01
terminal returns:
dpkg: need an action option

---

### Post by IcarusR on 2010-11-04
Sorry my fault command was in wrong order try this...

```
dpkg --force-architecture -i /path/to/the.deb
```

To see command options, syntax etc look at the manual..

```
man dpkg
```

---

### Post by azhermit on 2010-11-07
I managed to get the cupswrapper drivers installed with the package  installer. While trying to install the printer it then appeared  by Model # in the list of printers in "Find Driver" > Brother.  However, after installing it still nothing will print. Going into the CUPS interface I get a message that it can not find the printer. See attached screen shots.

Any ideas?

---

### Post by efflandt on 2010-11-07
If the Brother has an LCD display you should be able to find out its IP address from there, or print its config page from the printer itself, which should be able to tell you that.

You do not really need a .deb package or script if there is a proper .ppd file available (which there appears to be on that Brother link).  Earlier (9.04) the installer script for my Lexmark color laser did not work (possibly because I did not know to use **sudo** then).  But all I had to do after I gave New Printer the IP address and it was looking for a driver, was point to the .ppd file and pick the correct version of the printer from that.  More recent Ubuntu versions now automatically find a driver for my printer.

I think a ppd file is like an ini file for cups (config info or table of printer commands), so I don't think 32 or 64-bit matters for that unless the printer requires an actual driver.  But maybe mine worked 32 or 64-bit because it understands postscript or standard HP PCL, and there are already common drivers for those.

PS: If the driver actually got installed, try reconfiguring it to use **lpd://IP_address/BINARY_P1**, because maybe your system cannot find its netbios name.  I had to do that when wireless on my DSL wireless/modem/router crapped out and my wired printer is now on the WAN side of a 2nd wireless router, although, I use **socket://IP_address:9100** which is a JetDirect thing that most print servers can also do.

---

### Post by azhermit on 2010-11-17
> If the Brother has an LCD display you should be able to find out its IP  address from there, or print its config page from the printer itself,  which should be able to tell you that.
> 
 If the driver actually got installed, try reconfiguring it to use **lpd://IP_address/BINARY_P1**,



Between these two tips and Icarus's "force archecture" commands and some help from a local friend I finally have a working printer for both the 32 bit and 64 bit machines.

Thanks much!!!

---

