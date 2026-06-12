---
title: "how to remove ubuntu8.04.1 LTS"
date: 2008-10-27
forum: General Help
---

### Post by turbo71113 on 2008-10-27
i have installed ubuntu 8.04.1 LTS Desktop edition on vista.
it has uninstall option but its not responding.
i deleted so that i can again install a fresh copy by allocating a special drive for it.

can anyone tell me how to remove grub(i.e,where we find options to logon to vista or ubuntu) that comes during booting vista....

help pleaseeeeee:confused:

---

### Post by bodhi.zazen on 2008-10-27
See these links :

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

    wubi : [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

---

### Post by turbo71113 on 2008-10-27
> **bodhi.zazen said:**
> See these links :

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

    wubi : [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

will this work for vista

---

### Post by bodhi.zazen on 2008-10-27
should work just fine. If not, post any errors or other problems.

---

### Post by turbo71113 on 2008-10-27
> **bodhi.zazen said:**
> should work just fine. If not, post any errors or other problems.

hey i installed Wubi ubuntu...that is as anyother software we normally install on vista..

and i think the following process is when we install ubuntu on a fresh formatted partitio,

> **bodhi.zazen said:**
> (1) Boot you Windows installation
(2) Click on this link Get Mbrfix
(3) Download the program, unzip it and copy it to your root folder (I'll assume c:\)
(4) Open up the command prompt in Windows by going to start/accessories/command prompt
(5) Type:
cd \ and press "Enter"
mbrfix /drive 0 fixmbr /yes and press "Enter"

*PLEASE NOTE* The above assumes your boot device is device 0 - if you are not sure on this please post for help.

(6) Close the command prompt window

there is a note mentioned about the device 0...iam not sure about the above process..can u assist me in this plz

---

### Post by bodhi.zazen on 2008-10-28
I am having a problem understand what you are doing. You mention wubi and grub ???

How did you install Ubuntu ? 

If with wubi you did not install grub, wubi uses the windows installer.

See this link : [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

If you installed Ubuntu in the "standard" method, repartitioning your hard drive, then you installed grub and you need to use the Windows recovery disk to re-install the windows MBR.

So can you clarify what you did (wubi ?) and what step you need help with.

---

