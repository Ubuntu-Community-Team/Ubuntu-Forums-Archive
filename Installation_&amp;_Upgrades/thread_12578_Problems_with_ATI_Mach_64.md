---
title: "Problems with ATI Mach 64"
date: 2005-01-25
forum: Installation &amp; Upgrades
---

### Post by emmeborn on 2005-01-25
Hi,

I just can't solve this problem with my videocard.
When starting I get an error telling me that no videocard is present. The card is a ATI Mach 64 and i am running ubuntu on a PII 400MHz. I have run Red Hat 7.2 on this machine with no problems. I also have WinXP installed on another disc.
Help is wanted to solve this issue!

---

### Post by farruinn on 2005-01-26
At what point are you getting the error?  Is it during the X configuration phase of the install?  If it is, on my mac the "ati" driver works fine for this videocard.  If the error is occuring at a different point could you include some details?

~Nathan

---

### Post by emmeborn on 2005-01-28
After installation, when I try to log in I never come to the graphical login it just tries a couple of times and then I get the login prompt. Then I try to start gnome I get the error message that X is missing. I have also tried to modify the Xfree86config file but it makes no different.

This is very strange, I just will not go back to Red Hat 7.2 again.
Anyone that has any suggestions??? :???:

---

### Post by farruinn on 2005-01-28
When I have problems such as these I do 'sudo dpkg-reconfigure xserver-xfree86' which will reconfigure your X entirely.  Of course, if the message you're getting is really saying that "X does not exist" then maybe xserver-xfree86 isn't even installed? This seems unlikely to me if you're able to edit /etc/X11/XF86Config-4 though.  The installer should install this package of course, but I've had problems before...

~Nathan

---

### Post by kultuur on 2005-01-28
[QUOTE=emmeborn]Anyone that has any suggestions??? :???:[/QUOTE]
Can you find error messages in /var/log/XFree86.0.log ?

---

### Post by emmeborn on 2005-01-28
I have found out that it don't recognize my ATI card it sets my Voodoo 2 card as default card. Where can I change this setting?

---

