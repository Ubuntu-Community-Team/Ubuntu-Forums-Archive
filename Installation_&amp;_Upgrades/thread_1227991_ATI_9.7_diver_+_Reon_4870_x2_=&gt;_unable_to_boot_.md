---
title: "ATI 9.7 diver + Reon 4870 x2 =&gt; unable to boot normaadl"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by bartvanp on 2009-07-31
When I install the ATI proprietary driver my system isn’t booting normal anymore.
   
  During startup the Ubuntu loading screen turns blurry in strange colors with the Ubuntu logo somewhere in the corner of the screen in pink. The system is not responding anymore at all.
   
  I tried some things to fix the problem. 
  - From the recovery menu the restore option
  - aticonfig --initial
  - delete the xorg.conf file
  Etc.
   
  Nothing worked and I ended up with a system only booting into one big grey doted screen with some horizontal lines in it.
   
  After a new clean installation of Ubuntu the problems where over as long as I didn’t try to install the proprietary driver. Today I saw that there was a new driver available from ATI (9.7) so I tried it again. But with the same results. I get really tired of backing up my data with a live cd and reinstalling Ubuntu, so I really want to solve the problem this time without doing this.
   
  I spend some hours reading Ubuntu help forums, and although there seem to be a lot of people with ATI driver problems I didn’t find a solution for my problem.
   
  Is there anyone out here who has a clue what I can do to make the driver work?
   
  Or maybe I can better ask: does anyone know how I can uninstall the ATI driver, and activate the build in driver of Ubuntu from the command line?
   
  My configuration: ATI Radeon 4870 X2, Samsung 24” SyncMaster, Ubuntu 9.04 64bit, Latest ATI driver (9.7).

---

### Post by sackbj on 2009-07-31
I was having the same problem you were with an ATI Sapphire Radeon HD 3870 X2.  I tried everything I could find on the internet, including several walkthroughs and programs like Envy.  Nothing worked.  Eventually I went to ATI's site to download the drivers directly.  I read the release notes and they state specifially that the HD 3870 X2 does not have Linux support.  That's a huge bummer considering how much I spent on the card at the time.  I'm all nvidia now - never going back to ATI.

I am not sure if you will have similar issues witht he 4870 X2, but you might want to take a look at the release notes for their drivers and see what you can find.  Good luck.

---

### Post by bartvanp on 2009-07-31
I checked the release notes and my card should be supported by the driver.

---

### Post by bartvanp on 2009-07-31
Ok, I found a way to get rid of the ATI driver: sudo apt-get remove xorg-driver-fglrx

---

