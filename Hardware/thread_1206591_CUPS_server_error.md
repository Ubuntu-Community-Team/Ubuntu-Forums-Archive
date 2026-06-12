---
title: "CUPS server error"
date: 2009-07-07
forum: Hardware
---

### Post by mac71 on 2009-07-07
Hi all,

I recently re-installed from a remastersys back-up and all has gone well.
My only problem is, that when I try to get my printer installed/sorted, all I can get is:

The CUPS scheduler is not running.

I've checked in "bum" under services and cups is there, but not running and when i click to start, it reports that its started, but i still get the same "The CUPS scheduler is not running."

CUPS is apparently not in the startup and shutdown scripts either.

Anyone have any ideas on how i can fix this?

---

### Post by shatterblast on 2009-07-07
I think that's a standard issue for Remastersys maybe.  At least, I have had a similar contention with it in the past.  Basic solution:  reinstall your printer driver.  This could be done by unplugging your printer, turning off its power, and maybe reinstalling CUPS if necessary.  Rebooting the system comes next without the printer connected.  (Don't kick it please.)  If all seems fine, turn off the computer, reconnect the printer with it powered on, and turn the computer back on.

---

### Post by mac71 on 2009-07-07
Thanks, I'll give it a whirl in the morning and let you know the outcome.

---

### Post by mac71 on 2009-07-08
> **shatterblast said:**
> I think that's a standard issue for Remastersys maybe.  At least, I have had a similar contention with it in the past.  Basic solution:  reinstall your printer driver.  This could be done by unplugging your printer, turning off its power, and maybe reinstalling CUPS if necessary.  Rebooting the system comes next without the printer connected.  (Don't kick it please.)  If all seems fine, turn off the computer, reconnect the printer with it powered on, and turn the computer back on.
Ok, tried all that and still got the same outcome. :confused: Any other ideas?

---

### Post by shatterblast on 2009-07-08
Try the following line in Terminal please.

sudo /etc/init.d/cups restart

After that, check if you're system recognizes the printer.  It could be a permissions issue with that file.

---

### Post by mac71 on 2009-07-08
> **shatterblast said:**
> Try the following line in Terminal please.

sudo /etc/init.d/cups restart

After that, check if you're system recognizes the printer.  It could be a permissions issue with that file.
Ok, tried that and got this:

```
* Restarting Common Unix Printing System: cupsd 
cupsd: Child exited with status 1!
                                                                      [fail]
```
:frown:

---

### Post by shatterblast on 2009-07-09
This may help.  Try the following from Terminal please:

sudo apt-get install --reinstall ssl-cert

After that, reboot and try the following again from Terminal:

sudo /etc/init.d/cups restart

Apparently, the "server.crt" and "server.key" symlinks may need repair.  Reinstalling "ssl-cert" supposedly applies the fix.  It could be essential to delete those two files directly and then reinstall the file again if CUPS still fails to restart.

I assume that parts of Remastersys are fairly outdated from Intrepid to Jaunty.  I like the software, but it could use tweaks in my meager opinion.

---

### Post by brianbaru on 2009-07-10
i had the same problem but this post cured it

[http://ubuntuforums.org/showthread.php?t=1086562&highlight=cups+error+child](http://ubuntuforums.org/showthread.php?t=1086562&highlight=cups+error+child)

8.10 Hp 1215 cups server error post

entered following line

sudo update-rc.d cups defaults && sudo /etc/init.d/cups start

fixed it for me hope this helps

---

### Post by tgyorgyi on 2009-07-13
Shatterblast: thank you. I have installed a custom iso made with Remastersys, so had high hopes, and your suggestion worked, now I can connect printers. 

Thank you!

---

### Post by mac71 on 2009-07-13
> **shatterblast said:**
> This may help.  Try the following from Terminal please:

sudo apt-get install --reinstall ssl-cert

After that, reboot and try the following again from Terminal:

sudo /etc/init.d/cups restart

Apparently, the "server.crt" and "server.key" symlinks may need repair.  Reinstalling "ssl-cert" supposedly applies the fix.  It could be essential to delete those two files directly and then reinstall the file again if CUPS still fails to restart.

I assume that parts of Remastersys are fairly outdated from Intrepid to Jaunty.  I like the software, but it could use tweaks in my meager opinion.

OH YES!!!! Shatterblast, you're a star! Saved that bit of code in my home in case I need it again (probably). Nice one. Thanks.

---

### Post by mac71 on 2009-07-13
Now I've got the printer recognized and functioning, I have another issue. All documents start printing about an inch too far up the page. For instance;
On the test print page, the ubuntu logo has the top quarter chopped off and printing starts around 5mm from the very top of the page. 

Anyone know what file, and or how to edit it so that it prints correctly?

---

### Post by shatterblast on 2009-07-13
> **mac71 said:**
> Now I've got the printer recognized and functioning, I have another issue. All documents start printing about an inch too far up the page. For instance;
On the test print page, the ubuntu logo has the top quarter chopped off and printing starts around 5mm from the very top of the page. 

Anyone know what file, and or how to edit it so that it prints correctly?

I think that accessing Page Setup from most major programs should allow a fix to the margin sizes.  Assuming that a system reboot and turning the printer on and off doesn't fix the issue, it could be necessary to just "Manage Custom Sizes" under the Paper Size section.  Since I edit art a lot, mine worked under GIMP just fine, but it did not with the Eye of GNOME software.  I assume the feature should work fine under OpenOffice and Firefox.  I have different custom page types on my system since I do photo-printing.

---

### Post by mac71 on 2009-08-11
Ok, tried LOADS of things to get this printer issue sorted. Even 2 fresh install's of 9.04 (one using ext3 and another using ext4) didn't fix the problem.

Strangely though, I installed 8.10 and all was fine. After upgrading to 9.04, everything continues to be fine. Dunno what that's all about, but hey, it's all fixed and working like a charm. 

I'm a happy chappie again!:)

---

