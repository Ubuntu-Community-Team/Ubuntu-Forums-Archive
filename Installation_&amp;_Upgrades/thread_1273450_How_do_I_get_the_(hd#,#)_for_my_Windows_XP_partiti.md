---
title: "How do I get the (hd#,#) for my Windows XP partition?"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by gatohoser on 2009-09-23
Hey all,
The subject about says it all but what's happening is that I just installed a dual boot Ubuntu/XP. I installed Ubuntu first (I know, I know. I found out that's harder after) and then reinstalled XP. This wiped grub so I reinstalled it. But now I've lost access to XP. So I have gone into terminal and sudo gedit menu.lst in /boot/grub/ and have entered this:

title    Windows XP Professional
root    (hd0,1)
savedefault
makeactive
chainloader +1

But it doesn't seem to work. I also tried (hd0,0) which didn't work. I'm not quite sure how to find where I installed XP in linux speak.

---

### Post by presence1960 on 2009-09-23
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by gatohoser on 2009-09-23
Hey Presence. Thanks for your help. I fixed the situation by randomly typing numbers into menu.lst until I found the right partition. I was worried it would erase a boot record or something but then I realized I didn't have that much work into installing the two OS's. But thanks for your advice! I tried to delete the thread when I fixed it but I couldn't figure out how.

---

### Post by presence1960 on 2009-09-23
> **gatohoser said:**
> Hey Presence. Thanks for your help. I fixed the situation by randomly typing numbers into menu.lst until I found the right partition. I was worried it would erase a boot record or something but then I realized I didn't have that much work into installing the two OS's. But thanks for your advice! I tried to delete the thread when I fixed it but I couldn't figure out how.

you can edit your thread title to include **[Solved]** by using the thread tools at the top right of the page.

P.S. it would be nice if you know how to get those (hdx,y) designations for two reasons. One, if you ever have to do it again or two, if you are trying to help someone else.

---

