---
title: "Trying to install Canon PIXMA MG2520 printer"
date: 2014-02-09
forum: Hardware
---

### Post by Nick_Kirkendall on 2014-02-09
Does anyone know where I can find the drivers to install a Canon PIXMA MG2520 printer?  The description on the Best Buy website said it was compatible with Linux, but the cd-rom that came with the printer only seems to work with Windows.

---

### Post by tomearp on 2014-02-10
The [specification]("http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mg_series/pixma_mg2520?selectedName=Specifications") for the printer on the Canon USA website does not Linux as a compatible operating system.

In the [drivers section of the page]("http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mg_series/pixma_mg2520?selectedName=DriversAndSoftware"), if you select Linux as the operating system there are no download options. There is a message saying: "There is no driver for the OS Version you selected. The driver may be included in your OS or you may not need a driver."

That seems to be a pretty vague "it might work, it might not" sort of message. 

There is a post [here]("http://ubuntuhandbook.org/index.php/2013/07/canon-drivers-for-ubuntu-and-linux-mint/") about Canon drivers in Ubuntu. It does not specifically list your printer, but does list similar model numbers so it might be worth a go.

---

### Post by jose23 on 2014-02-11
I need help with this too. 

I've gone many hours trying to get this to work with strong helpers in #ubuntu, namely, glist16 and jose, who helped tremendously at trying to get this printer to work. I've gone through that resource which tomearp posted and hasn't worked. 

I'm looking at how to develop a ppd, but I'm a noob and have no idea what I'm trying to understand. Is it possible for an experienced to wishfully create this program? A wish that creates a ppd that gets Pixma mg2520 driver in existence and works. 


Thanks

---

### Post by glitsj16 on 2014-02-11
While trying to assist jose23 on #ubuntu (irc.freenode.net) it was discovered that the [PPA offering Canon Printer Drivers]("https://launchpad.net/~michael-gruz/+archive/canon-stable") isn't usable in its present state. It offers cndrvcups-common (Canon Printer Driver Common Modules) but this package is only available for amd64 ubuntu's and has an unsatisfiable dependency against cndrvcups-common-32, which is only available as i386, effectively rendering both as uninstallable on both 32bit and 64bit OS'es.

People looking for a Canon driver for pixma mg2520 are left in the unfortunate situation that neither the manufacturer nor the PPA can offer a solution. I suggest contacting the maintainer of the PPA through its launchpad page to report this: [https://launchpad.net/~michael-gruz/+contactuser](https://launchpad.net/~michael-gruz/+contactuser).

Also try to ask [official Canon email support]("http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mg_series/pixma_mg2520/form_display/support_by_email") which specific other linux driver is available/usable for the pixma mg2520, explaining this unfortunate situation.

Best of luck and as always #ubuntu on irc is there to assist in further attempts to get these machines working.

---

### Post by aikishugyo on 2014-02-12
Gutenprint experimentally supports this printer. You might need to compile from source, or check the printers.xml file in the online CVS browser or the README to see when it was added.
See the gutenprint project website for my details.

---

### Post by jose23 on 2014-02-12
I downloaded [h=3]printer-driver-gutenprint_5.2.8~pre1-0ubuntu2.1_amd64.deb[/h]    from synaptic. connected printer and printed. nothing happen. what do I do?

---

### Post by aikishugyo on 2014-02-13
1. Read up on how to install a printer using CUPS.
2. Find a repository with 5.2.9 (search forums or ask, I do not use Ubuntu currently). You are using a pre-release version which is naturally very buggy (that was the point of the pre-release).
3. Install the printer, using the correct gutenprint driver.
4. Use your browser to print a page, using plain media, resolution modes intended for plain media (read the names, it is clear what modes are for which media), and report back.

---

### Post by jose23 on 2014-02-13
Thanks Aikishugyo, installing 5.2.9 when running make install it returns an install recursive error. should I be worried about that? [http://paste.ubuntu.com/6927384/](http://paste.ubuntu.com/6927384/)



edit1 : Not finding any of the gutenprint 5.2.9 in the step 3.

---

### Post by tomearp on 2014-02-13
Judging by the output in the paste you will need to run
```
sudo make install
```
for it to work successfully

---

### Post by jose23 on 2014-02-13
Thanks tomearp, I still don't see any 5.2.9 drivers in CUPS add printer admin page. only 5.2.8 pre. Even after sudo make install. What's the deal? What do I do?

---

### Post by jose23 on 2014-02-13
Aikishugyo, I don't see mg2520 [http://gimp-print.sourceforge.net/p_Supported_Printers.php](http://gimp-print.sourceforge.net/p_Supported_Printers.php)

How do I make this work?

---

### Post by aikishugyo on 2014-02-14
Hi, you are right, the drivers are in CVS not in 5.2.9. So you will need  to d/l the source and compile it.
Once you have the dependencies it should be quite easy and installs in /usr/local so you do not overwrite your old system stuff (unlike some of the how-tos describe <shudder>).
The compile process has been cleaned up a lot in preparation for 5.2.10 in a month or so, I do not anticipate you will have any trouble.

---

### Post by jose23 on 2014-02-14
Great. 
cvs -d:pserver:anonymous@gimp-print.cvs.sourceforge.net:/cvsroot/gimp-print loginThis doesn't work because it asks for a password and...there is none on the site.


edit1: I grabbed it  from source forge; cd into guten-print/print ; ran sudo ./autogen.sh ; ran sudo make clean ; ran sudo make ; ran sudo make install ; ran sudo make ; and after all that I see no new printers added to the CUPS admin page. T_T This is a frustrating routine. What can I do?

---

### Post by aikishugyo on 2014-02-16
1. Probably you need to look at the output of your logs for these steps, impossible to tell if the PPDs got built and/or installed.
2. Also, you need to restart cups after the installation.
3. As for anonymous CVS login, I think it is on the site how to log in there, possibly your email, or none.
4. pre releae available so you can get the newest package now.

---

### Post by glitsj16 on 2014-02-16
Short overview of the routine to build the gutenprint 5.2.10 driver from source:

1. check for needed/wanted dependencies before building:
     $ sudo apt-get install libgutenprint-dev libgimp2.0-dev libijs-dev libgs-dev foomatic-db-gutenprint

2. configure the source (inside the extracted gutenprint/print dir):
     $ sh ./autogen.sh --disable-test --enable-maintainer-mode --without-doc

3. build the drivers and libraries:
     $ make

4. install (defaults to /usr/local/...):
     $ sudo make install

5. post-install commands:
     $ sudo ldconfig
     $ sudo cups-genppdupdate
     $ sudo service cups restart

6. open CUPS interface at [http://localhost:631](http://localhost:631) and add the pixma mg2520 printer if not already present:
     check settings and do a print test

7. optional: run gimp and check the availability/test of the gutenprint driver

Hope this gets the expected result

---

### Post by jose23 on 2014-02-16
Installed failed

[http://paste.ubuntu.com/6944450/](http://paste.ubuntu.com/6944450/)

---

### Post by Last_Ship on 2014-02-16
> **glitsj16 said:**
> Short overview of the routine to build the gutenprint 5.2.10 driver from source:

1. check for needed/wanted dependencies before building:
     $ sudo apt-get install libgutenprint-dev libgimp2.0-dev libijs-dev libgs-dev foomatic-db-gutenprint

2. configure the source (inside the extracted gutenprint/print dir):
     $ sh ./autogen.sh --disable-test --enable-maintainer-mode --without-doc

3. build the drivers and libraries:
     $ make

4. install (defaults to /usr/local/...):
     $ sudo make install

5. post-install commands:
     $ sudo ldconfig
     $ sudo cups-genppdupdate
     $ sudo service cups restart

6. open CUPS interface at [http://localhost:631](http://localhost:631) and add the pixma mg2520 printer if not already present:
     check settings and do a print test

7. optional: run gimp and check the availability/test of the gutenprint driver

Hope this gets the expected result

Thank you very much for this step-by-step. I got step 1, but where do i need to cd into in order to accomplish step 2? I've locate three different gutenprint folders, none of which have "print" as a directory inside. I apologize as I know this is incredibly basic, but any help would be much appreciated. Thanks.

---

### Post by aikishugyo on 2014-02-16
If you uncompress the downloaded archive it creates a gutenprint-<version> directory. Inside that is the print directory.

---

### Post by glitsj16 on 2014-02-16
A very kind and knowledgeable helper on #ubuntu is preparing gutenprint 5.2.10-pre1 in a PPA. We'll update this thread as soon as the builds are completed. Expected time-frame: 1.5hours.

@matt2422 and everyone who wants to build from the gutenprint 5.2.10-pre1 tarball:

The above instructions assumed that you downloaded the tarball from CVS at [http://gimp-print.cvs.sourceforge.net/viewvc/gimp-print/print/](http://gimp-print.cvs.sourceforge.net/viewvc/gimp-print/print/) .. I forgot to add that, apologies. If you downloaded the .tar.bz2 file located at [http://sourceforge.net/projects/gimp-print/files/gutenprint-5.2/5.2.10-pre1/](http://sourceforge.net/projects/gimp-print/files/gutenprint-5.2/5.2.10-pre1/) the above steps need 1 small change. Autogen has already been done, so step 2. should be ./configure --disable-test --enable-maintainer-mode --without-doc in this case.

Building succeeded on a 13.10 machine but on irc it was discovered that people on 12.04 (and potentially 12.10 and people still on 13.04) are seeing errors pertaining to libusb. So to get around that it is advised to wait untill the PPA build will be available, which shouldn't be long. That ofcourse also has the added benefit of offering a genuine Ubuntu/Debian package instead of doing a rather messy (but functional) 'sudo make install' for files that are inside different packages in the repos, i.e.libgutenprint2 and printer-driver-gutenprint.

Goodluck

---

### Post by Last_Ship on 2014-02-17
Thanks [**[COLOR=#000000]@glitsj16[/COLOR]**]("http://ubuntuforums.org/member.php?u=581318").  After the CVS link you provided, I was able to follow your previous  instructions and get my MG2520 up and running with the gutenprint driver  on 12.04. Much appreciated!

---

### Post by Last_Ship on 2014-02-24
is it possible to get the scan functionality working on the MG2520 with the Gutenprint drivers? Print/Copy works fine, but Simple-Scan, Canon's VueScane (linux version), and a couple other scanning utilities I found in the software center don't recognize the scanner.

---

### Post by aikishugyo on 2014-02-24
No, gutenprint is a inkjet printer driver, not scanner software.
You should make use of the SANE project for that. Report to their mailing list if something does not work, support might be experimental, and if the Ubuntu repos do not have a modern SANE (going by the ancient gutenprint example) you will need to compile it locally, very easy when you read the README.linux file in the source.

---

### Post by Last_Ship on 2014-02-25
I'll try that, thanks.

---

### Post by pdc on 2014-02-28
so you want to use the scanner function on the MG2520 MF device?

Canon supply a programme called ScanGear

you download it from their driver support site: eg Canon Asia

as ubuntu uses debian packages, use the debian package Canon supply

get it from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100551901.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100551901.html)

it comes down as a .tar.gz file

the commands would be

> tar -zxvf scangearmp-mg2500series-2.20-1-deb.tar.gz

> cd scangearmp-mg2500series-2.20-1-deb

> ./install.sh

the install sees if you have 32bit or 64bit debian and installs appropriately

to run scangear, first of all type

> scangearmp

that should get it running for you

[https://www.youtube.com/watch?v=GSU9YuE_36w](https://www.youtube.com/watch?v=GSU9YuE_36w)

this youtube shows you how to create a launcher to save you opening a terminal each time

---

### Post by Last_Ship on 2014-03-01
Thanks alot. I did try scangear originally and it didn't detect the scanner, but whatever version I used was downloaded from Canon's site. Looks like your instructions might be different so I'll give it a try. Thanks!

---

### Post by appkw020646 on 2014-04-16
I'm using the **updated** 14.04 system and got the printer to work through Settings. The driver/s must be there in the system as I managed to print out a test page which said the driver was STP00403.PPD Version 5.2.10-pre2. ( I certainly didn't install any printer drivers.)  So, it prints and if you want to, go to the post by **pdc** in this thread about scanning with this little machine. There are .deb packages that can be downloaded from Canon support and installed via the Software Centre to help in that regard.

---

### Post by pdc on 2014-04-16
thanks appkw020646

....out of curiosity....if you click on this link [http://localhost:631/printers/](http://localhost:631/printers/) it opens up CUPS (printer admin) on your computer; only you can read it

is the gutenprint driver listed? They feel they have a driver now for most of the Canon MG range

I enclose a thumbnail of our cups page: I use the canon driver

---

### Post by appkw020646 on 2014-04-17
[TABLE="class: list"]
[TR]
[TD]Canon MG2500 series
[/TD]
[TD] -System-Product-Name
[/TD]
[TD]Canon MG2500 series - CUPS+Gutenprint v5.2.10-pre2[/TD]
[TD]Idle 

[/TD]
[/TR]
[/TABLE]
Like so, pdc

---

### Post by pdc on 2014-04-18
thanks; so folks have a choice: 

the gutenprint driver;

or the Canon driver [http://support-asia.canon-asia.com/contents/ASIA/EN/0100550201.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100550201.html)  that comes down as [COLOR="#008000"]cnijfilter-mg2500series-4.00-1-deb.tar.gz[/COLOR]

the Canon driver has the [COLOR="#0000FF"]cngpij[/COLOR] monitoring utility that some like to use [http://ubuntuforums.org/showthread.php?t=2216067&highlight=canon](http://ubuntuforums.org/showthread.php?t=2216067&highlight=canon) (the poster couldn't access the utility as he had the gutenprint driver installed; installing the Canon driver gave him [COLOR="#0000FF"]cngpij[/COLOR] utility)

> cngpij -P Canon-MG2520USB would run the utility and one could set up a launcher for it

---

### Post by matiche on 2014-06-20
you good sir are awsome thanks alot couldn't for the life of me find a app that would   make it  possible to  scan now just to test printing

---

### Post by matiche on 2014-06-20
yep normal print job worked

---

### Post by Last_Ship on 2014-08-24
Just wanted to report that the the previously mentioned steps to install the Gutenprint drivers and configure in CUPS work for the printing functions, and installation of Cannon's ScanGear [http://support-asia.canon-asia.com/c...100551901.html]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100551901.html") takes care of the scanner functionality.

I've successfully reproduced these results in 10.10 and 12.04 with my Cannon PIXMA MG2520. 

For my purposes anyway, this issue is solved.

---

### Post by Axis Mann on 2014-09-09
My neighbour brought home one of those MG2520 printers and connected it  but couldn't get it to work.  I was able to add the printer for him  using CUPS.  I first used the Ubuntu Software Center to verify that cups  was already installed (it was).  I then started a brower and typed  [http://localhost:631](http://localhost:631) in the address bar.  When cups displayed, I  selected the add printer option and looked for the canon printer.  I  found an entry for the mg2500 series printer. I was able to print a test  page in colour and also printed a spreadsheet from Libre Office.

---

### Post by Axis Mann on 2014-09-09
> **Axis Mann said:**
> My neighbour brought home one of those MG2520 printers and connected it  but couldn't get it to work.  I was able to add the printer for him  using CUPS.  I first used the Ubuntu Software Center to verify that cups  was already installed (it was).  I then started a brower and typed  [http://localhost:631](http://localhost:631) in the address bar.  When cups displayed, I  selected the add printer option and looked for the canon printer.  I  found an entry for the mg2500 series printer. I was able to print a test  page in colour and also printed a spreadsheet from Libre Office.

By the way, my neighbour is running Ubuntu 12.04 on some kind of gateway computer.

---

