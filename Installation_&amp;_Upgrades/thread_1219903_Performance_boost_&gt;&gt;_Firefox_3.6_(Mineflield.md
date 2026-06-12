---
title: "Performance boost &gt;&gt; Firefox 3.6 (Mineflield) for Ubuntu (Hardy or Jaunty)"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by cb2410 on 2009-07-22
Tired of the slow Firefox 3.0 performance under Ubuntu? Want to test the performance of Firefox 3.6 under Ubuntu? I can recommend to install Firefox 3.5 (Minefield) beside Firefox 3 so you can *test* and compare the latest version.It's a lot faster with loading flash pages like Youtube. 



**Step by step walk-through-installation for Ubuntu 9.04 [SIZE=4]_Jaunty_[/SIZE]**: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2a1pre) Gecko/20090721 Ubuntu/9.04 (jaunty) Minefield/3.6a1pre

**Hardy Heron** User need to use this apt sources
```

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) hardy main

```
[B]Latest info: PPA for Ubuntu Mozilla Daily Build Team
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")
[/B]

 
**Step 1. **Copy the *apt sources* 1
```

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main 

```**Step 2:** On your Ubuntu computer, open *System > Administration > Software Sources*.

**Step 3:** Click the *Third Party Software* tab.

**Step 4:** Click the *Add* button.
     [B]
Step 5:[/B] Paste the line you copied in step 1 and click the *Add Source* button.     
[B]
Step 6:[/B] Copy the *apt sources* 2
```

deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main 

```[B]

Step 7: [/B]Click the *Add* button again inside Software Sources (Step 4) 

**Step 8:** Paste the line you copied in Step 6 and click the *Add Source* button.     

**Step 9:** Close *Software Sources*;  When prompted, **reload** the software sources information. Don't worry if you see a warning about unverified software sources; we're going to fix that next.

**Step 10:** Open your Terminal and copy/paste the Key ID
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE

```**Step 11:** Finally, tell Ubuntu to re-load the details of each software archive it knows about:

```

sudo apt-get update

```[SIZE=3]Starting the new installed Firefox browser:[/SIZE]
If everything worked correctly you should have a new menu entry under: 


Application / Internet - Minefield 3.5 Web Browser (The Bleeding Edge)

If you cannot see a new entry do this:

Application | Add/Remove

Search and add  --> **Shiretoko**

Now the new entry should be there :D

Enjoy

----

---

