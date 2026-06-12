---
title: "Switching from Mandriva questions"
date: 2009-03-10
forum: Hardware
---

### Post by renichms on 2009-03-10
I have a Compaq Presario CQ60-215DX laptop.  Right now, it is running Mandriva.  I ran KDE on it until Dolphin bombed.  Switched to Gnome.  There are now several other problems.  Konqueror will no longer connect to SMB shares and Firefox (and other apps) still lock up the entire system when trying to select a new place to download files to or when selecting a file to attach (in webmail, for example).  I've played with Ubuntu and not had these issues.

And so that brings me to my question(s).  Once I have backed up all the data I want to keep, if I do a clean install of Ubuntu 8.10 on my laptop, if it does not pick up the nVidia proprietary drivers or the wireless drivers, how can I tell it where to find them?  In Mandriva it was going to the central control panel and checking the box for proprietary drivers.  Basically, getting the kind of resolution I have now is the biggest issue I want to have settled before I do anything.  Does anyone here know if KMail can export in a format that something like Evolution could import?  Will Windows XP start like normal in VirtualBox if I just copy the virtual HDD off this computer and then back in when Ubuntu is on and has VirtualBox?

Does Ubuntu have any known issues like what I am experiencing?  As far as I know, Nautilus is stable and SMB shares can be mapped out, and I have yet to see Firefox bomb in such a way.

RN

---

### Post by arubislander on 2009-03-10
Ubuntu should let you know that there are appropriate drivers available via a notification on your desktop. If you don't see that immidiately you could always check under System->Administration->Hardware Drivers

The wireless drivers could be an issue... I've always found that Mandriva's support for these is better than Ubuntu's, but with some perseverance and help you will get them working. Our you could be fortunate and installing them will be just as easy as installing the nVidia drivers.

Your virtual HDD should work if the version of VirtualBox that you use in Ubuntu is the same or greater than the one you used in Mandriva.

Everyone's experience with Ubuntu is different but I trust that you won't be expierencing the issues you mentioned. But then again most Mandriva users don't either I suppose.

---

### Post by renichms on 2009-03-10
So basically, I just need to back up all my data, install a fresh copy of Ubuntu, then have it hooked into the network (wired) to make sure and get all needed updates and proprietary drivers.  Once it's confirmed working with the nVidia card and wireless NIC, make sure the new install has all the software I'll be using and then move data back over and test what needs it (importing email, test virtual HDD to be sure it all goes well before needing it).  Straight-forward enough rebuild.  Hopefully there will be no issues.  Probably will be doing this starting Friday afternoon.

RN

---

### Post by renichms on 2009-03-11
Well, I got my data backed up and jumped early.  nVidia driver is installed and working.  Unfortunately, Ubuntu says the wireless driver is installed and working but it is not.  It refuses to recognize any networks, even if I manually put in the info.  One search told me wicd would work so followed their directions and wicd is actually less helpful.  In addition, I cannot find how to get Compiz going so I can keep the old effects I had (and liked).

So...any suggestions on getting back to Network Manager and on getting my Compaq's Atheros wireless card running?  Any suggestions on Compiz?

RN

EDIT:  Went through Synaptic Package Manager, killed wicd, added something for Atheros, rebooted and it's working now.  Off to search for Compiz...

EDIT2:  More hyper editing time...  Okay, trying to get OpenOffice.org 3.0 but the problem is when I go to add the key, I can't browse to the folder and it won't let me type it in manually.  Once I can browse, I can add all the software I need, update everything and put my data back on the computer.  Any suggestions?  (Trying to search for a fix but wireless is becoming spotty [someone is looking into adding another AP right now but for the time being I do not have a reliable connection] so may not be able to do it myself.)

---

### Post by arubislander on 2009-03-12
Had any luck adding the key to install Oo.org 3?

---

### Post by renichms on 2009-03-12
No.  Ubuntu refused to connect to wired or wireless networks so I had to wipe it and go back to Mandriva.  So far, I have learned Ubuntu is very very bad at networking in general (absolute failure on 4 computers so far).  Mandriva has a bug that crashes whole systems that no one has done anything about for over a year.  Fedora can't install.  Debian and openSUSE I will have to look into more.  I have a pretty generic PC laptop and I just need a system that will network (wired and wireless, consistently) and that doesn't have whole system locking bugs that prevent it from being used to its fullest.

And, sadly, I had to get out a really long cable to get Mandriva to connect because for some reason it absolutely refuses to do wireless right now even though it did not 10 minutes ago.  I really hate Windows but this week, Linux is REALLY trying my patience.  For sanity, I'm probably buying a Mac next time.

RN

---

### Post by arubislander on 2009-03-13
I feel your pain.

Getting wireless to work can be trying at times. And you must really have an incentive to get it to work when things don't go as smoothly as with That Other OS...

I remember spending the best part of a month in getting the wireless to work on my father's laptop. Time was running out on me since I was on holiday... I think he had an atheros wifi too. Don't actually remember what got it working at last though... But I have found that helping to get wifi to work helping someone long distance is quite a challenge.

If you should ever try to get wifi working with Ubuntu again, I'll see if I can help some.

(BTW. I did get my dad's wifi working)

---

### Post by renichms on 2009-03-13
I probably came across as a  bit rude in last post...sorry about that.

I've got Vista on the laptop again.  I'll set it up to dual boot some time in the next week or so.  I prefer Linux but it's maddening how inconsistent it is.  I went through the SAME steps to get wireless working on Ubuntu again...and it didn't work.  Even Mandriva, the networking marvel, just stopped working with wireless.  I even switched from dhclient to dhcpcd since I had issues with that a while back.

I suspect if I give it a few more years, Linux will become practical for a laptop but I can't afford most of a week of downtime for every 2 months of use.

Now, for desktops and servers, Linux is the operating system of choice.  I can then build a system how I want and guarantee all the parts I choose to use are compatible with my Linux system(s) of choice.  As for laptops, it'll be Apple for my next one (it was going to be an Apple anyways).  Though, if I get an Eee PC laptop, it'll run Eeebuntu.

RN

---

