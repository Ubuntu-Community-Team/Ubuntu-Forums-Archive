---
title: "[SOLVED] Updates not installing (error:Broken Count &amp;gt;0)"
date: 2008-07-24
forum: General Help
---

### Post by Drizzel on 2008-07-24
When I run the update manager it says its downloading 47 out of 47 updates, but they never install and it wont show me what its trying to update. Is there something I can type in a terminal to find out what is failing to update? I'm on a fresh install of ubuntu, though this has been happening ever since I've been using ubuntu. Here is a screenshot of the error boxes. The exact error I got while hovering the mouse pointer over the update icon in the task bar is: Error: Broken Count >0' Installed packages have unmet dependencies. What can I do to resolve this?

---

### Post by iaculallad on 2008-07-24
You could update using the terminal, in that way, you could see what are being updated and what dependency needs to be met. You could post any error it displays.

```
sudo apt-get update && sudo apt-get upgrade
```

EDIT: For the broken count error:

Navigate to System->Administration->Synaptic Package Manager

If it detects broken packages, it will inform you. Select 'Custom' from the buttons select 'Broken'. Right click on the package and remove it.

---

### Post by Drizzel on 2008-07-24
Shows no broken packages. Also I ran the command you posted and I dont get any errors. This is what I see when I try to update via synaptic (see screenshot). It never installs any of whatever it downloads because I go through this routine every time I update. Its strange. The downloads happen so fast that I dont have time to click on the details option to see what its getting or rather not getting. Barely had enough time to pull off the screenshot. Any ideas what I can do?

---

### Post by plucky on 2008-07-24
> Shows no broken packages. Also I ran the command you posted and I dont get any errors. This is what I see when I try to update via synaptic (see screenshot). It never installs any of whatever it downloads because I go through this routine every time I update. Its strange. The downloads happen so fast that I dont have time to click on the details option to see what its getting or rather not getting. Barely had enough time to pull off the screenshot. Any ideas what I can do?


That is the normal screen when it is looking for updates.It downloads package lists from the servers and compares them to the installed lists on your computer.Only when it finds updates or upgrades,does it tell you that there are updates or upgrades to install.

Do you have it automatically install security updates?
Check your **System > Administration > Software Sources > Updates** and make sure **Only notify about available updates** is checked.

The "sudo apt-get update" command searches for updates
The "sudo apt-get upgrade" command actually installs the updates.
If you have no errors running the above commands and your software sources.list has all the repositories open,then you should be up to date.

Good Luck

---

### Post by Drizzel on 2008-07-24
Wow. Thanks so much! That had been driving me crazy. :)

No errors or anything, so I guess all is well.

---

