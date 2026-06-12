---
title: "Problems with External Harddrive!"
date: 2012-12-08
forum: Hardware
---

### Post by never4getthis on 2012-12-08
Ok, I decided to give Ubuntu a shot today, and to my surprise, I am incredibly disapointed and angry.

First of all, where on EARTH is the log out button. I entered a live session with a live USB, I made an administrator user and then wanted to switch to it. ....but HOW, I dont know if I'm stupid, but I go into the Ubuntu Help and the button on the top right is non existent. HOW ON EARTH is a ne user supposed to feel comfortable in an operationg system that its impossible to LOG OUT easy!

You might be thinking why I needed to switch user. Well earler in the day I decided to install ubuntu in an external haddrive. I checked the box of 'encrypt files' and then the install failed. Now every time I plug in the drive it asks me for the password, I type it in and BOOM error message! I am 10000000% sure that the key I am typing is correct.

Does any one have any sugestions? how can I install it on my hardrive now that its encrypted? Again, incredibly disapointed, I have not had any of these problems with other linux distros.

---

### Post by lemming465 on 2012-12-22
If this a recent version of Ubuntu, such as 12.04 or 12.10, the log out option is toward the bottom of the settings gizmo (gear/power icon, rightmost on the top bar).

To be an administrator on a live CD, you can open a terminal window (e.g. Ctrl-Alt-t, or windows & search for terminal) and type *sudo -i*

To switch to a different user, use the name dropdown (just left of the settings/power gizmo).

Live CD versus encrypted drive versus musical users is going to result in adventures in key storage, so I'm not surprised you are getting key prompts.  Without more details about which flavor and version of Ubuntu you are using (Ubuntu? Kubuntu? Xubuntu? 12.10? 12.04? 11.10? 10.04? ..) whether you are still running off a live CD or a disk-install, what user you are running as, etc. we aren't going to be able to tell you much about the key prompt.  It might be wanting your user password rather than the disk password, depending on the exact situation.  Also, which disk encryption option you picked matters.  Are you encrypting just files and directories, or entire partitions?

Sorry you are having so much trouble with Ubuntu compared to other distributions.  What else have you used?

---

