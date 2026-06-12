---
title: "HP LaserJet CP1525nw and Maverick 10.10"
date: 2010-12-21
forum: Hardware
---

### Post by odinb on 2010-12-21
Hi!

Purchased the HP LaserJet CP1525nw yesterday after my HP LaserJet 1200 gave up after over 8 years of usage....

HPs webpages states support for Linux (and Ubuntu as of 8.04) for this printer, so I was pretty sure there would be no issues. Yeah, right!

Already have HPLIP installed and working with my HP Deskjet 6940, so I thought it would be a breeze to add this one. "Setup Device" > "Device Discovery" does however not see the printer. No problem, I thought, I just need a newer version (3.10.9) of HPLIP, since I was running 3.10.6.
Could not find a repo carrying this, so I went to [COLOR="Blue"][hplipopensource.com]("http://hplipopensource.com/hplip-web/install/install/index.html")[/COLOR], but the webpage was/is down.
Referral to [COLOR="Blue"][sourceforge.net]("http://sourceforge.net/projects/hplip/files/hplip/")[/COLOR], where I finally downloaded 3.10.9 only to have the install fail on me due to dependency issues!!

Found the solution [COLOR="Blue"][here on the forums]("http://ubuntuforums.org/showpost.php?p=10250082&postcount=4")[/COLOR], and finished off the install.

After logging out and back in, I find myself at "square one" again, with "Setup Device" > "Device Discovery" still not seeing the printer.

"System" > "Administration" > "Printing" does however see the printer, and detects it correctly, but does not have a driver.
Try to find a driver on [COLOR="Blue"][openprinting.org]("http://www.openprinting.org/printers")[/COLOR], but cannot find anything.

Since CP1515 is almost the same printer, I try feeding it that file, but this does not work either.

At this point I pick up my Hackintosh, download all needed driver and firmware update files from HP.com in a couple of minutes, and can verify that there is nothing wrong with the printer.

Retry the detect from HPLIP after the firmware update of the CP1525nw done from my Hackintosh. No change...

At this point I contact HP-online-chat, but the Indian support guy I get to chat with has no clues about Ubuntu.....he referrs me to phone support, where they supposedly know more about Ubuntu.

Phone support only referrs me to hp.com, and when I point out for the second time that I have tried that already, and that these pages states support for ubuntu, he suggest that I install the priner on a windows machine, I politely decline, stating I have no machine running windows and hang up...

Anyone else out there that has any hints on how I can preferably get HPLIP to detect my printer?
If not, then maybe point me to a functioning ppd-file?

"sudo hp-check -r" ouptut can be found here: [http://pastebin.com/mhgzjLFV](http://pastebin.com/mhgzjLFV)

hplip install-log can be found here: [http://pastebin.com/RhiqcExV](http://pastebin.com/RhiqcExV)

Thanks!

---

### Post by odinb on 2010-12-22
Ok, have been googling around a bit more, experimented a little more, and actually got it working somewhat, just not with HPLIP (go figure...).
It prints pictures extremely slowly however, it takes anything from minutes to half an hour or more to print pictures.

Do the following:

Go to "System" > "Administration" > "Printing".

Then from the window that opens up, you choose "Add", then click "Network Printer" and "Find Network Printer", then wait about 5-10 seconds, and you should see the "HP LaserJet CP1525nw" listed twice.

Choose the one that has the IP-address of the printer in round brackets. The one with the Mac address in round brackets will not work.

Click "Forward" and then pick "HP" from the list, click "Forward" again, then pick "Color LaserJet" from the list, and the driver "HP Color LaserJet Series PCL 6 CUPS".

Click "Forward", and "Forward" a second time since we have no duplexer on this unit, and finally choose a name (or use the pre-filled one if you like) and finally click "Apply". Now you can print a test page, and then you are done!


Good luck!

---

### Post by billstei on 2011-01-28
This is working for me, but here is a mistake I made at first... there are two drivers in that list:

HP LaserJet Series PCL 6 CUPS
HP Color LaserJet Series PCL 6 CUPS

I accidentally picked the first one, and got black & white all the time. :redface:

Printing is very slow.  Any ideas why?  I have not done any firmware upgrades yet -- it has firmware version 20100430, which is not the latest.

------

Update: Upgraded firmware to 20101125, but printing was still very slow, about 15 minutes for a 1024x768 jpg.  Tried printing the same picture from Windows Vista and it only took about 30 seconds.

---

### Post by odinb on 2011-03-13
What does your Device URI for the printer specify?

It needs to print to the printer as HP-JetDirect, so your URI should look something like this: socket://192.168.1.220:9100

Mine prints more or less immediately.

---

### Post by scarab on 2011-04-03
I think the following is related, no answer yet:

hp laserjet pro M1530 MFP

Hi

using Kubuntu 10.10, just connected an hp laserjet pro M1530 MFP directly to networking.

installed it via system settings-printer conf and all goes OK for printing.

Now trying to scan and no way.
other data:
I can ping the printer with no problems

when using hp-setup, no way for the device to be found, not even using its IP:
Error: "/var/tmp/kdecache-scarab" is owned by uid 1000 instead of uid 0.
(4250) KSharedDataCache:rivate::mapSharedMemory: Opening cache "/var/tmp/kdecache-scarab/icon-cache.kcache" page size is 4096
(4250) KSharedDataCache:rivate::mapSharedMemory: Attached to cache, determining if it must be initialized
(4250) KSharedDataCache:rivate::mapSharedMemory: Cache fully initialized -- attached to memory mapping
(4250) KSharedDataCache:rivate::mapSharedMemory: 4366336 bytes available out of 10485760
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/scarab/.config/ibus/bus
Busen: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon
Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=mdns)
error: No devices found on bus: net

when trying to make uri:

scarab@scarab-laptop1:~$ hp-makeuri 192.168.0.143

HP Linux Imaging and Printing System (ver. 3.10.6)
Device URI Creation Utility ver. 5.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Device not found

hpcheck-r with one only error:
Printer Ready to print. HP_LaserJet_M1536dnf_MFP is idle. enabled since Fri 01 Apr 2011 10:05:10 AM AMT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

how to install it in hplip if it keeps being undetected with hp-setup? tried to remove it from printer configuration and the same occurs.

thanks in advance for possible solutions

F

---

