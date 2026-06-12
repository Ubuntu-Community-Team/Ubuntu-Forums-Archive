---
title: "Notebook woes with 5.10 live cd"
date: 2005-11-24
forum: General Help
---

### Post by Tunnelrat81 on 2005-11-24
My questions are reguarding my attempt to successfully load live cd's onto both my powerbook pismo as well as a friends old Dell Inspiron 5000.  The problems that I've had with both are similar but I'm not sure they're the same.  

The pismo problem is VERY similar to what I describe below for the Dell (the only difference being some functionality out of the dell, while the mac is completely unusable until I kill it with the power button.  But I've asked about it in the mac section (so far with no help) so I'm asking here about the Dell.  Booting the live cd seems to work flawlessly until I get into gnome, where the loading time is VERY long followed by 100% CPU usage indicated by the system monitor.  This 100% usage conitues indefinitely with NO windows/applications etc...running.  JUST the desktop, running at max cpu.  Naturally the notebook is nearly unusable during this time i.e. it takes quite a long time simply to open the system monitor.  

Both notebooks are of similar cpu speed and each one has 128 Mb Ram.  They also are both using some flavor of ati graphics card.  I believe the psimo has an 8 MB ATIRage M3 card, and the Dell is another ati card.  

In both cases the cdrom is very active (on the mac indefinitely it seems) during the gnome bootup and applet loading stuff.  My tendency is to think that it is a graphics setup or xorg.conf problem that I've got, but I haven't been able to make any progress.  In both cases having run "live-expert," the autodetect function for graphics card finds and identifies the ati card by its model name, but then somethings not working, so that remains a possibility.  

I'd appreciate any help I could get reguarding this/these problems as I've got a perfectly working install on my Desktop pc.  I also wonder if these same  problems would be likely following a FULL installation rather than booting the live cd.  

-J

---

### Post by SuperMike on 2005-11-24
So the short of this is that you've got a Mac and a Dell laptop, and two kinds of Ubuntu Live CDs. You want to install the OS but are extremely conservative and want to test the OS with the Live CDs first. You tried the Live CDs but it seems to be hung or really, really slow. The other odd thing is that you seem to have struck the odd chance that the problem is *also* occurring in *both* your Mac and your Dell.

Hmmm. If it were me, I'd be thinking bad ISO images. Did you get these discs from Canonical (ship-it) or did you download and burn the ISO images yourself? The other rare occurrence could be defects in the CDRs that Canonical used. Do you see defects or scratches? Or perhaps they were damaged in shipment or flexed (bent slightly)?

Now let's say the Mac isn't an issue -- just the Dell laptop, or vice-versa. In that case, I would be thinking that something was up with swap space, meaning that it has to do a ton of paging in a very tiny swap space. Or perhaps you had a defect in RAM or the hard drive bytes, causing some amount of bytes to be out of whack. But that doesn't appear to be your case.

---

### Post by Tunnelrat81 on 2005-11-25
What you said is true.  I have a perfectly working install of breezy on my desktop pc and a perfectly good install of OSX on my mac laptop.  Both functioning, but I'm not the most aquainted with mac OS nor am I too interested in getting to know it especially since getting more aquainted with Linux and enjoying it as I do.  The iso problem is one that I suspected right off the start however, with regards to the mac ppc live cd.  I also found on the forums a similar problem in the ppc section that suggested that the problem was breezy related and that the user was able to reinstall hoary and get all performance back.  I immediately downloaded the hoary live iso and burned it, coming up against the very same problem.  I wish it was something that easy.  And its possible that I'll simply have to commit to a real install and hope that I don't get stuck (with the mac, that is).  The old Dell isn't mine to install to, so that likely won't get much further attention.  Thanks, and drop in with some more suggestions if possible.

The extremely conservative part is, well not totally true.  My single concern is that I won't be able to get the laptop set back up with ubuntu for the ability to play dvd's and music.  Thats ALL I use it for right now, but would like to be able to use it for some more advanced remote access etc.....with my pc.  Plus, since i'd rather further my ubuntu experience before expanding to OSX use, the movie/music concern is my only reservation.  

-J

---

### Post by Tunnelrat81 on 2005-11-27
I'm just following this post up with a note that the Dell laptop was given to me (interestingly enough, it was deemed useless to my friend, and handed over) so I immediately installed ubuntu on it successfully and everything seems to be up and running.  Apparently it was a 'live cd' specific problem that I no longer need to worry about.  With this new laptop running ubuntu, I can leave osx on the Mac laptop and not worry making that one work.  Thanks for your response, and have a good day.

-J

---

