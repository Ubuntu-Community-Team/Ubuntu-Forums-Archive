---
title: "Package manager won't run"
date: 2008-04-19
forum: Georgia Team - US
---

### Post by Eric Weir on 2008-04-19
I've posted about this on the Ubuntu installation and upgrade forum, but thought I'd try here, too.

I finally got my system to recognize the HD and get Kubuntu installed. After doing that and downloading all the upgrades, adept notified me that one application had not been upgraded because it "was broken or would break" the application.

Subsequently, when I went to install Firefox and Thunderbird, adept notified me that there was a conflict with another application, "probably some part of adept itself, or with apt, apt-get, or aptitude," and asked if I wanted to try to resolve the conflict. When I said, yes, after a few seconds adept crashed. This continues to happen even after rebooting.

The only way I know to solve the problem is to do another install. I imagine there are other things well short of this that  I can do, but being a nontechie I don't have a clue what they are.

Any suggestions would be appreciated? 

Sincerely,

---

### Post by siafulinux on 2008-04-26
> **Eric Weir said:**
> I've posted about this on the Ubuntu installation and upgrade forum, but thought I'd try here, too.

I finally got my system to recognize the HD and get Kubuntu installed. After doing that and downloading all the upgrades, adept notified me that one application had not been upgraded because it "was broken or would break" the application.

Subsequently, when I went to install Firefox and Thunderbird, adept notified me that there was a conflict with another application, "probably some part of adept itself, or with apt, apt-get, or aptitude," and asked if I wanted to try to resolve the conflict. When I said, yes, after a few seconds adept crashed. This continues to happen even after rebooting.

The only way I know to solve the problem is to do another install. I imagine there are other things well short of this that  I can do, but being a nontechie I don't have a clue what they are.

Any suggestions would be appreciated? 

Sincerely,

Actually since you are [planning on doing another install]("http://ubuntuforums.org/showthread.php?t=756912") to move your /home directory, you may not need to worry about this. Still, there are better ways to try and deal with a situation like this other than trying to do a new install.

Go to a console window in KDE or by pressing CTRL-ALT-F2 or F3, etc. Type in "sudo apt-get update", hit enter and then try the following commands to see if they resolve the error:

[LIST=1]
[*]*sudo apt-get -f install*
[*]*sudo apt-get -f remove*
[*]*sudo dpkg --configure -a* (This one usually works for me).
[*]*sudo dpkg -r [package name]* (This tries to remove the offending package).
[/LIST]

JC

---

