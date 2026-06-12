---
title: "Printer problems with Hardy (worked with Dapper)"
date: 2008-08-26
forum: Hardware
---

### Post by nexus_2006 on 2008-08-26
Hello.  I just started fall semester at university and I cannot geet my printer to work (uh-oh).  I have a Canon PIXMA IP6600D that worked with dapper by following the instructions on this page:

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

This time around, though, it will not work.  I upgraded from Dapper to Hardy over the summer, and this is the first time I have had my printer setup.  Can anyone help me?

I installed the repos, the packages, plugged the printer in, and got a system notification saying that "ip6600d has been added".  In the printers dialog it is there, correct driver cited, and all the options (duplex, etc) that should be there are, but even that test page won't print.  I log on to the local CUPS server and the printer is present there too.  I can add jobs, delete them, pause them, but nothing ever comes out of the printer.

What can I do?

---

### Post by nexus_2006 on 2008-08-27
Bus 005 Device 006: ID 04a9:10a9 Canon, Inc.

Thats the output of lsusb.

I have found that it tries to add 2 different URLs for the printer, it either tries 

usb://Canon/IP6600D
canon:/dev/usb/lp0

but neither seems to work.  Thats all I have been able to find out so far.

Any help?

---

### Post by nexus_2006 on 2008-08-28
I really don't know what else to do, and really need help.  I don't want to have to boot windows to print assignments now that I've "upgraded" to 8.04, when this printer worked with 6.06.

(right, this is basically just a bump ;))

---

### Post by nexus_2006 on 2008-08-28
OK, I've been trying to figure this out by finding somw wikis and other pages.  I've come to the conclusion that this either will not work with Hardy because the drivers haven't been confirmed to worki since Edgy.  The other option is that my cups install is fubar.  I'll work under that assumption and try to see if I can find the config files that cups uses and maybe add my printer manually, or see what the deal is.  No matter what drivers or location I give to the thing, if I delete it and try to add it againi (different name, same name, different location, etc) CUPS still remembers how many jobs its supposed to have.  I need to clear this info out and get a fresh start.  I tried a reinstall of everything cups from synaptic, but it didn't change this behavior.

Hopefully someone can comment or add to the above conversaion I'm having with myself :p

---

### Post by Sef on 2008-08-28
Check out this [link]("http://forums.linux-foundation.org/read.php?25,1671,1671,quote=1").  It's for 7.04, but it could work with your system.

Here's the [gentoo wiki]("http://gentoo-wiki.com/Canon_Pixma_Series").

An [ubuntuforum thread]("http://ubuntuforums.org/showthread.php?t=282096&highlight=pixma&page=7") (be sure and read the last  post.)

Check out [turboprint]("http://www.zedonet.com/en_p_turboprint.phtml").

---

### Post by esmrg on 2008-09-01
Hi!

The problem with printing that many people are having with Hardy is NOT related to the printer. It is cupsys.

I've been looking around for answers and I found them.

A big change was made to 8.04 - that is - the inclusion of AppArmor into the kernel. Now, an easy fix is usually to disable apparmor, but that isn't a very good workaround.

Typically when something doesn't work after a distribution upgrade, there was a major change made to a configuration file of said package. During the upgrade depconf usually complains to the user about the change - and asks the user to either keep their files, or install the new one. Unless you have a very very custom setup that you personally hand edited, the best choice is to install the new configuration. However, sometimes there are problems or they fix the configuration file later.

In this case, a simple uninstall - reinstall of cups will not work. You need to tell dpkg to do a purge (or remove all config files).

sudo dpkg --purge --ignore-depends=cupsys cupsys

if it complains about some files couldn't be removed:
delete everything in /etc/cups

sudo apt-get install cupsys



this should get you a fresh cups config for apparmor

you will have to install your printer again

---

### Post by pYrO1v1aniac on 2008-09-07
I've tried the solution posted above, and it appears to have made no difference towards making this printer usable in 8.04 hardy heron. Does anyone have any solutions which work?

---

### Post by delilahjed44 on 2008-09-07
Hello, I am leaving this note as a possible connection for others that may run into this issue with this printer and or PSC ALL-IN-ONE PRINTER/SCANNERS which is to my ownership. So when they type in the info in search this may come up to help them.  Not to mention but it works with other printers as I have found this here in the forums.

OS> UBUNTU HARDY HERON ( 8.04 ) NEW INSTALLATION.

Printer PSC 2355 All-In-ONE stopped working. I opened synaptic, un-installed everything foomatic. Installed gnome-cupsy-manager. Tried to print, but printer icon said, missing foomatic filters. Went back to Synaptic, re-installed (FOOMATIC FILTERS) only.

Un-installing foomatic.

Choose the search icon at the top of synaptic. Then in the find box type in foomatic, then for each search use the drop down arrow in the (LOOK IN) and start with name. Continue down each choice until foomatic files come up, the ones on your OS will be colored in green boxes. Clk un-install then apply.

Then go back to search and find gnome-cupsy-manager. If its not installed you will see the box colored white, so mark it install and apply.

Now back at my desktop:

I then created a new icon for the printer, System-Administration-Printer. However I chose to use 2210 PSC for the manufacturer HP, as they did not have the choice of my own printer (2355). NOTE, very important...There is no foomatic-rip file for the PSC 2355 ALL-IN-ONE SCANNER/PRINTER. In this you must create a new printer/icon and choose the closest printer mode you can get to. Next choice for 2355 was 2210. In this you can get your printer working correctly. Be sure to configure the manufacturer and the mode you created as your new printer when using your programs to print out photo's and or anything. Reason giving, because even though I made it my default, in most of my programs settings it is still choosing the 2355, < this wont be acknowledged because of the foomatic-rip. So with each program for printing your goodies make sure its configured to your new printer icon to what best suites your printer. This could change later but if you want it up and running now, this works great.

---

