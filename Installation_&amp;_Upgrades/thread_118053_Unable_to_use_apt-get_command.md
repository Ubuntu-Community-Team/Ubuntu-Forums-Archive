---
title: "Unable to use apt-get command"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by StevenKannel on 2006-01-16
Hello all,

I am fairly new to Linux and particularly new to Ubuntu.

To make a long story short, I am a student at a university with strict network rules.  In fact, it is impossible to use most torrent clients and other applications that are harmless to the network.

I am trying to install new packages to Ubuntu and particularly gcc, make and gnopernicus.  When I type sudo apt-get update at a terminal window, it says

Reading Package List.....Done

but does not hit any of the ubuntu repository archive sites.  Therefore when I type something like sudo apt-get install gnopernicus I get something like

E: could not find package gnopernicus.

When I was on winter break living at home, I did not have this problem on this computer; no hardware changes have been made to it between break and the time I arrived back at school.  Also, in GNOME, when there are updates available, this little icon comes up near the clock in the upper-right of teh screen saying I need updates.  Since I've been here at school, this icon has not shown, even though I never installed updates in the first place.

I am almost certain that the network policy is blocking ports needed for getting Ubuntu updates.  I am authenticated into Miami's network through Cisco Clean Access Agent (windows) and on Linux I am authenticated into the network through a secure web site.  Normal internet browsing seems to work fine in Linux.

One more twist:  I am using VMWare to run Linux at the current moment, but I use bridged networking so the guest OS receives its own IP address.  Using VMWare to run ubuntu never malfunctioned while I was off-campus, so I am still led to believe critical ports are closed on Miami's network.

Any suggestions would be greatly appreciatd.

---

### Post by Mustard on 2006-01-16
Just a guess, but have you configured your browser to use the university proxy?

If you have that would make me think that your browser is correctly configured for the university proxy, but your apt-get isnt.  That's my best shot at guessing what the problem might be anyway. :)

---

### Post by StevenKannel on 2006-01-16
Thanks for the idea Mustard.  I looked into this and apparently my browser does not require proxy configuration for web browsing.  Do you have any other suggestions?

---

### Post by wanger123 on 2006-01-16
Hi Steven, see my post in this thread
[http://www.ubuntuforums.org/showthread.php?p=652997#post652997](http://www.ubuntuforums.org/showthread.php?p=652997#post652997)

wanger

---

