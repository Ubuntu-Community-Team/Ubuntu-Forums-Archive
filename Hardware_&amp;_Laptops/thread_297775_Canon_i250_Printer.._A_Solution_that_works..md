---
title: "Canon i250 Printer.. A Solution that works."
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by clpc on 2006-11-11
I have pieced this together from various sources found in forums and websites and managed to get my Canon i250 printer working.
I hope this helps others that are sick of the frustration of trying to get this printer working in Ubuntu.

I am a newbie to linux and Ubuntu so my terminology may be inaccurate but the following worked for me.

If you are going to be jumping part way into this because you have already done some of it and had no success then I suggest you go and remove your canon i250 printer from the list of printers first...i.e. from the desktop menu go to System>Administration>Printing and remove any printers for the i250 you have probably added while trying to get your printer working. This way you will be working from a fresh start.

Download the following two files and save them somewhere that you will know where they are when done.

[http://download.canon.com.au/bj/i250linux/bjfilteri250-2.3-0.i386.rpm](http://download.canon.com.au/bj/i250linux/bjfilteri250-2.3-0.i386.rpm)

[http://download.canon.com.au/bj/i250linux/bjfiltercups-2.3-0.i386.rpm](http://download.canon.com.au/bj/i250linux/bjfiltercups-2.3-0.i386.rpm)

You will need alien installed, it can be installed from the Synaptic Package Manager.
Then bring up a terminal window and type the following two lines pressing enter after each one.

sudo alien --scripts bjfilteri250-2.3-0.i386.rpm

sudo alien --scripts bjfiltercups-250-2.3-0.i386.rpm

Then in Nautilus (The file manager in Gnome) just double click the bjfilteri250-2.3-0.i386.deb and bjfiltercups-250-2.3-0.i386.deb files, this way they will get loaded into the Gdebi package installer and you just click the install button.

Now restart cups with this line.

sudo /etc/init.d/cupsys restart

Finally, in Ubuntu 6.10 libtiff ver4 and libpng ver3 are installed and if not they can be installed from the synaptic package manager.
The drivers for i250 want libtiff ver3 and libpng ver2 so you need to create a couple of symbolic links from the versions required to the versions you have.
Do that with the following two lines.

sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

sudo ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2

Now go to System>Administration>Printing and add the printer.
On step 2 of the Add Printer section if the i250 driver is not in the list then click the 'Install Driver' button and browse to /usr/share/cups/model/canoni250.ppd file.

Once all is done you should be able to print a test page.... I could and after many hours of mucking around I was pleasently surprised when the printer sprang to life.:)

---

### Post by N3o21 on 2006-11-23
:( 

It doesn't work.
When I try to print Test page nothing happens.

I don't know what to do :( printer is installed, but doesn't work.
Isn't there any other package which you have installed before the printer become work?

(sorry about my english)

---

### Post by davesmith on 2006-11-23
when i run the <sudo alien --scripts bjfilteri250-2.3-0.i386.rpm> command, i get an error message in the terminal 

File "bjfilteri250-2.3-0.i386.rpm" not found.

what am i missing here?  Any help would be appreciated

---

### Post by N3o21 on 2006-11-24
> **davesmith said:**
> when i run the <sudo alien --scripts bjfilteri250-2.3-0.i386.rpm> command, i get an error message in the terminal 

File "bjfilteri250-2.3-0.i386.rpm" not found.

what am i missing here?  Any help would be appreciated

Probably you are running this command in bad directory.

You must just change directory to directory, where you have downloaded rpm files.

For example:
Download rpm files to "~/Downloads/rpm" directory
Run terminal
Enter "cd ~/Downloads/rpm" command
Now you can simply run "sudo alien --scripts bjfilteri250-2.3-0.i386.rpm" and "sudo alien --scripts bjfiltercups-250-2.3-0.i386.rpm" commands.

---

### Post by davesmith on 2006-11-24
Thanks...another very useful bit of terminal information

Well i managed to follow the instructions above, installed the drivers and my canon bjc 250 printer works nicely now, good test page...but a little heavy on the ink!

Marvelous the help one gets on this forum, tnx

---

### Post by N3o21 on 2006-11-24
> **davesmith said:**
> Thanks...another very useful bit of terminal information

Well i managed to follow the instructions above, installed the drivers and my canon bjc 250 printer works nicely now, good test page...but a little heavy on the ink!

Marvelous the help one gets on this forum, tnx

:( my i250 doesn't work under linux :(
****. You just installed this files and added the printer?

Can you tell me something?
If you see the printer prosperites (System-administration-print-i250-prosperites).
In Connection tab, have you got only one i250 or two for select, but selected only one?

---

### Post by davesmith on 2006-11-24
I downloaded the files, converted them from redhat to debian using alien and added the printer as described.  There were two bjc 250 drivers listed. The one with ex at the end worked after i pointed the wizard to the .ppd file.  I knew i had got it right because the wizard said the bjc 260 ex driver was recommended.

At that stage, i looked at <properties> and pointed the wizard to <LPT1#>This connects the printer to the hardware port where the cable to the printer is connected.


Maybe try another port, could be the answer....however my printer works now but it uses a heavy amount of ink, but it does work

---

### Post by N3o21 on 2006-11-25
It's working :D 

But I have to install libtiff, libpng.
See here: [http://www.ubuntuforums.org/showthread.php?t=126063](http://www.ubuntuforums.org/showthread.php?t=126063) (this solution doesn't work, but here is the libraries, which is needed to print)

It's great.

---

### Post by mwob on 2006-11-26
Thanks for the guide.

I followed this through from start to finish, no problems at all. It doesn't work for me though :( When I print nothing happens - I get nothing out. If I look in the print queue the documents are just sitting there stopped. If I start them again they just stop again! 

The only thing I can think of is that when I went to connect the printer from System-Admin, I was presented with 2 "i250" printers. I tried the first one, which didn't work, so tried again with the second one... 

Any ideas?

---

### Post by N3o21 on 2006-11-26
follow this guide: [http://www.ubuntuforums.org/showthread.php?t=126063](http://www.ubuntuforums.org/showthread.php?t=126063)

but don't install canoc-i250.deb. Go only to this step, and now, follow guide which is in first post of this thread.
It works for me (selecting first i250 when adding new printer). But if you power off you printed, you must add it again. The best solution is leave the printer always on.

---

### Post by padre999 on 2006-12-19
> **N3o21 said:**
> It's working :D 

But I have to install libtiff, libpng.

Same for me. Works great, thanks.

---

### Post by Stormx on 2006-12-20
Issues! I can print a test page perfectly, with the CUPS test page or the normal ubuntu one. But I can't print from any apps.

Constantly, the cups error log gives this, over and over again.:

```
E [20/Dec/2006:22:41:34 +0000] cupsdAuthorize: Local authentication certificate not found!
```

Printing a test page works perfectly, but gives these errors:

```
E [20/Dec/2006:22:45:46 +0000] [Job 18] No %%BoundingBox: comment in header!
```

Printing a 1 line text file from gedit gives this:

```
E [20/Dec/2006:22:48:11 +0000] PID 32740 (/usr/lib/cups/filter/pstocanonbj) crashed on signal 11!
```

Now this could be to do with my drivers, I just don't know. if it is, please direct me somewhere else.

Basicly the printer prints nothing on the gedit try. It sits there saying

> Stopped: job-stopped

in the print queue state on state.

Any ideas? :)

---

### Post by Sef on 2006-12-21
Check [Turboprint]("http://www.turboprint.info/").  They have some free drivers for Canon printers.

---

### Post by tanas on 2007-05-31
I managed to install my i250 (after 2 days of effort). I can't tell what made the difference, but I do know that there is something missing in this HOWTO.
The package libpng3 is no longer included in ubuntu 7.04, so you should redirect to the newer one, libpng12 using

 sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.3

---

### Post by M@T3 on 2007-06-06
Hi!

I did everything as you wrote, but no succes. It's weird, cos both packages are installed (bjfiltercups and bjfilteri are indicated on my Synaptic list) and i250 is on the printer list and "Ready". I made the symbolic links without problems as well.

During test page printing the job is visible for a while (looks like printing) but the hardware is not working at all. It's the same with printing in Open Office. 

I'm kinda sad, cos I really like Ubuntu, but after 3 days of suffering I have to say I'm not able to install Canon i250.  And I had no succes in any other kinds of Linux.

I hate it, but must use XP if I wanna print.

---

### Post by hugomeeuwes on 2007-12-22
Here the same.
Managed to get a good test page.
I downloaded libpng2, libtiff3g and xlibs and installed them manually (forced 32bit on AMD 64)
(xlibs kept questioning for a lot of files if I wanted to replace them or use the old one, I kept all the old ones.)
Then installed canon-i250_2.3_i386.deb.
Finally had to do apt-get install -f
This removed xlibs again, but at least the driver was installed.
Test page works, but apps won't print.

---

### Post by hugomeeuwes on 2007-12-22
I got it to work!
Do as I told in my previous post, then add the printer with the newly appeared driver (i250-ver2.3).
Do not use the printer ubuntu has already seen, remove this one and add a new printer.

---

### Post by L_V on 2007-12-22
Each new release is a real nigthmare to reinstall this Canon i250.

Now new problems/conflicts with libglib1.2 I never got before.

I wonder if testing printer compatibility with new linux releases would not be a good idea to avoid regressions.

Forced to keep a XP partition just for printing.

---

### Post by ubunny on 2008-03-10
tried this and the links with no result.

what do I need to do to troubleshoot when I don't have any error messages?  The canon i250 uses a usb port

tried alien with the rpm's
even loaded tiff3 from repositories
nothing

:confused:

---

