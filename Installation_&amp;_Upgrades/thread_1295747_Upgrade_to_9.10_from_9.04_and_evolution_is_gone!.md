---
title: "Upgrade to 9.10 from 9.04 and evolution is gone!?"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by nurvzy on 2009-10-19
So, I decided to upgrade to the latest realease a bit early because I wanted to use eclispe 3.5 for some new projects I'll be working on and to my dismay when I came back I noticed evolution wasn't installed anymore.

So I load a terminal and try:
```
sudo apt-get install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  evolution: Depends: evolution-common (= 2.28.0-0ubuntu4) but it is not going to be installed
             Recommends: evolution-documentation (= 2.28.0-0ubuntu4) or
                         evolution-documentation-en (= 2.28.0-0ubuntu4) but it is not going to be installed
E: Broken packages
```So I install evolution-common and evolution-documentation-en and try again but get the same message.

Am I missing a repository I should be pulling from?

I've done a fair share of checking the internet for an answer to my question, with no luck.   Am I just SOL until the official release comes out?  Or is there something more I can do?

Please, any advice is appreciated.

Thanks,
Nick

---

### Post by mikewhatever on 2009-10-19
How to fix a broken package [https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by nurvzy on 2009-10-19
Thanks for the quick reply.

When I open up synaptic I don't actually see any broken packages listed (in the statusbar it says 0 broken packages).  Evolution just isn't installed and it refuses to install it even though I have what it considers the dependancies.  But I followed your link (thank you for providing) and followed the instructions.

That didn't seem to do anything.  I click Edit -> Fix Broken Packages.  I wait a few seconds and I see "Successfully fixed dependency problems" near the bottom.  Although I didn't have any broken to begin with.

So I try and install evolution again and I receive the same error as above just this time in a window and "Broken Packages" is excluded.   

I try "Fix Broken Packages" for good measure, and try to install evolution to no avail.

What would you try next?  I'm a bit stumped.

---

### Post by nurvzy on 2009-10-20
I figured it out (with some help of a linux guru).  Had to re-enable pre-release repository on my sources list.  evolution installed fine after that.

Hope that helps someone else.

---

### Post by feriender on 2009-10-31
You may experience problems when you are trying to 'Restore settings' in Evolution 2.28.1.

If the backup file 'evolution-backup.tar.gz' is stored on an external device (ex. pendrive), the restoring fails immediately. 

Solution: copy the backup file to your /home folder, and try again with Evolution.

---

