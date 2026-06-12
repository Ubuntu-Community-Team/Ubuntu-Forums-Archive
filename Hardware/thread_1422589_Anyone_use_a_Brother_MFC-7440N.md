---
title: "Anyone use a Brother MFC-7440N?"
date: 2010-03-05
forum: Hardware
---

### Post by Objekt on 2010-03-05
I need a new printer, and of course it has to work under Ubuntu.

Has anyone used a Brother MFC-7440N under Ubuntu?  It is the leading candidate so far.  Brother provides a Linux driver ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7440N]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7440N")), but I'm wondering whether it's significant that there have been no updates to the Linux driver since June 2008.

I'm a bit nervous about this purchase, because I don't want to get stuck with another piece of junk that will only work under Windows.  I also want to avoid the many shortcomings of the printer being replaced, a Canon Multipass F60.  I have grown very tired of its lack of Linux drivers, constant complaining that the color ink is out, glacially slow USB 1.1 connection, etc.

Feel free to suggest an entirely different brand or model, as well.

---

### Post by roger_1960 on 2010-03-05
Hi

Not the same hardware, but, I have 2 DCP115C's and have followed Brother's instructions and installation notes to the letter (ie use MFC210C drivers and run a couple of commands in Terminal before installation) and it all works!!  I think their site is great , but you must follow their installation instructions and carry out the pre installation requirements.  The instructions for 9.04 worked with 9.10 for me.

I don't know, but would guess that their drivers will work.

---

### Post by demoric on 2010-03-05
I just jumped right in and tried to install my HL-3070CW after a little bit of trial and error I found the correct network settings.  The drivers for USB works flawless, and the network drivers seem fine too.

Brother seems to have good linux drivers.  My guess is that if its not broke don't fix it for the lack of "new" drivers.

P.S.  If you're just looking for a printer I do like the this one.  Its color, wireless, USB or network, supports printing from USB devices (cameras thumbdrives), and it's LED so there's less moving parts.  If you hunt around you can pick them up for less than $300.  I got mine new for $209 shipped.

---

### Post by Objekt on 2010-03-07
Thanks for the input.  I went to buy the printer today, and Costco no longer has it in stock.  Only on the website.  So I have to wait another week for it to be shipped here.  It figures!

Buying a "just a printer" device would be cheaper, but I've become quite attached to the multifunction thing, specifically the scanner.  It's really handy, and the one part of the Multipass F60 I would miss with just a printer.  I don't have room for both, and anyway the Brother can plug directly into the router, rather than requiring a PC to run it.

LED printing technology is interesting, but I'm limiting myself to what's available at Costco because of their superior return & warranty policy.

---

### Post by tcchris on 2010-03-07
Hi , I have the mfc465-cn . Multifunction  network printer/scanner .
As of Karmic , the driver is in the repo's (yeah !!)
So now I just go to cups page to install .
Brother works well with Linux

---

### Post by gordintoronto on 2010-03-07
I have a Brother network laser, and it works great. The only hassle was that Ubuntu wants it to have a static IP address, and the Brother utility to tell the printer to use a static IP address runs under Windows...

---

### Post by Objekt on 2010-03-10
I received my Brother MFC-7440N today and have set it up.  Installing the Linux drivers required a little command-line action, but was not one of the harder things I've done.

This thing is AWESOME!  Brother offers Linux drivers to use all the features: print, scan, and fax, and I can verify that they all work - except fax, only because I don't have another fax machine to fax to.  But I'll probably give faxing a try in the next few days, maybe by faxing myself a test page from work.

I have the MFC-7440N plugged into my router, and I can print to it and scan from it over the network, on both my Ubuntu 9.10 machine and my girlfriend's Windows XP box.  

One thing I didn't notice before I ordered it: this multifunction device will scan to an FTP site.  That could be handy for those of you who run servers at home.  I was just happy that it connects via Ethernet, so I don't have to connect it to a PC to make it accessible over the network.

I'm sure I will be able to access it from the netbooks too, as soon as I put the Brother Linux drivers on those.

In sum, BIG success!

---

### Post by step12dude on 2010-04-17
Objekt - I noticed that you've got your Brother MFC-7440N printer working under Ubuntu 9.10 64-bit.  I've been trying to do the installation according to the Brother instructions and I have not gotten very far.  Perhaps you can help.

I download the drivers, go to the Download directory, become a superuser, and then I try the dpkg -l --force-all (or --force-architecture) command, and I keep getting an error 

        No packages found matching brmfc7440nlpr-2.0.2-1.i386.deb.

Any thoughts or tricks?  Thanks!

I'm running Ubuntu 9.10 64-bit and the MFC-7440N is a network printer.  I can see the printer on the network and I can use it just fine thru a Windows XP guest that's running under VMWare Player.  

Thanks!

---

### Post by Objekt on 2010-04-17
> **step12dude said:**
> Objekt - I noticed that you've got your Brother MFC-7440N printer working under Ubuntu 9.10 64-bit.  I've been trying to do the installation according to the Brother instructions and I have not gotten very far.  Perhaps you can help.

I download the drivers, go to the Download directory, become a superuser, and then I try the dpkg -l --force-all (or --force-architecture) command, and I keep getting an error 

        No packages found matching brmfc7440nlpr-2.0.2-1.**i386**.deb.

Any thoughts or tricks?  Thanks!

I'm running Ubuntu 9.10 **64-bit** and the MFC-7440N is a network printer.  I can see the printer on the network and I can use it just fine thru a Windows XP guest that's running under VMWare Player.  

Thanks!

That's probably the problem right there.  It looks like you are trying to install the 32-bit version of the drivers in a 64-bit OS.  Sometimes you can do that, but I don't think this is one of them.

I do still have all the drivers I downloaded in one folder, so I can confirm which packages are the correct ones.  Unfortunately, I can't always get Ubuntu to boot now (see this thread: [http://ubuntuforums.org/showthread.php?t=1456411]("http://ubuntuforums.org/showthread.php?t=1456411")), so I'm in Windows as I type this & thus the files are temporarily inaccessible.

---

### Post by step12dude on 2010-04-19
Thanks for your reply.  

I understand that I'm trying to install the 32-bit drivers, but when I scour the Bother Linux Solutions documentation regarding 64-bit Linux, that's what it seems to say to do.  I haven't found any 64-bit drivers for the MFC-7440N on Brother's Linux page or anywhere else.  

Below (at the bottom of this post) is the exact text from Brother's FAXs page.  I've done Steps #1 and 2 but when I try installing with dpkg, I get the error message that I mentioned in my earlier post.

Since you appear to have been successful in getting the MFC-7440N to work under 64-bit Ubuntu, I thought you might be able to provide some guidance, particularly if there's another way to get this done or if there are, in fact, 64-bit drivers somewhere that I have not (yet) located.

Thanks...
============
**I'm using a Linux 64 bit edition. Can I use the Brother Linux printer drivers?** 


Yes. Brother printer drivers are created and optimized for 32 bit version of Linux,
 but those can be used for 64 bit Linux also. Some additional steps are required.

**For dpkg users:**
**1.** Install the standard c library for 32bit applications (e.g. lib32stdc++6(Debian) or ia32-libs(Ubuntu))
**2.** Create some folders if it is required
2-1. Create /usr/lib/cups/filter if it does not exist.
**Command1: mkdir /usr/lib/cups**
**Command2: mkdir /usr/lib/cups/filter**

2-2. Create /usr/share/cups/model if it does not exist
**Command: mkdir /usr/share/cups/model**

**3.** Install the drivers using "--force-architecture" or "--force-all"option.

**4.** Copy brlpdwrapperXXX files under /usr/lib/cups/filter/ to /usr/lib64/cups/filter/
**Command: cp /usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter**

**5.** Copy libbrXXXX files under /usr/lib/ to /usr/lib32/ if /usr/lib32 exists.
**Command : cp /usr/lib/libbr* /usr/lib32/**

---

### Post by Objekt on 2010-04-19
Well, that's what I get for going on memory.

Is it only the fax driver you're having trouble with?  Please copy and paste your terminal session from when you try to install the driver, so I can see exactly what's happening.

---

### Post by Objekt on 2010-04-22
Another thought: did you set all the *.deb packages to be executable?

I don't know the console commands, but you could do this:

1) open Nautilus as a superuser
2) browse the the folder where you have all the various Brother .deb packages
3) modify them to be executable (right click on file->Properties->Permissions tab->check "Allow executing file as program").

I'm pretty sure I had to do that before any of the .deb files would install anything.

Also, are you connecting the printer directly to your computer via USB, or are you using it as a network printer?

---

### Post by joshcrack on 2010-10-27
Hey man... I am on 32bit Ubuntu 10.10 and I am having trouble installing my MFC-7440N which is on my network. here is a thread w/ some of the screenshots of what I've been trying to do... 

[http://ubuntuforums.org/showthread.php?t=1606673](http://ubuntuforums.org/showthread.php?t=1606673)

Please tell me how you got yours working. Thank You.

---

### Post by benjaminchoate on 2011-06-02
I'm using Ubuntu 11.04 64-bit and was having trouble using the recommended settings. I found the solution suggested in this link to work quite well.

[http://superuser.com/questions/260652/how-do-i-use-my-brother-mfc-7440n-from-debian-or-ubuntu](http://superuser.com/questions/260652/how-do-i-use-my-brother-mfc-7440n-from-debian-or-ubuntu)

---

### Post by beermotor on 2011-08-15
> **benjaminchoate said:**
> I'm using Ubuntu 11.04 64-bit and was having trouble using the recommended settings. I found the solution suggested in this link to work quite well.

[http://superuser.com/questions/260652/how-do-i-use-my-brother-mfc-7440n-from-debian-or-ubuntu](http://superuser.com/questions/260652/how-do-i-use-my-brother-mfc-7440n-from-debian-or-ubuntu)

I'm using a Brother MFC-7460DN that I just got from Newegg, and the instructions at that link allowed me to print. Now trying to get scanning working.

---

