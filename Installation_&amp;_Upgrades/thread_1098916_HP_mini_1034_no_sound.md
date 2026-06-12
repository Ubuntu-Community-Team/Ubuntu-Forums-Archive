---
title: "HP mini 1034 no sound"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by m626rider on 2009-03-17
Today I Installed Ubuntu 8.04 on a HP mini 1034 but can't get any sound out of the speakers. I can get sound from the headphones which is just driving me crazy.

---

### Post by otchster on 2009-03-28
I have the same problem with my HP Mini 1000.

---

### Post by Ubuntiac on 2009-03-30
*sigh* Same here... I was just surfing looking for an answer to this for my 1010NR...

EDIT: Gohai reported getting his to work with the newer 1.0.19 ALSA driver. There's a PPA listed for it at the end of [this big report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/"). (Subscribe and choose "This bug affects me" up the top while you're there).

---

### Post by m626rider on 2009-03-30
Loaded version UNR V.8.04 and sound worked on HP mini 1034.

---

### Post by otchster on 2009-03-31
I am using Jaunty v9.04.  No sound on a HP Mini 1000.

---

### Post by gsaito on 2009-06-16
HP Mini 1035NR with Ubuntu Netbook Remix 9.04: Headphone works OK but no sound on speakers.

All the other hardware appears to be working OK.

---

### Post by aysiu on 2009-06-16
I created a special remix of Ubuntu 9.04 that includes sound fixes:
[http://www.psychocats.net/hpminiremix](http://www.psychocats.net/hpminiremix)

I hope that helps. If not, you can do the sound fixes yourself, but it's a bit tedious:
[http://www.psychocats.net/ubuntucat/vanilla-ubuntu-on-the-hp-mini-1120nr/](http://www.psychocats.net/ubuntucat/vanilla-ubuntu-on-the-hp-mini-1120nr/)

---

### Post by bluedragon436 on 2009-07-21
Hey aysiu...  I tried to follow your page at: [COLOR="Red"][http://psychocats.net/hpminiremix/]("http://psychocats.net/hpminiremix/")[/COLOR]  Where it says to paste: sudo m-a a-i alsa-source in the terminal... when I do that it says [COLOR="Red"]sudo: m-a: command not found[/COLOR]    what am I messing up on here???  Everything else seems to be working awesomely except the sound...  just trying to get this worked out before I head down range in a month with this laptop...  Thanks again, and I am loving the remix on my netbook...

I tried to shoot this to you in a PM, but said you had exceeded your limit...  Thanks for your help!!
James

---

### Post by aysiu on 2009-07-21
> **bluedragon436 said:**
> Hey aysiu...  I tried to follow your page at: [COLOR="Red"][http://psychocats.net/hpminiremix/]("http://psychocats.net/hpminiremix/")[/COLOR]  Where it says to paste: sudo m-a a-i alsa-source in the terminal... when I do that it says [COLOR="Red"]sudo: m-a: command not found[/COLOR]    what am I messing up on here???  Everything else seems to be working awesomely except the sound...  just trying to get this worked out before I head down range in a month with this laptop...  Thanks again, and I am loving the remix on my netbook...

I tried to shoot this to you in a PM, but said you had exceeded your limit...  Thanks for your help!!
James
**Step 1:**
Go to System > Administration > Software Sources and make sure the third-party source *deb [http://ppa.launchpad.net/minichoco-team/ppa/ubuntu](http://ppa.launchpad.net/minichoco-team/ppa/ubuntu) jaunty main* is enabled.

**Step 2:**
Reload when prompted.

**Step 3:**
In System > Administration > Synaptic Package Manager, make sure *alsa-source* and *module-assistant* are installed.

Then try the command again.

---

### Post by bluedragon436 on 2009-07-22
I don't have the [http://ppa.launchpad.net/ninichoco-team/ppa/ubuntu](http://ppa.launchpad.net/ninichoco-team/ppa/ubuntu) jaunty main or anything close to it..  I only have [http://acrhive.canonical.com/ubuntu](http://acrhive.canonical.com/ubuntu) jaunty partner and the same thing with (source code) at the end...  this might be part of my issue I guess... how do I go about getting that???  I am currently installing the also-source, but I did have the module-assistant...  once I install the also-source will that remedy the above stated missing third-party source deb??

---

### Post by aysiu on 2009-07-22
Yeah, if that PPA isn't enabled, go ahead and add it by going to System > Administration > Software Sources > Third-Party Software > Add and then pasting it in.

---

### Post by bluedragon436 on 2009-07-23
Ok so I tried to cut and paste the ppa into the third-party like you said, and it gives me an error when I say reload that says

Failed to fetch [http://ppa.launchpad.net/ninichoco-team/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/ninichoco-team/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages)   404 Not Found
Some Index files failed to download, they have been ignored, or old ones used...  


am I doing something wrong here??   I am still learning the ins and outs of Linux, but am getting my ***** kicked on this one...  Is this maybe something I should start with a fresh install of Ubuntu again??  I have also tried to do the ppa mentioned on pg 1 of this thread... and got a different error..  I am currently trying to reinstall it completely, and will then follow your instructions to see what I get...  Is there a better version than the one I can get form the Ubuntu site, that might not have this issue??  I couldn't find the one you said you had that had the fixes already completed...  I think I already found it, but just in case if you could get me a link so I make sure I get the correct download before I waste any time...  I did try and re-install the version of the Remix that I got from the Ubuntu site last night, with no success with it allowing me to make the proper changes needed for the sound to work... everything else is grand and all I got left to fix is the sound... and I want to get it fixed soon, or I will have to revert back to Windows before I roll out for this deployment... which I really don't want to do!!

---

