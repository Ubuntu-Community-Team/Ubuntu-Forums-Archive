---
title: "How to install firefox 3.5 in jaunty?"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by H.K.Murmu on 2009-07-08
How to install/upgrade firefox 3.0 to 3.5

I am now running firefox3.0 but newer version 3.5 is avilable.I have downloaded it and installed. But firefox is not upgraded. I have also checked in repository but 3.5 version is not available in repository.

So how can I upgrade firefox.
Please help me

---

### Post by masux594 on 2009-07-08
Just search in the forum, don't open a new thread when there is no need!

Sysc, A

---

### Post by tacantara on 2009-07-08
I just read a thread on Firefox 3.5 now appearing in the repos.  It installs as Shiretoko (the "working title" for FF 3.5) and shows up as such in your programs menu.  Sorry I don't have a link to that thread, but you should be able to search for it easily enough.  Good luck :)

---

### Post by starcraft.man on 2009-07-08
Firefox is in the repositories, the package is named simply *firefox-3.5*. It installs to the internet section of applications, it will be named shiretoko, but it is firefox 3.5. Shiretoko was the code name for development.

If you need help installing, see my signature.

Note: Please search in future, lots of these...

---

### Post by Brandon Williams on 2009-07-08
```
sudo apt-get install firefox-3.5
```

The released version is in the standard repos for those with universe enabled. It still calls itself shiretoko, but that's just so that it will install alongside firefox-3.0 more easily.

---

### Post by t0p on 2009-07-08
> **starcraft.man said:**
> 
Note: Please search in future, lots of these...

To be fair to the OP, this site's search function is crap.  I recommend that people use google to search these forums.  You can do this by adding to your search terms the following string:

```
site:ubuntuforums.org
```

If you add that to your search terms, google will produce results only from this site.  So the OP could have used google and got [these results]("http://www.google.co.uk/search?hl=en&q=install+firefox+3.5+site%3Aubuntuforums.org&btnG=Google+Search&meta=&aq=f&oq=").

---

### Post by JohnLau on 2009-07-09
You can follow my guide:
[http://compustorm.no-ip.org/2009/07/howto-install-firefox-3-5-on-ubuntu-jaunty/](http://compustorm.no-ip.org/2009/07/howto-install-firefox-3-5-on-ubuntu-jaunty/)
;)

---

### Post by asforme on 2009-07-09
Okay, so this installs along side 3.0, is there any way to upgrade the firefox installation instead?  Or at the very least, set 3.5 to be my default browser so links in IM open in 3.5 instead of 3.0.  Going into preferences in 3.5 and click "check now" to check if it's default seems to do nothing.

---

### Post by H.K.Murmu on 2009-07-09
thanks for suggession

---

### Post by JohnLau on 2009-07-09
> **asforme said:**
> Okay, so this installs along side 3.0, is there any way to upgrade the firefox installation instead?  Or at the very least, set 3.5 to be my default browser so links in IM open in 3.5 instead of 3.0.  Going into preferences in 3.5 and click "check now" to check if it's default seems to do nothing.

That's easy. You can set it in in System --> Preferences --> Preferred Applications 
Then Click 'Custom' instead of firefox
After that, use
```
firefox-3.5 %s
```
for the command
This should work!
John

---

