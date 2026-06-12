---
title: "Installing iTunes that ****WORKS****!!!"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by krejustin on 2009-09-08
Good luck
 Summary:
sudo apt-get install wine
winecfg
 I cd into my Desktop (just to SEE the file I was about to download, but it is not necessary
 wget [http://appldnld.apple.com.edgesuite.net/content.info.apple.com/iTunes7/Win/061-4476.200402.tGbhu/iTunesSetup.exe](http://appldnld.apple.com.edgesuite.net/content.info.apple.com/iTunes7/Win/061-4476.200402.tGbhu/iTunesSetup.exe)
 wine iTunesSetup.exe (here is where it hanged up, give it some time, but if it fails just close the terminal window)
 wine ~/.wine/drive_c/Program\ Files/iTunes/iTunes.exe (and fill yourself with patience) 
 Good luck

---

### Post by jakwriter on 2010-01-31
Could you get a little more exact on these directions?  For example, what version of Ubuntu are you running?  Is that the latest version of iTunes?

I ask because everything worked up to the actual installation.  The wizard runs and then I get 

[I]The installer encountered errors before iTunes could be configured.
Your system has not been modified.  To retry these operations at a later time, please run the installer again.[/I]

No iTunes . . . 

I've tried using an older version of iTunes 7.0, 7.7, same story.

Any ideas?

---

