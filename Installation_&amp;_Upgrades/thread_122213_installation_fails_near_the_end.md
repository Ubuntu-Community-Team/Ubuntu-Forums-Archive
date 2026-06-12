---
title: "installation fails near the end"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by sailen on 2006-01-27
I've got a problem installing Ubuntu Linux on my system. The comp is
AMD Athlon 1.8, Asus A7V333, 768M DDR, Radeon 9600pro, have no net
adapter.
When primary installation finished and computer reboot, package
installation and configuration started. The process stops suddenly and
error message appear. Something like "Error while installation. Some packages were not installed, you may fix it by yourself.."
I tried installing both Ubuntu 5.10 and Kubuntu 5.10 - the problem is
the same.
I hope you could advise me what to do with this.

---

### Post by amohanty on 2006-01-27
Its possible your CD was not recorded properly. When the boot prompt comes up  type:
**expert**
press <Enter>

You should get a screen with a long list of items. Scroll down to verify install media and select it. That should tell you if the CD is ok or not.
If the CD is ok, try and post the _exact_ and _full_ message. It will be helpfu l in figuring out what went wrong.

HTH
AM

---

### Post by sailen on 2006-01-27
It happened! Kubuntu went on with 7-th try!
Installation completed successfuly, but now there's another problem.

When I try to change some settings (root password required) it says "Cannot use su" or smth like that. So I can't get root rights.
What's the problem about, who knows?

---

### Post by agapito on 2006-01-27
That's easy. Ubuntu doesn't have a root account, at least not the way other distros have. The password you need is your password. I had the same problem when i migrated from Mandrake. :) To give a command as root in the shell type **sudo** [COLOR="Red"]before the command[/COLOR], it will ask for your password. To get a shell as root do **sudo -s -H**.

[COLOR="Red"]Edited[/COLOR]

---

### Post by sailen on 2006-01-27
Well I ment different thing. For example I start Kuser, type password, then it says "su retuned with an error"
some programs says "conversation with su failed"

---

### Post by amohanty on 2006-01-27
> "conversation with su failed"

I answered this question sometime back. Take a look at this post:
[http://ubuntuforums.org/showpost.php?p=652349&postcount=2](http://ubuntuforums.org/showpost.php?p=652349&postcount=2)

HTH
AM

---

