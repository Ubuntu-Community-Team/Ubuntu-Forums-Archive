---
title: "Resume 9.04 Upgrade after Crash?"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by dedukes on 2009-07-08
Hi.  My laptop's battery died (sigh, i forgot to plug it in) during an upgrade from 8.10 to 9.04.  The screen goes blank after I log in.  But when I run it on a 9.04 LiveCD it seems to work perfectly.  I've backed up my home folder.

There's a terminal command for resuming upgrade, yes?  Apt-get, I think? When I boot off the hard drive and go into the terminal I have no internet access, so I can't resume the upgrade in the terminal.  Internet access is fine running off the LiveCD.  Is there a way to resume upgrade while using the LiveCD?

I'd rather not have to do a clean install.

Thanks.

---

### Post by prshah on 2009-07-08
> **dedukes said:**
> Hi.  My laptop's battery died during an upgrade from 8.10 to 9.04.  The screen goes blank after I log in.

There's a terminal command for resuming upgrade, yes?  

I'd rather not have to do a clean install.


Hi I had a similar problem; see my [post and solution]("http://ubuntuforums.org/showpost.php?p=4872499&postcount=1").

Summary:```
dpkg --configure -a
```
> Considering the magnitude of the disaster, I was sure that I'd have to reinstall, but there was no difficulty at all; hardy recovered nicely inspite of an interrupted upgrade.

Though this is for Hardy, it should work just as well for Jaunty.

---

### Post by dedukes on 2009-07-08
thanks, prshah!  i hope you're right.  i'll give it a try.

---

### Post by dedukes on 2009-07-08
Okay, I ran "dpkg --configure -a" and that seems to have done the trick!  phew, this marks the (apparent) end of several days of wrestling.  

The only glitch is that I have to get an internet connection through ethernet connection.  I can see all available wireless networks, but when prompted for the password to log onto my wireless network the "connect" button is dimmed (even after I enter the password).  I'm guessing this is an unrelated issue and I'll trying searching for answers elsewhere.

---

