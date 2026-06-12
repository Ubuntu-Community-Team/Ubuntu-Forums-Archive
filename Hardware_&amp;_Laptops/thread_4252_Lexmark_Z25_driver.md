---
title: "Lexmark Z25 driver"
date: 2004-11-13
forum: Hardware &amp; Laptops
---

### Post by digital_k on 2004-11-13
I have only been using Ubuntu for about a week, everything is runny smoothly. However I cannot seem to get my Lexmark Z25 printer to function . When I run the set up, it is detected as Z25-Z35. When I print a test page  , the paper is pulled down into the printer, it pauses, then it spits out a blank page. I checked Lexmark's site, and there are drivers for other versions of Linux, Redhat/Mandrake. Will these work ?
Any help appreciated.

---

### Post by digital_k on 2004-11-13
Hmmmm...No one have any ideas??? ](*,)

---

### Post by digital_k on 2004-11-14
lol...so no one knows how i can get my printer working without replacing it?

---

### Post by az on 2004-11-14
Lexmark offers crappy support to linux users.  For some models (like the higher end ones - which doesn't say much since its a Lexmark) there is an API made available from lexmark for anyone to develop drivers.  


Lexmark does not understand open source.  Too bad.  There are many other printers with top notch linux support.  Keep that in mind next time you buy.  Sorry.

Dont aswer back saying that linux sucks.  Just complain to Lexmark.

---

### Post by digital_k on 2004-11-14
Oh I would never say that Linux sucks, I like too much, especially Ubuntu. Thanks anyway. :)

---

### Post by ljoris on 2004-11-15
[QUOTE=digital_k]Oh I would never say that Linux sucks, I like too much, especially Ubuntu. Thanks anyway. :)[/QUOTE]

Ahum, beeing an ubuntu newbie ... i've had some rough time getting my Lexmark Z52 to work ... until i found out about cups and gimpprint driver ... works flawlessly ... let me know if you require further assistance

---

### Post by Swab on 2004-11-15
I got my Z25 working in Xandros a while back, look at this thread from the Xandros forums.  I suppose it can be applied to Ubuntu.

[http://forums.xandros.com/viewtopic.php?t=2519&postdays=0&postorder=asc&highlight=z25&start=0](http://forums.xandros.com/viewtopic.php?t=2519&postdays=0&postorder=asc&highlight=z25&start=0)

---

### Post by digital_k on 2004-11-18
[QUOTE=ljoris]Ahum, beeing an ubuntu newbie ... i've had some rough time getting my Lexmark Z52 to work ... until i found out about cups and gimpprint driver ... works flawlessly ... let me know if you require further assistance[/QUOTE]



Hi. I sent you a pm and I was hoping to get more info about how you got your printer going.. Thanks..:)

---

### Post by ljoris on 2004-11-22
[QUOTE=digital_k]Hi. I sent you a pm and I was hoping to get more info about how you got your printer going.. Thanks..:)[/QUOTE]

ehrm, sorry for this really late reply, do you still need assistance ?

---

### Post by irnov on 2005-02-06
Ljoris,
how you get the lexmark z52 to work?
could you give me a pointer?

thanks

irnov

---

### Post by noble on 2005-06-12
> OK, this will take some skill on your part, but it can be done.

First, log in as root and download the drivers from

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242)

Make a directory and put the Lexmark driver in it... Let's assume we named it LEX, and that folder is sitting in /root OK? (in all of the commands, you do not type the # key, this is just to signify the prompt)

OK, so we have moved the driver into the folder now, and we will go into the folder by opening a command prompt and typing:

# cd /root/LEX

We will now extract the archive by typing the following command:

# tar -xzvf CJLZ35LE-CUPS-2.0-1.TAR.GZ

This now leaves us with a shell script rpm installer called lexmarkz35-CUPS-2.0-1.gz.sh... not very useful to a Debian distribution like Xandros, so now comes the fun part...We will make another directory now, and extract the files into it...

# mkdir lextemp

# tail -n +143 lexmarkz35-CUPS-2.0-1.gz.sh | gzip -cd | tar xvf - -C lextemp

Now we will enter the lextemp directory and convert the rpm files, since Xandros should not use rpms unless absolutely necessary.

# cd lextemp

# alien -t *.rpm


Next, we will use the tar command to extract the files to their proper place.

# tar -zxf lexmarkz35-CUPS-2.0.tgz -C /

# tar -zxf z35llpddk-2.0.tgz -C /

Now for some editing... type the following commands in the order shown below..

# cd /usr/local/z35llpddk/utility

# ln -s auckUS.lut bnsi1.lut

# cd /usr/lib

# ln -s liblexz35core.so.0.0.0 liblexz35core.so.0

# ln -s liblexz35printer.so.0.0.0 liblexz35printer.so.0

# ln -s liblexz35printjob.so.0.0.0 liblexz35printjob.so.0

Now to test and see if the driver is working...

# /usr/lib/cups/backend/z35

Output should not error out, and give an output similar to this...

direct z35:/dev/usb/lp0 "Lexmark Inkjet color printer" "Lexmark Printer"

OK, if all is well, we allign the print heads by typing;

# /usr/lib/cups/backend/z35 utilities

Now that the heads are aligned, we can select the printer in the control center by following Launch > Control Center. Once in there in the Periphrial devices section there chould be a setting called printers... highlight printers and then go to add >local printer > Lexmark inkjet color printer and now under the model number one should see an entry for Z35 v 2.0-1... Select that, and then do your test page... Congrats, You're finished!

Hopefully Xandros will eventually make a Debian installer for this driver, but until then this works pretty well... Best of Luck, and hope this helps..

the howto worked really find under hoary.
only problem i have is that i am able to print the testpages with the utility software, but when i add the printer via cups to use it with other applications nothing will happen.

perhaps someone can help me

---

### Post by Efwis on 2005-06-15
to get it to work in all applications, i found if you do this additional step it works fine.

under the add printer, choose the z35-v2.0-1, then under driver click on it and choose standard, problem solved.

---

### Post by digital_k on 2006-06-29
Wow, I came across this thread when I was checkin my CP settings. Hard to belive its been almost 2 years since I posted that! Well I did finally get the thing to work, but it never did work properly. My advice is to go with an HP or other Linux friendly manufacturers. :)

---

### Post by mulima on 2006-07-30
worked, great on dapper

---

### Post by taplinb on 2006-08-13
I too would like a fix to this. Short-term, I'll relocate my Canon printer, but it kinda sucks that Lexmark printers work with some distros and not others. I vaguely recall gimp-print drivers working standalone, but of course I want Unbuntu 6.x (Edubuntu really + LTSP) to fly. So, share please... :)

---

### Post by asi1983 on 2006-08-29
> **digital_k said:**
> I have only been using Ubuntu for about a week, everything is runny smoothly. However I cannot seem to get my Lexmark Z25 printer to function . When I run the set up, it is detected as Z25-Z35. When I print a test page  , the paper is pulled down into the printer, it pauses, then it spits out a blank page. I checked Lexmark's site, and there are drivers for other versions of Linux, Redhat/Mandrake. Will these work ?
Any help appreciated.

vcxcvxbsrfgb

---

### Post by 429148 on 2006-08-29
This is from another Thread by user Black Hole Fire.  I'm going to try to see if this works.

HOWTO: Lexmark Printers
Hello everyone. This is a ubuntu-adopted version of the gentoo howto (which I originally wrote) [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Printers that this howto covers (there are many, many others, but these are the printers that have been confirmed to work so far (also note that Dell's printers are merely rebranded Lexmarks):

Quote:
Lexmark 5700 (black & white only)
Lexmark X1100
Lexmark X1110
Lexmark X1130
Lexmark X1140
Lexmark X1150
Lexmark X1180
Lexmark X1185
Lexmark Z513
Lexmark Z515
Lexmark Z715
Lexmark Z55
Lexmark Z615
Lexmark Z705
Lexmark Z605
Lexmark Z600
Lexmark Z25
Dell A920
Z65 (z65 driver)
Lexmark Z33 (z35 driver)
Lexmark Z33 (z35 driver)
With that said, let's get to it!

The driver we'll be using is the z600 one, which can be found here. Even if your printer isn't a z600 this driver works with a LOT of Lexmark's, so try this driver first.

Download the driver, save it to a desktop folder such as `lexmark` (I say _folder_ because extracting the driver is a messy process!).

Obviously, exclude the comments to the right of the hash (#) marks, I include them only to explain the commands.

Code:

$ mkdir lexmark $ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. $ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver. $ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script. $ tar -xvzf install.tar.gz # extract the contents produced by tail $ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz. $ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz. $ sudo tar xvzf z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place $ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place $ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries $ cd /usr/share/cups/model $ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped


The driver is now installed. Restart the cups daemon:
Code:

/etc/rc2.d/S19cupsys restart

Check whether the printer backend works;
Code:

$ cd /usr/lib/cups/backend $ ./z600

The output of the above command should be _similar_ to this:
Quote:
direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer"
If you get no output, mount the usb filesystem.

Add this to your /etc/fstab file:

Code:

usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0


Then just type: sudo mount usbfs. That should fix it.

Now simply set up your printer through the System->Administration->Printing in gnome. Make sure you select the z600 driver, and you're golden.

For KDE users...well, you'll have to use whatever printer dialogue that KDE provides.

There you have it! If you need any help, post to this thread.

---

### Post by KINABOYS on 2006-10-06
yeah can u help set up my lexmark z25 printer please

---

### Post by Efwis on 2007-01-03
> **KINABOYS said:**
> yeah can u help set up my lexmark z25 printer please

KINABOYS, did you ever get your lexmark printer working? If not shoot me a PM I can help ya out.

---

### Post by mattm591 on 2007-06-26
I tried these instructions but can't get my Lexmark Z25 working under Feisty. Anyone got any ideas?

---

### Post by cisoprogressivo on 2007-07-24
> **mattm591 said:**
> I tried these instructions but can't get my Lexmark Z25 working under Feisty. Anyone got any ideas?
same problem.
Nobody can help us?

---

### Post by grobar on 2007-08-04
INSTALLATION IN UBUNTU FEISTY
I just installed z25 so here is how to do it.

1. GO to [http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242&searchLang=en&searchLang=en&os_group=Mandrake](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242&searchLang=en&searchLang=en&os_group=Mandrake)
  OR direct link [http://www.downloaddelivery.com/srfilecache/CJLZ35LE-CUPS-2.0-1.TAR.GZ](http://www.downloaddelivery.com/srfilecache/CJLZ35LE-CUPS-2.0-1.TAR.GZ) (skip step 2 then)
2. Choose CJLZ35LE-CUPS-2.0-1.TAR.GZ and download it
3. Right click on it and chose extract here (you get new dir there called CJLZ35LE-CUPS-2.0-1.TAR.GZ_FILES)
4. go there by Opening terminal(application-->accessories) type "cd /Desktop/CJLZ35LE-CUPS-2.0-1.TAR.GZ_FILES" and then this " mkdir test " (to make dir test which is for later)
5. again in terminal type this "sudo sh lexmarkz35-CUPS-2.0-1.gz.sh" or ""sudo sh lexmarkz35-CUPS-2.0-1.gz.sh -keep"
6. now you have a new directory "installer" in CJLZ35LE-CUPS-2.0-1.TAR.GZ_FILES . Go there and llook for 2 .rmp files. Right click on them and extract them both to "test" dir you made in step 4.
7. Go in upper left corner of ubuntu feisty and chose system---->administration----> printing
8. New printer ---> lexmark z25 then click forward then choose z35 v2.01 driver you just installed and voila !
9. if ubuntu asks where it should look for the driver chose this  /Desktop/CJLZ35LE-CUPS-2.0-1.TAR.GZ_FILES/test/usr/share/cups/model

---

### Post by horned0wl on 2007-08-22
Hello!  :)

This is my maiden flight into the Ubuntu forums, after only 7 months using Linux/Ubuntu, and I'm happy that I can come in under a positive note.

I have a Lexmark z35 printer, and spent a good deal of time and frustration researching how to get it to work under Ubuntu.  Initially, all I could find were z22-z32 drivers, until I found the following link.  After following their instructions, to the letter, my Lexmark z35 sails into the light, having printed a color-band test page, an .odt, an .odx, a .doc and an .xls -- all under Ubuntu 7.04, Feisty Fawn, using OpenOffice 2.0.2.  This driver setup should work well for your z25. (Note: These instructions are much easier to follow than the immediate previous post...)

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z25](http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z25)


Cheers!

---

### Post by horned0wl on 2007-08-22
Still working (see my entry below) after a USB disconnect, a reboot into WinXP, where it also works under its native driver package, and back into Ubuntu.  I'd say their package and scripting are first rate.  Recommend they be placed in FooMatic.

Cheers!  :)

---

### Post by grobar on 2008-05-17
FYI:Strangely enough this doesn't work in ubuntu 8.04...
I'm never gonna buy Lexmark printer again :lolflag:...


> **grobar said:**
> INSTALLATION IN UBUNTU FEISTY
I just installed z25 so here is how to do it.

1. GO to [http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242&searchLang=en&searchLang=en&os_group=Mandrake](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242&searchLang=en&searchLang=en&os_group=Mandrake)
  OR direct link [http://www.downloaddelivery.com/srfilecache/CJLZ35LE-CUPS-2.0-1.TAR.GZ](http://www.downloaddelivery.com/srfilecache/CJLZ35LE-CUPS-2.0-1.TAR.GZ) (skip step 2 then)
2. Choose CJLZ35LE-CUPS-2.0-1.TAR.GZ and download it
3. Right click on it and chose extract here (you get new dir there called CJLZ35LE-CUPS-2.0-1.TAR.GZ_FILES)
4. go there by Opening terminal(application-->accessories) type "cd /Desktop/CJLZ35LE-CUPS-2.0-1.TAR.GZ_FILES" and then this " mkdir test " (to make dir test which is for later)
5. again in terminal type this "sudo sh lexmarkz35-CUPS-2.0-1.gz.sh" or ""sudo sh lexmarkz35-CUPS-2.0-1.gz.sh -keep"
6. now you have a new directory "installer" in CJLZ35LE-CUPS-2.0-1.TAR.GZ_FILES . Go there and llook for 2 .rmp files. Right click on them and extract them both to "test" dir you made in step 4.
7. Go in upper left corner of ubuntu feisty and chose system---->administration----> printing
8. New printer ---> lexmark z25 then click forward then choose z35 v2.01 driver you just installed and voila !
9. if ubuntu asks where it should look for the driver chose this  /Desktop/CJLZ35LE-CUPS-2.0-1.TAR.GZ_FILES/test/usr/share/cups/model

---

