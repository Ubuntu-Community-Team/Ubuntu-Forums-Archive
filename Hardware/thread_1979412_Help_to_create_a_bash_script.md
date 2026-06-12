---
title: "Help to create a bash script"
date: 2012-05-13
forum: Hardware
---

### Post by vedovatti on 2012-05-13
Hi guys,
I need help to create a scrip. The **background** is that I need it to change hybrid (or switchable) graphics with vgaswitchroo. So far the best option I found is to add the command:```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```in the file /etc/rc.local. The commands turn off the discrete card.
My script that I want is to be executable and when I excecute it and in the /etc/rc.local the command that is on the line 17 is echo OFF > /sys/kernel/debug/vgaswitcheroo/switch, it changes to echo DIS > /sys/kernel/debug/vgaswitcheroo/switch, that should turn off the integrated. And if the same procedure but the other way around if the command and in the line 17 is echo DIS > /sys/kernel/debug/vgaswitcheroo/switch, change it to echo OFF > /sys/kernel/debug/vgaswitcheroo/switch. Does anybody know how to program a script like I need?
Thank you.

---

### Post by oldfred on 2012-05-13
I am no script expert. But the way I create simple scripts is to run them from command line to make sure they work, then list history with history command and copy into a bash file. Best to remove sudo from bash file.

Some possibly related:
Boot using recovery mode & 'Reconfigure graphics' or
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

---

### Post by vedovatti on 2012-05-13
Thank you but I just solved the main problem I had,that was to switch hybrid graphics with a script. The solutions is on the comment 9 in the [http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317) . Just as additional info I have a HP tm2 (Intel/ATI) and Ubuntu 12.04. Finally I can manage both cards. Anyway, thank you very much for your fast answer.

---

