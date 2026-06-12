---
title: "Can't add printer in new install"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by GeekPapa on 2009-11-08
I am in agony after installing 9.10 due to changes which require me to re-learn service management in Ubuntu at a time when I just don't have the bandwidth.  That having been said:

Ubuntu 9.10 does not allow me to install a printer.  I have a network OfficeJet and while the System->Administration->Printing applet comes up, it does not allow me to do a connect local (fails with There was an error during the CUPS operation: 'httpConnectionEncrypt failed'), and the "Server->New" Menu won't allow me to choose printer.  CTRL+N doesn't work either and [http://localhost:631/](http://localhost:631/) doesn't appear to have anything on it.  In fact, there doesn't seem to be an httpd running at all. 

Is there a graphical manager or command line tutorial for Upstart?  I need to get a printer on this thing asap.  Oh, and for the record, hp-setup finds the printer, but no ppd, but I don't want to pursue that avenue because it seems inside-out.

TIA

---

### Post by sexyclient2 on 2009-11-09
Same exact problem here.  64-bit Ubuntu 9.10 printing fails!  I have a Brother printer serving up print-jobs via wifi, but I can't do anything with Ubuntu 9.10...  Just works my ***.  This release should still be in beta (cuz it sure as hell ain't production-ready.)  Sharing fails, bluetooth fails after one use, wwan fails to stop draining my battery, sound fails during voice-chat in empathy AND pidgin, and now after trying to setup my network printer -- drum-roll, please, as this may come as a shock-- PRINTING ALSO FAILS!  I reiterate: "Ubuntu: Linux that just works," my ***...

Please excuse my rant.  I'm pissed at the bevy of failures (and at the overwhelming lack of support for these problems) that I've encountered with this accursed koala.  I have a paper to hand in tomorrow, but thank god for windows!

EDIT:
[http://ubuntuforums.org/showpost.php?p=8271133&postcount=4](http://ubuntuforums.org/showpost.php?p=8271133&postcount=4)
Thanks to advice from the user "Iowan", I've figured out how to solve the problem.  I just copied the command he gave me to fix samba and replaced "samba" with "cups".  The simple solution is to type this into the terminal:
```
sudo /etc/init.d/cups restart
```

---

### Post by GeekPapa on 2009-11-12
The samba fix didn't work for me.  What DID work was downloading CUPS 1.4.1 source and installing that from the code base.  Not available on Repos, but the source compiled clean, installed and worked like a champ.

[Standing on Soap Box]  Ahem... "If linux is ever going to be accepted as a replacement for other desktop operating system, EVERY new release must come with the basics intact - sound, video, browsing, printing... etc." [Steps down, straightens pocket protector]

Thanks folks.

---

### Post by nike984 on 2010-03-05
as Lutz pointed out in the following link, 
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/335898/comments/7](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/335898/comments/7)
it could be an AppArmor issue. 

Try ```

sudo aa-complain cupsd
sudo /etc/init.d/cups restart
```It worked for me.

---

### Post by captainseabag on 2011-05-26
Thanks! That worked for me in 10.04 lucid.

Cheers guys. I'm starting my UCP this week and am excited to get deeper into the wonderful world of Ubuntu. I've already installed it for hundreds of my clients!

---

