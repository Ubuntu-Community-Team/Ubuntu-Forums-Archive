---
title: "flash trouble after upgrade"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Bigneil on 2009-11-08
i just upgraded to karmic from jaunty. ... i have 64 bit machine i was using 64 bit jaunty, does the upgrade from 'system update' upgrade to 64 bit from 64 bit or does it do 32 bit by default???  if so, it might explain my flash player being all screwd up??  any advice would be welcome,,, also, is it possible to roll back to previous version ???

---

### Post by QIII on 2009-11-08
If you were running 64 bit Jaunty, you would have upgraded to 64 bit Karmic.  32 bit is not the default.

Could you elaborate further on "screwd up"?

---

### Post by Bigneil on 2009-11-08
thanks for your reply,  the web browser crashes and closes down upon attempting a youtube video or flash game on facebook.

---

### Post by Bigneil on 2009-11-08
oh yea... i also tried to re-intall 64 bit flash but there was an error, i cant remember what it was now but i could have another go and take a screen shot?

---

### Post by QIII on 2009-11-08
Open Firefox and type about(colon)plugins in the nav bar.

Could you C&P the flash portion here?

And yes, let's see the screen shot with the error.

---

### Post by Bigneil on 2009-11-08
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes



is this what you needed to see?

---

### Post by Bigneil on 2009-11-08
i notice it says r32 after the flash version.. is this the culprit?

---

### Post by QIII on 2009-11-08
Yes.

Next step:  Can you go to Synaptic and tell me if you have swfdec or gnash installed?

If you do, mark them for removal and uninstall them.  Some people have had problems if they "Mark for complete removal", so don't do that.

If you installed Flash from Adobe's website, you may need to follow the uninstallation instructions before attempting to reinstall.

Edit -- Re: "r32".  No.  That indicates "release 32", not 32 bit.

---

### Post by Bigneil on 2009-11-08
none are ticked off as far as i can tell...i took a screen shot.

i think i installed flash from a command i pasted into the terminal nonfree i think... is it possible that my firefox is 32 bit aswell? would that even run on 64?

---

### Post by QIII on 2009-11-08
The flash plugin-nonfree installer should install the non-free (read "proprietary") flash.  If you ininstall the installer, you won't uninstall Flash, so there is no point in uninstalling it.

Could you do a search of your file system and find out all the places where "libflashplayer.so" lives?

You may also be running into a problem with profiles.  Karmic installs the branded Firefox rather than Shiretoko, and it uses a profile in ~/.mozilla/firefox rather than Shiretoko's ~/.mozilla/firefox 3.5 (or whatever it was).

If you did an upgrade rather than a fresh install, you may have two profiles.  Don't get rid of either one, since you may want the contents.  But let me know if you have two folders... ~/.mozilla/firefox and ~/.mozilla/firefox 3.5.

---

### Post by Bigneil on 2009-11-08
i'm not finding the firefox folders where would they be?   here is the search results from.... where "libflashplayer.so" lives

---

### Post by Bigneil on 2009-11-08
should i try to install the Shiretoko and uninstall the branded? then re-install the flash player?

---

### Post by QIII on 2009-11-08
If you are running Karmic, you want the branded version.  Shiretoko was a stop-gap.
 
 Your libflashplayer.so files are placed so that they can be accessed by anyone on the machine, which is probably better than having them in an individual profile folder anyway.  Unless your upgrade created some sort of permissions issue.
 
 Let me think about this for a while.  I'm going to fiddle around on one of my other machines and see if I can come up with an answer.

I suspect someone will come along while I am doing that and, recognizing what a dolt I am, give you a much easier solution right off the top of his head.

Alas.

---

### Post by Bigneil on 2009-11-08
LOL, thaks for your time, you have gotten farther than i did with it.  i have not customized or set up too much stuff on here.... i could fresh install from a carmic cd as long as i am 90% sure that things would come good easier that keeping my current one and finding a solution or workaround.... i will sleep on it.  c](*,)

---

### Post by QIII on 2009-11-08
I am reluctant to just say "Install it clean", although I think it is generally accepted as the best solution and I usually do it that way.

I keep a separate /home partition, make a back up, do a fresh install without touching my /home partition, dpkg my saved .debs and just move on.

Have have very few problems going that route.  Anything I don't like is generally easy to fix by importing a file or profile back from the contents of my saved /home partition.

But if you do decide to reinstall, save your /home file (if it is not in a separate /home partition) to some place you can get at it afterwards.  You can still use it to build the contents of a /home partition if you do your partitioning that way in your initial reinstall -- which I HIGHLY recommend.  It makes clean installations of new versions a lot easier!

---

### Post by paxmark1 on 2009-11-08
I updated and kept getting the npviewer.bin crashes.  Strange, I thought I had 64 bit flash.

There are several good references in the forums, but the one I liked best was elsewhere.

[www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit](www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit). html -              nice little bash script

but that was not enough for me.

sudo updatedb
locate libflashplayer.so

and then I used a file manager (actually sudo mc) to look at the sizes and date stamps of all the locations of libflashplayer.so

  Whole lot of symlinks.  I  did rm to all that were the 32 bit version, and voila, youtube works for me.  

peace   mark

---

### Post by Bigneil on 2009-11-08
> **paxmark1 said:**
> I updated and kept getting the npviewer.bin crashes.  Strange, I thought I had 64 bit flash.

There are several good references in the forums, but the one I liked best was elsewhere.

[www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit](www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit). html -              nice little bash script

but that was not enough for me.

sudo updatedb
locate libflashplayer.so

and then I used a file manager (actually sudo mc) to look at the sizes and date stamps of all the locations of libflashplayer.so

  Whole lot of symlinks.  I  did rm to all that were the 32 bit version, and voila, youtube works for me.  

peace   mark

I can't open your link.. firefox just closes down

---

### Post by Bigneil on 2009-11-09
ok i have dedcided to do a clean install of carmic from cd...

---

### Post by Bigneil on 2009-11-09
success, including 64 bit flash

---

