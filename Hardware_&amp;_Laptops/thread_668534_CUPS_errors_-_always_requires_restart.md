---
title: "CUPS errors - always requires restart"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by vancouverite on 2008-01-15
Hello ubuntu forums,
I have a new problem with CUPS.  Everytime I restart my computer the cups system goes down.  When I go to the printer configuration everything is grayed out except "Go to server" and "Refresh" (see attached image).  Refresh doesn't seem to do anything, and when I select go to server and input "localhost" as the cups server I get the following error:

"There was an error during the CUPS operation: 'httpConnectionEncrypt failed'." (see attached image)

If I go to terminal and restart cups with "sudo /etc/init.d/cupsys restart" everything begins to work just fine (see attached image).  I tried reinstalling cupsys through synaptic and also gnome-cups-manager, but that didn't work.

My computer is in an engineering lab and has the lab printer connected to it.  Many of my lab mates were dubious about my switch to ubuntu and I am working hard to get them on the band wagon.  Please help me fix this before I have to move the printer to a M$ machine.

I have attached part of the cups error log (I had to truncate it to fit the forum's file size limit - it was mostly repeats as I restarted numerous times today and got the same errors every time) and some screen shots of the print manager and error in a hope that it will help to clear this up.

Thanks for your help.

---

### Post by Spenzer4Hire on 2008-01-16
Same exact issue here.  The problem showed up after the most recent CUPS update.  It's manifested itself on 2 fresh 7.10 i386 installs.    Restarting cups fixes the problem.

What gives?

---

### Post by Spenzer4Hire on 2008-01-16
Well, I just noticed that unchecking the "share published printers" check box allows CUPS to start properly on boot.

I've filed a bug report here [https://bugs.launchpad.net/ubuntu/+bug/183652](https://bugs.launchpad.net/ubuntu/+bug/183652)

If you have anything to add, please do.

BTW, I don't have any issues on my AMD 64 install.

---

### Post by Spenzer4Hire on 2008-01-16
My error log is different than vancouverite's.  (I think I'm at a different log level or something.)

When the "Publish shared printers" checkbox is unchecked I get no errors in the log.

When the checkbox is checked I get these errors in my log on boot:

E [16/Jan/2008:17:37:41 -0600] cupsdAuthorize: Local authentication certificate not found!
E [16/Jan/2008:17:37:41 -0600] cupsdAuthorize: Local authentication certificate not found!
E [16/Jan/2008:17:37:41 -0600] cupsdAuthorize: Local authentication certificate not found!
E [16/Jan/2008:17:37:41 -0600] cupsdAuthorize: Local authentication certificate not found!
E [16/Jan/2008:17:37:52 -0600] DNSServiceRegister failed with error -65537

But when I run /etc/init.d/cupsys restart while the checkbox is checked I get no errors in the log and CUPS works fine.

Makes me wonder if CUPS is starting before another critical service or something.

---

### Post by vancouverite on 2008-01-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/183652](https://bugs.launchpad.net/ubuntu/+bug/183652) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I also found that disabling the printer sharing fixed the problem.  An unfortunate consequence.

Also, was it the most recent CUPS update, or the avahi updates?  I received updates for both recently and had actually attributed this problem to avahi, but rolling back to 3.0 from 3.1 doesn't help.

BTW, printer is now on a M$ machine :(

vancouverite

---

### Post by Spenzer4Hire on 2008-01-16
I couldn't say.  You probably have more insight into the situation than I.  I'm just hoping the launchpad guys figure it out.

---

### Post by miltonics on 2008-01-18
There was an avahi update today.  I hope that fixed the problem.

---

### Post by kraymore on 2008-01-20
well, i am waiting for the fix to be distributed through ubuntu.  i hope its really soon.  i need to print on all my computers.  i think the packages started messing up 4 days ago.  before then it was working fine.  can't help but think that this has effected many people in the working/business world.

---

### Post by TSJason on 2008-01-21
:-) Today's update fixed this for me

---

### Post by Tulsapoke on 2008-01-22
My parents just had this same problem.  His system is totally up to date.  Hopefully they are still working on fixing this.

---

