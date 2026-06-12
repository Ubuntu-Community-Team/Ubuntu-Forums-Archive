---
title: "[SOLVED] Epson V200 scanner &amp;amp; Hardy"
date: 2008-08-17
forum: Hardware
---

### Post by 2CV67 on 2008-08-17
I recently bought & installed in Gutsy a new Epson V200 scanner, thanks to the excellent thread:
 [http://ubuntuforums.org/showthread.php?t=627650&page=3](http://ubuntuforums.org/showthread.php?t=627650&page=3) (now archived).

I just did a clean install of Hardy, so am ready to reinstall the scanner.

Is the best (& complete...) procedure that shown in post #41 of that thread?
> I've got my scanner working! I added the line "epkowa" to the /etc/sane.d/dll.conf file as suggested here:
[http://uellue.de/blog/single.php?date=1192278660](http://uellue.de/blog/single.php?date=1192278660)

So, to summarise, for Ubuntu Hardy users the process is:

Download the driver RPMs "iscan" and "iscan-plugin".

Unpack them and use "alien" to convert to deb packages.

Install them using the "dpkg --install" command or by right clicking on the file and then clicking "Open with GDebi package installer"

Add the line "epkowa" to /etc/sane.d/dll.conf

Check that your scanner is seen using "scanimage -L"

You should now be ready to scan using xsane.

One cautionary note - I haven't yet thoroughly tested my scanner, but it has successfully acquired a preview so it should be OK.

Or what? 

Thanks for any help!  :)

---

### Post by 2CV67 on 2008-08-28
Well, in the end I did just that & basically it works straight away!

Thanks to robc02 & thanks to Epson!

Slight snag with XSane Viewer, see:[http://ubuntuforums.org/showthread.php?t=901664](http://ubuntuforums.org/showthread.php?t=901664)
but I guess that is nothing to do with installing the V200.

Wouldn't it be nice if it was just plug-&-play though?....

---

### Post by boddhisatva on 2008-11-07
Has anyone made the scanner work under Intrepid? After the upgrade the system no longer recognizes it. I went over the same procedure as half a year ago on Hardy, but it doesn't help.

---

### Post by 2CV67 on 2008-11-07
Sorry, I (who started this thread) am not even going to try Intrepid until the kernel-panic problems (started in Hardy & continuing in Intrepid) are fixed.

See:[http://ubuntuforums.org/showthread.php?t=832383](http://ubuntuforums.org/showthread.php?t=832383)

For me, Ubuntu is dead in the water for now.
Thank goodness for XP.

Sorry. :icon_frown:

---

### Post by wsscott on 2008-11-16
I have the same question as boddhisatva. Does anyone have the Epson V200 scanner working in Intrepid?  I also followed the uellue link. Everything seems OK except the scanner isn't recognized with scanimage -L.

---

### Post by wsscott on 2008-11-16
Additional information......  The Epson V200 is recognized with "sudo scanimage -L", but is not recognized without "sudo".  Do I need to somehow fix permissions?

Thanks

---

### Post by boddhisatva on 2008-11-16
> **wsscott said:**
> I have the same question as boddhisatva. Does anyone have the Epson V200 scanner working in Intrepid?  I also followed the uellue link. Everything seems OK except the scanner isn't recognized with scanimage -L.

I got the scanner working in Intrepid. As in Hardy, I followed the instructions from here: [http://ubuntuguide.org/wiki/Dapper#Setting_up_USB](http://ubuntuguide.org/wiki/Dapper#Setting_up_USB)
It talks about lisane.rules. Now, in Hardy that file doesn't exist and isn't necessary (it worked fine without it). In Intrepid the file doesn't exist either, but for some reason the scanner doesn't work like it did in Hardy. So I just **created the file** (/etc/udev/rules.d/45-libsane.rules) and put whatever came out of 'lsusb' into it (in fact I just copied the line from that link, as 'lsusb' showed the same as there). In other words, I just followed the instructions to a T, the only thing I needed to do extra was create the libsane.rules file and copy the text there. I was quite amazed that worked (it was a rather random idea). I hope it will be the same on other machines running on Intrepid.

---

### Post by wsscott on 2008-11-30
Followed instructions from boddhisatva to add 45-libsane.rules to /etc/udev/rules.d/........scanner worked immediately!

---

### Post by Tanker Bob on 2008-12-13
Had the same problem with my Epson Stylus CX7800. Adding 45-libsane.rules to /etc/udev/rules.d did not work for me. There is already a file 50-libsane-extra.rules there that has the appropriate lines in it. I did fix it by creating and adding the proper information to /etc/sane.d/epkowa.conf. That file was in Hardy but missing from my Intrepid installation. I posted the details [here](http://reformedmusings.wordpress.com/2008/12/13/fixing-epson-scanners-in-ubuntu-810-intrepid-linux/). Scanner now works fine.

---

### Post by herdivet on 2008-12-27
I have this 'almost' working fine in 8.10, however...
sudo scanimage -L shows the printer.
sudo xsane warns me I shouldn't do this, but it works.
xsane as user reports no scanner found.

I followed the directions above, only I had to add epkowa to /etc/sane.d/dll.conf

I feel like I'm almost there, but not quite there.  Any suggestiions?

Thanks!

---

### Post by Tanker Bob on 2008-12-27
Check your user Group settings. You have to add yourself (and whomever else will use the scanner) to the Scanner group, or simply give yourself permission to access the scanner depending on your distribution. After that, you shouldn't need to use sudo to run XSane.

---

### Post by herdivet on 2008-12-30
Added myself to the scanner group, didn't make any difference.  It must be a permission problem somewhere.  Not sure where and I'll have to start digging around for it.

Thanks for the reply, that was a really good idea, and I thought it should fix it.  Of course things seldom are that simple.

---

### Post by Tanker Bob on 2008-12-30
> **herdivet said:**
> Added myself to the scanner group, didn't make any difference.  It must be a permission problem somewhere.  Not sure where and I'll have to start digging around for it.

Thanks for the reply, that was a really good idea, and I thought it should fix it.  Of course things seldom are that simple.

Did you log out after changing the permission? Permission changes don't take until you re-login. If that doesn't work, try restarting.

---

### Post by herdivet on 2009-01-02
Yeah, I rebooted and it hasn't resolved the problem.  It's gotta be permission, but I'm not sure where.  If I run '/usr/bin/iscan' it gives an error that it "could not send the command to the scanner, check the scanner status".  If I do sudo /usr/bin/iscan it executes fine.

---

### Post by 2CV67 on 2009-01-28
I started this thread for my V200 in Hardy & have just upgraded to Intrepid & lost my scanner.

I followed the very clear track from Tanker Bob [here]("http://reformedmusings.wordpress.com/2008/12/13/fixing-epson-scanners-in-ubuntu-810-intrepid-linux/") - thanks!

I have user priviledges for the scanner OK (but...)

lsusb finds it OK.

Synapt shows everything there except libsane-extras
Trying to install that leads to Error messages (attached) & so no installation.

Didn't do any special installs or restarts.

sane-find-scanner finds it OK.

scanimage -L does not find it.

sudo scanimage -L does find it...

/usr/bin/iscan leads to an error.
sudo /usr/bin/iscan works just fine.

It sounds like a simple permissions problem.
I rechecked that in Users & Groups I DO have scanner permission.
I have not started inventing files or anything fancy, since the thing works for sudo.

Any suggestions?

---

### Post by 2CV67 on 2009-02-04
Bump?

I just ran through the procedure in the above post again & got exactly the same results.

Anybody know what that means?

What does the error message, when failing to install libsane extras mean?
Can I fix that?
Do I need to?

Why does sudo scanimage -L find it but not without sudo, when I have scanner permission?

Why does sudo /usr/bin/iscan actually produce a fully working scanner application, but not without sudo..

What is iscan (vs Xsane etc)?
How can I launch it by GUI?
I see iscan in Synaptic, but can't find any way to launch it by GUI.
Can't find it in Add/Remove or any menu possibility.

Thanks for any clues.

---

### Post by Tanker Bob on 2009-02-04
It still sounds like a permission issue. Try giving yourself permission to everything to do with USB devices, logout/in, and see what happens. If that doesn't work, try giving yourself permission for everything, logout/in, and see. I think that there has to be some errant permission laying around ambushing you.

---

### Post by 2CV67 on 2009-02-05
Thanks - I will try that today.

By the way - I started a new thread for Epson V200 in Intrepid, because I thought the title to this thread was now doubly out-of-date!
It had been [SOLVED] for Hardy but is not entirely for Intrepid...

[http://ubuntuforums.org/showthread.php?t=1060319](http://ubuntuforums.org/showthread.php?t=1060319)

---

### Post by 2CV67 on 2009-02-05
See [http://ubuntuforums.org/showthread.php?p=6680404#post6680404](http://ubuntuforums.org/showthread.php?p=6680404#post6680404) for results etc

---

