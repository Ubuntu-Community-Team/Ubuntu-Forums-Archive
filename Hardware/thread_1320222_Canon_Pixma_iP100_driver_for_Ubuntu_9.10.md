---
title: "Canon Pixma iP100 driver for Ubuntu 9.10"
date: 2009-11-09
forum: Hardware
---

### Post by cellison on 2009-11-09
If you've been having problems trying to get the previous driver for this printer working, that's because the libcupsys2 package has been renamed to libcups2 with the upgrade to 9.10. After hours of struggling and figuring things out, I repackaged both cnijfilter-common and cnijfilter-ip100series to have the dependencies satisfied. 

I've installed them on Kubuntu 9.10 and they're working fine. If you need them, please reply to this post and I'll gladly e-mail them to you. I was looking to start a ppa, but it looks like WAY too much work. I might start one in the future to facilitate the exchange of the packages if many people seem to need them.

UPDATE: The packages are now hosted on mediafire for 9.10

The common package: [http://www.mediafire.com/download.php?reh1jndbjzy]("http://www.mediafire.com/download.php?reh1jndbjzy")

The ip100 package: [http://www.mediafire.com/download.php?yzhi2zjkyje]("http://www.mediafire.com/download.php?yzhi2zjkyje")

For those that are looking for drivers for *ubuntu < 9.10, here's the links:

For the ip100 driver: [http://ftp.akl.lt/baltix-linux/Baltix-Ubuntu-packages/baltix-3.x/Canon-printing+scan/cnijfilter-ip100series_2.90-1_i386.deb]("http://ftp.akl.lt/baltix-linux/Baltix-Ubuntu-packages/baltix-3.x/Canon-printing+scan/cnijfilter-ip100series_2.90-1_i386.deb")

For the common package: [http://ftp.akl.lt/baltix-linux/Baltix-Ubuntu-packages/baltix-3.x/Canon-printing+scan/cnijfilter-common_2.90-1_i386.deb]("http://ftp.akl.lt/baltix-linux/Baltix-Ubuntu-packages/baltix-3.x/Canon-printing+scan/cnijfilter-common_2.90-1_i386.deb")

Install the common package first and then the ip100 driver.

Hope this helps someone! I know this has been a headache and a half for me!

---

### Post by Uncle5ive on 2010-01-17
I did: 

[LIST]
[*]a fresh new load of Ubuntu 9.10;
[*]did the updates;
[*]installed the first file (common);
[*]then the second file (ip100).
[/LIST]
The printer exists in System, Admin, Printers and when I right click to look at the print queue nothing is visible.   
However, when I click on View and tick Show Completed Jobs the several previous printouts appear on the list, but sadly none have printed on the printer.  
When I watch the queue, the print briefly appears and then disappears (on its way to completed jobs, I assume).
  
Please help me to get my little Canon PIXMA iP100 working on Ubuntu 9.10.

---

### Post by Uncle5ive on 2010-01-18
It now works.

I left it a couple of days and during that time some more updates came through, so maybe that had something to do with it, and now it works fine.  

I can't explain it, but can recommend this printer driver to others.

---

### Post by Uncle5ive on 2010-05-23
I have upgraded to Ubuntu 10.04 and request some assistance to get my Canon PIXMA iP100 printer driver working.  Any suggestions?

---

### Post by Uncle5ive on 2010-06-12
May I have some help with this, please?

---

### Post by cellison on 2010-06-20
Terribly sorry it's taken so long to reply. I got a new laptop not too long ago and put Ubuntu 10.04 on it. I hadn't tried to print anything on it yet, but I needed to today and saw that you had posted about having problems. I took the drivers that I posted on Mediafire and installed them and had no problems with that. Then I went into System>Administration>Printing and clicked Server>Settings. Then I clicked "Publish shared printers connected to this system". It didn't work after that, so I rebooted and now it works fine.

Hope this helps and you haven't been struggling to get this working since Jan.

Best

---

### Post by Uncle5ive on 2010-08-27
It now works, thanks for your help.

---

### Post by fullmoonguru on 2010-10-22
Anyone know about installing this printer on 64 bit 10.04?

---

### Post by jpantone on 2010-12-05
Anything re 10.04 and the ip100? tried the referenced .deb files - they installed, but did not print. (Appeared in the queue for < 1sec - then dissapeared with no printout)

Thanks!

---

### Post by fullmoonguru on 2010-12-05
It worked for mine in 32 bit.  I don't remember doing anything special.

---

### Post by fourky on 2011-01-19
hi eveybody !

I have a computer with ubuntu 9.04 and the printer works fine, following the instructions and packages you mentioned, pretty happy about that !

I try now to install the printer on a Dell computer Vostro 3300, pretty new model. ubuntu 10.04 installed on it.
i did install the two packages, and tick the box under the server's options. but the printer appears to be not connected all the time... 
i plug it to the other computer, and it works fine....

Can anybody help me?


thank you by advance !!!

---

### Post by fourky on 2011-01-20
Little update,

I tryed again, with a friend, did a little lsusb, and a dmesg. 
And after checking that everything looked ok, I tryed to print, and it printed by direct.
So now working for me, but I don't know what was the problem...

Thanks for the two pakages !!!!

---

### Post by BobPaulson on 2011-02-16
> **jpantone said:**
> Anything re 10.04 and the ip100? tried the referenced .deb files - they installed, but did not print. (Appeared in the queue for < 1sec - then dissapeared with no printout)

Thanks!

Exactly the same with me with 10.10. Does anyone have any idea about this?

Thanks, Bob

---

### Post by BobPaulson on 2011-02-16
Just to be more clear, I tried everything mentioned in this thread, using Ubuntu 10.10 32-bit:

[LIST]
[*]downloaded the 9.10 drivers mentioned above (thanks for those!)
[*]installed the common package first, then the iP100 driver
[*]under System>Administration>Printing clicked Server>Settings and clicked "Publish shared printers connected to this system"
[*]rebooted and the printer appeared under System>Administration>Printing
[/LIST]
But when I print something, the printer icon appears for a half second in the upper panel and disappears, but nothing prints, nothing shows in the queue.

Ran the Printing>Help>Troubleshoot tool, but after I told it the test page didn't print, it said "sorry, can't help you, submit a bug".

lsusb shows the printer connected.

Any ideas what else I could try?

Thanks, Bob

---

### Post by daisysmith on 2011-05-02
Help me please!!!
I really dont understand any of this stuff.. i have tried downloading the common drivers and even the driver on the canon site for linux but i dont know how to open it and i cant install it with the software center.
i downloaded ubuntu to replace windows because windows crashed and it was a last ditch effort to save my computer, as i dont have the windows cd to reboot it, so i really dont know what i'm doing.
i have a canon ip100 printer but its not listed in the list of printers when i try to install it by plugging my printer in. 
i used a 10.10 cd but it then told me to update it so i think im running a newer version.
thank you xxx

---

### Post by fullmoonguru on 2011-05-02
What is the extension on the file you downloaded?  Let me know & I can probably help you use it.

---

### Post by Steve White on 2011-07-08
Hi y'all!

I just got my iP100, and lost a day or so.

I finally got it going in Ubuntu 9.10, using cellison's repackaged packages, but not without substantial head-scratching and tweaking and other stuff you don't want to know about.

Now it works very nicely indeed.

**The main problem**

On my system, cellison's new packages didn't make some symbolic links.  The symptom is that the command
[INDENT]printuiip100[/INDENT]

fails to find some Canon libraries.

I did this:

```
sudo ln -s /usr/lib/libcnbpcmcm303.so.7.03.1 /usr/lib/libcnbpcmcm303.so
sudo ln -s /usr/lib/libcnbpess303.so.3.1.0 /usr/lib/libcnbpess303.so
sudo ln -s /usr/lib/libcnbpcnclapi303.so.3.3.1 /usr/lib/libcnbpcnclapi303.so
sudo ln -s /usr/lib/libcnbpcnclbjcmd303.so.3.3.0 /usr/lib/libcnbpcnclbjcmd303.so
sudo ln -s /usr/lib/libcnbpcnclui303.so.3.3.1 /usr/lib/libcnbpcnclui303.so
sudo ln -s /usr/lib/libcnbpo303.so.1.0.11 /usr/lib/libcnbpo303.so
```

Then I started from scratch re-starting the printer re-installing it in CUPS.

**Other problems** encountered along the way

1) If it isn't obvious:  I printed using the smaller USB connector, not the normal-sized one with the PictBridge logo.
Then the printer shows up on USB:

[INDENT]lsusb[/INDENT]
[INDENT]...
Bus 001 Device 005: ID 04a9:10b9 Canon, Inc. 
...[/INDENT]

2) In the Gnome Printer application, under Policies, it says
[INDENT]Not published
See server settings[/INDENT]
Enable the 'Publish shared printers connected to this system'
option in the server settings used in the Printing Administration tool

3) Ohboy.  The font FreeMono.ttf has to be in the standard place.
I had removed it, for my own exquisite reasons.
This is an unfortunate dependency of the CUPS package.
If yout experience this, re-install the ttf-freefont package.

4) In /var/log/cups/error_log
[INDENT]E [07/Jul/2011:11:42:36 +0200] [Job 1] Unable to open job control file "/var/spool/cups/c00001" - No such file or directory![/INDENT]
... repeated for each job

Well there were permissions issues.  I'm not sure I understand what was going on, if this is a problem with the printer driver package, or a consequence of not finding the libraries or what.  Anyway it's not happening now.

**Useful in debugging**

1) The FAQ that comes with the Canon driver.

2) /var/log/cups/error_log

I'm writing Canon about all this.  Let's hope they do the right thing!

Cheers, kids!

---

### Post by Steve White on 2011-07-08
I can further report that those instructons work in Ubuntu 10.10 (Maverick).

Unfortunately, I tried them on an AMD running Ubuntu 11.4.  No luck.  Too many libraries not found or of the wrong type.

Again, I'll inform Canon!

---

### Post by Steve White on 2011-07-08
Canon USA's unsurprising, disappointing response to my request for information and for a driver update:

> Canon USA does not support Linux.  Unfortunately we do not have any information on getting the printer to work on this operating system.  
...
Please let us know if we can be of any further assistance with your iP100.

You know, you might almost think... they might get in trouble for assisting their customers with their product.  Hmmmm....

---

### Post by Steve White on 2011-08-24
The above instructions work also on a 32-bit Ubuntu 11.4 system.

This time I didn't experience the file permissions problem... 
no explanation for that.

Further info on configuring CUPS
Ubuntu menu:  System -> Administration -> Printing

Add a new printer
[INDENT]Select Device
Have to wait maybe 15-20 sec for the Bluetooth printer to show up in the list

 In the Printer Properties, the Device URI should apppear like
[INDENT]bluetooth://001BDC0F3D1F[/INDENT][/INDENT]

Make and Model
[INDENT]Sometimes the automatic search doesn't find the right ppd file.

I found a ppd file in /usr/share/ppd/canonip100.ppd
When this is chosen, Printer Properties displays
[INDENT]Canon iP100 series Ver.2.9[/INDENT][/INDENT]

---

