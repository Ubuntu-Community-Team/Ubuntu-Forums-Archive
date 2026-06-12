---
title: "Canon printer not working after 10.04 upgrade!"
date: 2010-05-02
forum: Hardware
---

### Post by QuahogRocks on 2010-05-02
Hello, first timer here.  I just upgraded my ubuntu 9.01 system to 10.04 and I love it, save for one thing; my Canon ip1600 printer, which was a pain in the A to get working on ubuntu, now no longer works with 10.04.....I'm using it running off the ip2200 v.2.60 driver as discussed in this thread [http://ubuntuforums.org/archive/index.php/t-558993.html](http://ubuntuforums.org/archive/index.php/t-558993.html).

My system finds the ip2200 driver just fine after I go through the steps outlined in that thread, and the printer installs etc...  But it will not print to save its life.  It just says "Idle" and the print que icon appears in the top toolbar in ubuntu then disappears in a few seconds and the printer goes on being a 5 pound paper weight.

Is there a compatability issue with the 10.04 update, possibly with Cups?  Please help, this printer has been awesome for all the years I've had it, and ubuntu is way better than windows, but the teeth i have to pull to get this printer working is getting ridiculous!  If I have to downgrade back to 9.01 I guess I'll do that as a last resort, maybe someone could let me know how to do that without losing all my files and having to do a clean install.

So...any ideas?

PS  Thank you so much

---

### Post by QuahogRocks on 2010-05-02
bump

---

### Post by aoc on 2010-05-08
My Pixma ip1500 has stopped working after the 10.04 upgrade as well. It also took a bit of work in 9.10, but I got there eventually.
I also see the printer icon for a second after I send a test page, and the print job number increases, but there is nothing in the print job list. Even the completed jobs list is empty.
Can anyone offer some advice on what to try.

---

### Post by aoc on 2010-05-10
I must say that I am disappointed.
This thread has had over 100 views, so I bet a lot of those have been people with broken printers with this new release, and the thing is, I didn't even search for this release. It just presented itself as the latest stable release, so naturally I expected it to work.

Now I have always thought that the Linux community were helpful, so can someone tell me what I should do here. 

Do I sit for ever waiting for a reply? Should I roll back to my earlier version, like the OP asked, and how do I do it?

Or should I just ditch Ubuntu and try to find something that works?

---

### Post by anglican on 2010-05-11
> **aoc said:**
> My Pixma ip1500 has stopped working after the 10.04 upgrade as well. It also took a bit of work in 9.10, but I got there eventually.
I also see the printer icon for a second after I send a test page, and the print job number increases, but there is nothing in the print job list. Even the completed jobs list is empty.
Can anyone offer some advice on what to try.
What errors are showing up in the log file (/var/log/cups/error.log)?

H

---

### Post by Shtrk on 2010-05-11
My canon ip1600 worked only in 9.04. Since then is dead.... And back then, I spend days on forums untill make it work.

---

### Post by aoc on 2010-05-11
Thanks anglican.
There was nothing in the error log, but there are 7 other error log folders. Error_log.2 had the following;

E [09/May/2010:10:36:24 +0800] [Job 12] Invalid printer command "Clean"!
E [09/May/2010:10:39:44 +0800] [Job 13] Invalid printer command "Clean"!
E [09/May/2010:10:43:41 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [09/May/2010:10:47:15 +0800] [Job 16] Unable to queue job for destination "Canon-iP1500-2"!
E [09/May/2010:10:47:18 +0800] [Job 16] Unable to open job control file "/var/spool/cups/c00016" - No such file or directory!
E [09/May/2010:10:48:23 +0800] [Job 16] Unable to open job control file "/var/spool/cups/c00016" - No such file or directory!
E [09/May/2010:11:32:07 +0800] [Job 16] Unable to open job control file "/var/spool/cups/c00016" - No such file or directory!
E [09/May/2010:11:32:19 +0800] [Job 16] Unable to open job control file "/var/spool/cups/c00016" - No such file or directory!
E [09/May/2010:11:38:02 +0800] [Job 16] Files have gone away!
E [09/May/2010:11:38:02 +0800] Missing <Job #> directive on line 104!
E [09/May/2010:11:38:02 +0800] Missing <Job #> directive on line 105!
E [09/May/2010:11:38:02 +0800] Missing <Job #> directive on line 106!
E [09/May/2010:11:38:02 +0800] Missing <Job #> directive on line 107!
E [09/May/2010:11:38:02 +0800] Missing <Job #> directive on line 108!
E [09/May/2010:11:38:02 +0800] Missing <Job #> directive on line 109!
E [09/May/2010:11:38:02 +0800] Missing <Job #> directive on line 110!
E [09/May/2010:11:38:02 +0800] Missing <Job #> directive on line 111!
E [09/May/2010:11:38:02 +0800] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [09/May/2010:12:29:18 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [10/May/2010:17:06:46 +0800] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory


I have to go to work now, but will be back in about 11 hours.

---

### Post by aoc on 2010-05-11
OK, I'll leave a little later. Silly of me not to look for error logs. I have been relying on google far too much.

error_log.1

E [10/May/2010:17:55:26 +0800] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [10/May/2010:18:56:23 +0800] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [11/May/2010:17:22:31 +0800] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory

error_log.3

E [08/May/2010:17:39:12 +0800] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [09/May/2010:05:30:47 +0800] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [09/May/2010:05:30:48 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [09/May/2010:05:31:11 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [09/May/2010:05:31:15 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [09/May/2010:05:31:50 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [09/May/2010:05:32:13 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [09/May/2010:05:32:41 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [09/May/2010:05:33:54 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [09/May/2010:05:34:48 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [09/May/2010:05:47:06 +0800] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory

error_log.4

E [07/May/2010:18:37:15 +0800] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory

logs 5 6 7 are the same. I upgraded on the 8th, so this looks like something went wrong at an earlier time. I don't use the printer that often.
Perhaps I will look for that directory and delete it?

---

### Post by IdahoBackwoods on 2010-05-11
My Canon iP4500 still works after the 9.10 --> 10.04 upgrade.  However, I use TurboPrint for printing because I was unable to get full functionality without it.

---

### Post by douglaswood34 on 2010-05-11
Okay,  I had the same exact problem.  I have an Epson Stylus CX8400.  When I upgraded to 10.04, it ceased to work.  Here is what I just did.

Go to [http://www.openprinting.org/printers](http://www.openprinting.org/printers)

Enter your printer information to search for your printer and suggested drivers.  It will list the recommended drivers near the bottom of the page.  Choose the .deb file that is newest 5.2.5 (DEB for LSB 3.2) in my case.  I chose to run the file.  That installed the newest driver for the printer, and there you go....  I was finally able to get a test page.  I also printed another page (one I had been waiting on!) after the install.  Works like a charm.

---

### Post by maxquad on 2010-05-11
Ya I had problems with the same error all I had to do is reinstall printer cups

---

### Post by aoc on 2010-05-12
Still not working, but I have tried a few things.
I uninstalled and reinstalled cups, but ended up with the same error messages.
I did the classic delete printer, unplug printer from usb and power, and reboot computer and reconnect printer, and the printer was recognised and installed, but I still get the following error message;

E [12/May/2010:18:33:48 +0800] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!

When I look in that folder (/usr/share/cups/drv/) it is empty. What should cups be looking for there, and how do I get it in there.

I realise that this is probably not an issue created from the 10.04 upgrade, so I will leave it to the mods to decide if this should go in a fresh thread.

---

### Post by ZX3Junglist on 2010-05-27
I'm having a similar issue. I have an HP 1600 series, which worked flawlessly in 9.04 without any configuration. On the same hardware, I did a clean install of 10.04. When I plug the printer in, it is detected and drivers are installed automatically. The printer is listed in printers. But, when I try to print anything, even a test page, the printer does nothing, just stays idle.

---

### Post by richard24680 on 2010-05-29
Printer Canon Pixma iP1500 in Ubuntu 10.04 also does not work for me. 

Is there any solution?

please, point it step by step if somebody can help.

thanks.

---

### Post by richard24680 on 2010-05-29
I have read and tried all the answers but I can not see a way to put the Printer Canon Pixma iP1500 to work in Ubuntu 10.04.

any help? please.

---

### Post by ankle on 2010-07-07
I'm also having problems, I'm afraid - got the Pixma iP2500 working in 9.10, eventually, but can't get anything to print in 10.04.

---

### Post by recluce on 2010-07-08
I have both an older i865 and an ip4500, both are working fine for me (Ubuntu 10.04 x64, clean install). I did, however, install the Canon proprietary driver for a better print quality, per the instructions that can be found somewhere in this thread:

[http://ubuntuforums.org/showthread.php?t=975747](http://ubuntuforums.org/showthread.php?t=975747)

---

### Post by victorhugo289 on 2010-07-21
> **QuahogRocks said:**
> bump

Ha ha ha , why do you have to say "bump"? ! Lol

---

### Post by A.dela on 2011-08-31
Mmmm... same problem here: recognises the printer with the 2200 drivers but when I try to print everything seems to queue forever (and icon flashes just for a moment at the top bar).

I find this, so it seems the document has been sent:

```
localhost - - [31/Aug/2011:15:52:38 +0200] "POST /printers/Canon-iP2200 HTTP/1.1" 200 499 Create-Job successful-ok
localhost - - [31/Aug/2011:15:52:38 +0200] "POST /printers/Canon-iP2200 HTTP/1.1" 200 430610 Send-Document successful-ok
```

And these are my only error logs at cup (which are not from the same time I sent the last file):

```
E [01/May/2011:12:22:47 +0200] Unable to bind socket for address [v1.::1]:631 - Cannot assign requested address.
E [01/May/2011:12:23:23 +0200] Unable to bind socket for address [v1.::1]:631 - Cannot assign requested address.
```

Been a while trying to get this worked. Is anything I'm missing? ](*,) I'm quite new so it may be a simple thing I missed...

Meanwhile, think I'm saving the documents in a pendrive and goint to windows to print :(

---

