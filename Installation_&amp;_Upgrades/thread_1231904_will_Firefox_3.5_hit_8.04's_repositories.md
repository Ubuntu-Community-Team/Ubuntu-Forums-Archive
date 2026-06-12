---
title: "will Firefox 3.5 hit 8.04's repositories?"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by TimDaniels on 2009-08-05
Firefox 3.5.1 has been out for a few weeks, but
the repositories for Ubuntu 8.04 only have Firefox
3.0.12.  Is that the end of the line for Firefox in
Ubuntu 8.04, or will Firefox 3.5.1 eventually find
its way into 8.04's repositories for the Update
Manager to find?  (I don't want to get into doing
terminal commands for apt-get to do this.)

If I download and somehow get Firefox 3.5.1 to install
itself, will this somehow confuse the Upgrade Manager
so that it tries to upgrade to Firefox 3.5.1 later
(if and when Firefox 3.5.1 enters the repositories)?

*TimDaniels*

---

### Post by aysiu on 2009-08-05
Firefox 3.5.2 will never hit the 8.04 repositories. You may be able to add in through a PPA some form of it called Shiretoko, but it won't be the default Firefox, and it may not work for some sites that require a user agent string that identifies as Firefox.

If you want Firefox 3.5.2 in Hardy, this is the best way to get it:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

And it will not interfere with the regular update manager Firefox.

---

### Post by TimDaniels on 2009-08-05
> **aysiu said:**
> Firefox 3.5.2 will never hit the 8.04 repositories. [...]
If you want Firefox 3.5.2 in Hardy, this is the best way to get it:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

And it will not interfere with the regular update manager Firefox.

Thanks for the info and link.

*TimDaniels*

---

### Post by c-cube on 2009-08-12
[QUOTE=aysiu]Firefox 3.5.2 will never hit the 8.04 repositories.[/QUOTE]

I'm very surprised, for Ubuntu documentation says the contrary [here]("https://help.ubuntu.com/community/FirefoxNewVersion").

> Hardy and Intrepid

Please check back here in a few days.
**The Ubuntu Mozilla Team is working to make Firefox 3.5 available for older releases. **

When you have installed the new package, a new icon will appear in Applications > Internet alongside your old Firefox icon. The name is based on the codename for the new Firefox release, so Firefox 3.5 was labelled Shiretoko Web Browser. 

---

