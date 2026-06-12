---
title: "Upgrade to KDE 4.3.2 causing problems"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by jpcrow on 2009-10-08
Hello!

Two days ago I decided to format my laptop with WinXP and install kubuntu.

I've had some experience with Ubuntu and Gnome but wanted to try out KDE and see how I liked it.

Well, everything was perfect... until I went to upgrade KDE.

I was puzzled by error messages in Konsole about UID 1000 not being UID 1.

Now apparently you aren't supposed to use 'sudo' but instead use 'kdesudo' when you have KDE installed and there is a bug associated with this issue which I have read up on.

I found this out after I had upgraded and didn't investigate into it utill KDE started spitting out Error messages like crazy. (First reboot after upgrade)

I think because I used 'sudo' when I upgraded, ie. 'sudo apt-get dist-upgrade' that I have now messed up my permissions for important files that KDE uses.

I gather this from the error messages:

Klipper Config file unwritable. Contact administrator.

and 

Kmigrator failed 

and 

akonadi failed to start


What should I do? Uninstall the upgrade? and then reinstall using kdesudo?

(I don't know how to do that)

or somehow change the permissions... I'm kinda stumped (I'm tech savvy and can follow instructions but not quite knowledgable enough to diagnose and repair without your help =)

Thanks!

PS I installed Kubuntu 9.04 two days ago.

---

