---
title: "HD Error after Installation"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by sennin-sama on 2009-09-07
I need help with my Ubuntu, I installed ubuntu(9.04) using it to overide my windows, but while tryin 2 install windows along side, i cud find the Ubuntu partition even after re-installin a fresh installation of the Linux the partition was still missing, making my computer to give the error message "ur HD failure Iminent",  even my new installation of ubuntu cannot find d partition, i assigned 20gig to it, and my computer is 80, bt my linux sees d HD as 60Gig, i feel the partition is there somewhere bt  i dont knw wat to do. any help?

---

### Post by presence1960 on 2009-09-08
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

