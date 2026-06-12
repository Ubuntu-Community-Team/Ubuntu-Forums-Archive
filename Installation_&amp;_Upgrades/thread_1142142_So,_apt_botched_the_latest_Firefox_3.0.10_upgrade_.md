---
title: "So, apt botched the latest Firefox 3.0.10 upgrade for me..."
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Kareeser on 2009-04-28
... and what a bad time for it to do so! I was just paying off my VISA, and I was about to press "submit", when my laptop hardlocked. :(

So, one Alt-SysReq-REISUB later, and I was back in business... except...

```
julian@julian-4:/usr/bin$ which firefox
/usr/bin/firefox
julian@julian-4:/usr/bin$ cat /usr/bin/firefox
julian@julian-4:/usr/bin$ 
```
[size=1](Likewise, /usr/lib/firefox-3.0.10/firefox.sh was empty)[/size]

Weird.

No matter what I tried, I just COULDN'T get apt to repair firefox! I'm thinking that it botched itself during the update...

I've tried:
```
sudo apt-get remove firefox
sudo apt-get purge firefox
sudo apt-get autoremove firefox
sudo apt-get -f install firefox

```

Nothing works... it's as though /usr/lib/firefox-3.0.10/ is untouched after each of those commands!

I only managed to get back here because I ran an apt-cache search for "firefox" and installed Shiretoko (which is the codename for Firefox 3.5)

Any suggestions on getting firefox 3.0.10 back? No rush, I'll try out this beta :)

---

### Post by nivek1385 on 2009-04-29
I had issues with FF have upgrading to 3.0.10...whenever I tried opening it up after the upgrade, it would launch a window without the FF icon (just a generic icon) and would only have the title bar with a gray window and nothing else.  Come to find out, FF didn't shut down properly prior to the update, and was still running in the background.  Once I killed the FF process and tried again, that solved my problem.

---

