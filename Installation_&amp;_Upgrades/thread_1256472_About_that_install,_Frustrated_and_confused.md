---
title: "About that install, Frustrated and confused"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by sonstar on 2009-09-02
WOW!!!!!!!!!!!
I have two hdd in my computer box. On the original drive I had xp running and it was forever freezing. so put mint on the new drive. A friend said Ubuntu was better so i installed it on the original drive. At that time the ubuntu install had a slider bar to choose which drive and how much of the drive i wanted to use. That was fine and I loved the Ubuntu os. 
Then I got a hold of a xp install disk and I needed it because ubuntu could not use my printer so for printing I had to boot up the old xp and get frustrated. That's why I decided to install the new xp on the newer drive and wip out the mint. when I did this the xp install went into the other drive and wiped out all documents for ubuntu (bummer) I tied to do a virtual install by using the ubuntu disk, and try to find my files but they are gone, even though  there is still a file on the original disk for Ubuntu, and when booting up the option of loging onto Ubuntu is there but files are not there sufficent for booting up.
 
Now comes the most recent problem. I had the xp running on the extra drive and I could still boot up the old version as well. I got some kind of virus or malware and could not boot up the newer xp. I wiped it clean and reinstalled xp, partitioning the drive so I could also add the latest Ubuntu 9.4.  Upon installing Ubuntu there was no slider bar. I chose to use the guided install and use the option that says, use the bigest portion of continuous space (paraphrased). 
End result, I can not boot up the xp, I can not find the old xp on the boot up menu and when i try to use the Ubuntu os It says I do not have enough space to download the updates. I know I installed the Ubuntu on the partition that has 130 Megabytes.
    WHAT SHOULD I DO? Should I just wipe the the xp and Ubuntu install and try again? If so how do I understand the partitioner part, since there is no slider bar to control the partitions?
Thank you for your precious time.
May God richly bless you all.
Sonstar

---

### Post by presence1960 on 2009-09-02
very confusing to know exactly what you have. We need to see exactly what is on those disks & your boot process.

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by sonstar on 2009-09-02
sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/gerard/Desktop/boot_info_script*.sh: No such file or directory

I am on Ubuntu 9.4 and when i try to download the link you sent, the message is, that I don't have enough space on my disk to download that program. The firefox that came with the Ubuntu install is not working properly. I can't go back on any items, the back arrow is grey, not active.
Bookmarks don't work either.

---

### Post by presence1960 on 2009-09-02
> **sonstar said:**
> sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/gerard/Desktop/boot_info_script*.sh: No such file or directory

I am on Ubuntu 9.4 and when i try to download the link you sent, the message is, that I don't have enough space on my disk to download that program. The firefox that came with the Ubuntu install is not working properly. I can't go back on any items, the back arrow is grey, not active.
Bookmarks don't work either.

the instructions said to boot from the Live Cd & do that.

---

