---
title: "updates broken"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by dfpd62 on 2009-05-07
Hi Folks,

I installed 9.04 when prompted by updater, and while it has taken me a few weeks to get used to it I am still not sure that I like it.

My problem is that each time that I try to apply updates/fixes I get this error message, 
Software Updates - KDE Control Module.
"An Internal system error has occurred"
"A problem that we were not expecting has occurred.
Please report this bug with the error description."

"The backend took too much time to process the synchronous request - you need to fork!"

I do not know if any updates are being applied or not, the "Updates Available" icon in the panel goes away when the error message is closed.
when I click on "Refresh" all that appears is "1 Blocked Update"
do I assume that updates are being applied?

Any ideas welcome.

Thanks in advance

Donald

---

### Post by bandidoloco on 2009-05-07
"apt-get autoremove" should do the trick I guess

---

### Post by dfpd62 on 2009-05-07
Tried that, and 
apt-get upgrade,
 apt-get --fix-missing install,
 dpkg --configure -a
,apt-get -f install,
 apt-get update.
not strictly in that order, but all done, and what is a "Fork"

---

### Post by pennygov on 2009-05-13
Anyone else with this problem? My upgraded (from Intrepid) is doing the same thing and my husband's newly (yesterday) installed system is doing it.

I would also like to know what a "fork" is (other than the obvious). Is this a message we should be sending to someone on the bugfix team?

---

### Post by kibster on 2009-05-13
Pardon me for butting in But I am also having update issues. Might this be for upgrades. Because mine is of different..then some of yous.

---

### Post by Kevbert on 2009-05-13
This is a known bug. Please take a look at [[COLOR="Red"]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/272410") and add any additional comments as required.

---

### Post by shaunehunter on 2009-06-10
this is how to get blocked updates:

from the terminal type.

sudo apt-get dist-upgrade

then your password.

I read somewhere on these (or kubuntuforums.org) that the reason you get these is they require the removal of other packages.

That might be wrong and or misquoted as it was a while ago but it's never led to problems for me.

---

