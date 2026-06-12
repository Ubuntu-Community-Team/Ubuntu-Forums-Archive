---
title: "canon ip4700 printer-driver problem on 64bit karmic"
date: 2010-04-12
forum: Hardware
---

### Post by r_avital on 2010-04-12
[FONT=Tahoma]There is a [solved thread]("http://ubuntuforums.org/showthread.php?p=9114934") about this, but it didn't work for me, and I'm posting it here in case no one looks at solved threads, so here goes...[/FONT]

Downloaded a tar.gz from Canon containing two .deb packages:
cnijfilter-common_3.20-1_i386.deb
cnijfilter-ip4700series_3.20-1_i386.deb

Unpacked the archive into a separate folder under my home folder.  In a terminal, I used:

sudo dpkg -i --ignore-architecture <package name>

...which is what** was suggested** in the thread linked above.

This worked through installing the packages (the common package first, then the ip4700 package) with no errors.  However, when I go  to set up the printer (System>Administration>Printing), the ip4700 still does not show up in the list.

What am I missing?

I'm using the print admin tool because the printer is on a network (on a DLINK printer-server).  This very same laptop was printing fine on the same printer, via wi-fi and all, when it was running 32-bit Jaunty.  When I scrubbed it and installed 64-bit Jaunty, I could never make this work any longer (so we know it's not a Karmic problem, but rather a 32bit vs 64bit issue), and **I do have the ia32-libs installed** (if that's relevant).

Any suggestions?

TIA

---

### Post by r_avital on 2010-04-13
Ignore the following and scroll down to the **update** section.

OK, I'll post the solution here for the benefit of anyone else having the same problem, setting up this printer through a network when the printer is on a print-server box (should probably work for any printer, as long as you find your printer's own ppd file).  My thanks to the folks on the other thread, but I found a quicker and simpler and painless way to solve the problem:


[LIST=1]
[*]Download[URL="http://support-th.canon-asia.com/contents/TH/EN/0100236703.html"] IJ_Linux_Printer_Driver_Source_320.tar from the Canon site
[/URL]
[*]Unpack the archive.  There will be a bunch of directories.
[*]Open the ppd directory.  Verify that the file canonip4700.ppd is there.
[*]Go to System>Administration>Printing, and click on the New button.
[*]After it's done looking for printers and finding none, select the network printer option.
[*]Enter the IP address for your printer-server.
[*]After it's done searching for printers again, it will present you with a screen that includes a list of printer manufacturers.  Ignore the list, but above the list there are 3 radio buttons.  Select the option "Provide a ppd file" and navigate to the ppd file in the archive (in the ppd directory) you unpacked in step 2.
[*]Done.  My 64-bit Karmic seems to have generated a driver, because the next screen asked me whether I wanted to print a test page, which I did.
[/LIST]
Sorry again for the double post, and hope this helps somebody.

_**Update**_

OK, ignore the above, I've had to re-do this after Lucid+Grub2 crashed and I re-installed Karmic 64-bit, plus some of the commands and underscore/hyphen above are wrong, so here's a corrected step-by-step. [I] Again, this is for setting up the printer on a network print-server (e.g. Dlink etc).
[/I] 
      1. Download cnijfilter-ip4700series-3.20-1-i386-deb.tar.gz [from this hard-to-find page  on the Canon site.]("http://support-th.canon-asia.com/contents/TH/EN/0100236002.html")
      2. Also downloadcnijfilter-source-3.20-1.tar.gz (source file) [from this page.]("http://support-th.canon-asia.com/contents/TH/EN/0100236703.html")
Extract the *first* archive, *not the source archive*.  It will create a directory named cnijfilter-ip4700series-3.20-1-i386-deb.  *This is a directory, not a package.*  In this directory, you will find the following:
[LIST]
[*]A script named install.sh, ignore it, it will return errors on a 64-bit OS
[*]A directory named "packages."
[/LIST]
      3.  In the packages directory, you will find:

[LIST]
[*]cnijfilter-common_3.20-1_i386.deb
[*] cnijfilter-ip4700series_3.20-1_i386.deb
[/LIST]
           4.  Go to a terminal and install them, [I]in this order:
[/I]```
sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb 
```And then:
```
sudo dpkg -i --force-architecture cnijfilter-ip4700series_3.20-1_i386.deb
```      5.  Open the source archive (in Archive Manager), open the top directory, then open the PPD directory.  From it, extract canonip4700.ppd to a directory of your choide.
            6. Open System->Administration->printing, add a new printer, and when it's done looking for drivers,  select network printer, enter the ip address of your print-server, click on probe.  It will look for printers again, then it should enter "ps" in the queue field.
            7. Click on Forward, and select the "provide a ppd file" option.
            8. You should at this point be prompted to print a test page.

Sorry for the earlier confusion, HTH

---

### Post by marshaller on 2010-05-02
Hi
Have tried your suggestions, but when trying to
sudo dpkg -i --ignore-architecture cnijfilter-common_3.20-1_i386.deb
I got a failure "unknown option" (my best translation from danish) --ignore-architecture.
Have anyone any sugestions?

---

### Post by r_avital on 2010-05-03
> **marshaller said:**
> Hi
Have tried your suggestions, but when trying to
sudo dpkg -i --ignore-architecture cnijfilter-common_3.20-1_i386.deb
I got a failure "unknown option" (my best translation from danish) --ignore-architecture.
Have anyone any sugestions?

Yes, that was my own carelessness, again, darn it.  The correct command syntax is this:

```
sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
```

My apologies.  I will correct it now.  Let me know if this works out for you :)

---

### Post by Merzhin on 2010-05-03
OK,
:D
that workaround matches for me!

Thanks a lot!

---

### Post by r_avital on 2010-10-11
Ouch...

Found another missing detail in my "brilliant" procedure above...

One laptop with Lucid 64 bit, followed the procedure above, ip4700 printer prints nice and pretty.

Another laptop SAME lucid 64 bit, same procedure as above, gives errors.

Until I found out what was missing:

Make sure the following packages are installed:

cups-driver-gutenprint
ghostscript
ghostscript-cups
gsfonts
ijsgutenprint

Some of these may already be installed by default.  What solved the problem for me was the installation of the ghostscript package.

All are from the Lucid repositories

---

