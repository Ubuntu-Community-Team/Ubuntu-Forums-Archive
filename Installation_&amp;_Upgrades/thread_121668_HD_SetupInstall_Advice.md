---
title: "HD Setup/Install Advice"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by ano1 on 2006-01-25
I am a present Ubuntu user. At the moment I have two HDs set up as follows:
[LIST]
[*]120 GB
[LIST]
[*]Ext3 format
[*]Ubuntu Installed on it
[*]Drive is dieing 
[/LIST]
[*]40GB
[LIST]
[*]Formated FAT32
[*]Contains backed-up folders
[/LIST]
[/LIST] 

My plan is to purchase a new 120GB HD within a week to replace my main failing one. I have copied all important files off of it. 

My new plan is such:
[LIST]
[*]Copy all files from my 40GB drive to the new drive 
[*]Reformat the 40GB drive [Ext3] and install ubuntu on it
[*]Partition the 120GB drive so that 40GB are used to backup the main drive and use the rest for plain file storage [my home folder etc.]
[/LIST]

After all that background info I have three questions:
[LIST=1]
[*]Please comment on this plan. How would you set it up if you had a 40GB and a 120GB HD?
[*] Also is there a free program that I could install that would automatically backup my main HD to a partition on the other drive?
[*]How do I set my second HD to be used as my 'home folder'? 
[/LIST]

Thanks for very much for your time, consideration and feedback.

---

### Post by dcstar on 2006-01-25
[QUOTE=ano1]
......
How do I set my second HD to be used as my 'home folder'?
......[/QUOTE]
When the new HD is formatted and set up with its filesystem, create a /etc/fstab entry for it and mount it under the /home folder.

But **before** you do this, copy all the data (that you want) in the original home folder to a temporary location to be moved to the new /home once mounted.

---

### Post by ano1 on 2006-01-25
[QUOTE=dcstar]When the new HD is formatted and set up with its filesystem, create a /etc/fstab entry for it and mount it under the /home folder.

But **before** you do this, copy all the data (that you want) in the original home folder to a temporary location to be moved to the new /home once mounted.[/QUOTE]

Thanks alot for the information. Anyone else have some advice?

---

