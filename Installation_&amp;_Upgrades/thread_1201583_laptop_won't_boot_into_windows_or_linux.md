---
title: "laptop won't boot into windows or linux"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by firewall_03 on 2009-07-01
I have a laptop that has Vista and Ubuntu 9.04 installed on it. I used wubi to install ubuntu and I decided to make it a permanent install so I can have more storage space, I followed a guide from this forum to do that and I used the unetbootin partition manager program. The program finished resizing the partitions and what not and now I can't boot into windows or linux. Any Suggestions?

Your help is appreciated I use the laptop to talk to my family while I am serving in Afghanistan.

---

### Post by presence1960 on 2009-07-01
boot from your Ubuntu Live USB or CD. Choose "use ubuntu without changes to your computer". When the desktop loads download the Boot Info Script to your desktop. Get it here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on your desktop. Paste the entire contents of that file back here. Once pasted here highlight all text and click the # sign on the toolbar at the top of window. This will place Code tags around the text. Submit your reply. This will give all info pertaining to your setup and boot process. We'll take a look and see what you have, then we'll go from there. I have a couple errands to run, but post this back when you can. There is a whole community here to help.

---

### Post by presence1960 on 2009-07-01
BTW I want to express my gratitude & appreciation for your valuable, dedicated service to our country. Thank you.

---

### Post by firewall_03 on 2009-07-01
Thanks I will do that once I get netbootin downloaded and get my iso on the thumbdrive thanks for the quick reply

---

### Post by firewall_03 on 2009-07-01
[http://pastebin.com/m5637acc](http://pastebin.com/m5637acc)

---

### Post by presence1960 on 2009-07-01
it appears your wubi install is still on windows. Did you uninstall it through windows control panel as you would add/remove any other program? Once you do that You should be set to install Ubuntu.

P.S. BTW your sda1 partition is your Vista recovery partition-**Do not touch that unless you already made a set of bootable recovery disks. If you lose that partition and don't have recovery disc(s) you won't be able to recover Vista** You can't boot into windows? You may need to repair Vista's bootloader, but since you have a recovery partition you can't access the repair function of the install process. Go here and download the Vista repair disc. it only has the repair function of the Vista install DVD, nothing else: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Burn that as an image to a disc then follow this how to to repair your MBR: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
After that you should be able to boot Vista and then install Ubuntu.

---

### Post by firewall_03 on 2009-07-01
Do you think there is a way I can backup the recovery partition and do a totally clean install of everything? I might just format everything and just go straight ubuntu

---

### Post by presence1960 on 2009-07-01
> **firewall_03 said:**
> Do you think there is a way I can backup the recovery partition and do a totally clean install of everything? I might just format everything and just go straight ubuntu

yes you can back up the recovery partition to any media large enough to store it. Then you can always put it back on the first partition if need be. BUT just to be safe I would still burn a recovery DVD. Your manufacturer should have that option for you somewhere inside the start menu on Vista.

---

### Post by firewall_03 on 2009-07-02
> **presence1960 said:**
> yes you can back up the recovery partition to any media large enough to store it. Then you can always put it back on the first partition if need be. BUT just to be safe I would still burn a recovery DVD. Your manufacturer should have that option for you somewhere inside the start menu on Vista.

I just went ahead and backed it up to my external and did a complete install of ubuntu, I will wait till I get back to the states to put vista back on it. Thanks for all your help!

---

### Post by presence1960 on 2009-07-02
> **firewall_03 said:**
> I just went ahead and backed it up to my external and did a complete install of ubuntu, I will wait till I get back to the states to put vista back on it. Thanks for all your help!

you are welcome. By then you may not want windows anymore!

---

### Post by firewall_03 on 2009-07-02
I just had ubuntu the way I liked it, I had virtualbox installed so I could use itunes for my itouch, VLC for all the movies I acquired while being in Afghanistan.  I guess this is what I would call a learning experience

---

