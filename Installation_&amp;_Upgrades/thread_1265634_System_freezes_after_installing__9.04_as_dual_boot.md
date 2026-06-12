---
title: "System freezes after installing  9.04 as dual boot"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by ortizsr on 2009-09-13
Ladies & Gentlemen :

I just download the latest to a flashdrive, and copied same to my F:\drive on my computer.
Then the Winrar options permitted me to select the C:\ drive for extracting and installation.
Upon rebooting the dual boot is clearly in place, but  once I select the Ubuntu system the computer freezes after revealing the inital Ubuntu screen.
 Please can anyone point out what I need to do to correct this problem????

Respectfully,

Herman Ortiz

P.S. I am but a beginner.

---

### Post by presence1960 on 2009-09-13
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

You don't want to extract the iso to your hard disk and try to install like that. You want to burn the iso as an image to either CD or create a bootable usb from the iso using [unetbootin]("http://unetbootin.sourceforge.net/"). If you used wubi that methos may work, but not for an install with dedicated partition(s) for ubuntu.

So for us to see exactly what you have you are going to have to create a Live CD by burning the iso as an image to CD. See [here]("https://help.ubuntu.com/9.04/switching/installing-burning.html") to learn how.

---

