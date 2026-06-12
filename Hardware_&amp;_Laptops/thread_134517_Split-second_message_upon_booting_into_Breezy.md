---
title: "Split-second message upon booting into Breezy"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by swong1 on 2006-02-22
Hi, I upgraded to Breezy not long ago. It works reasonably well. The problem I'm encountering is not critical, but I would like to know what it is and how to solve it. The problem is that everytime I boot into Breezy, a message appears for a split second before it runs the boot-up script. The message appears too fast for me to read. Is it saved in any log file? Is there anyway to read it? I would like to know what it says and if it is important. Thanks!

---

### Post by hollowhead on 2006-02-22
I may be wrong but I would try looking in dmesg type "dmesg | less" w/o quotes at the shell prompt (in terminal) and have a look in /var/log/messages.  These is where I would start.  My experience of linux for what its worth is that you get loads of errors but not many are critical for example try starting some apps via the terminal and you get messages about fonts being found etc but the app seems to run OK.  I'm getting a message of some type about a hd error on shutdown but everything concerned with the hd seems to work OK.  Hollowhead.

---

### Post by swong1 on 2006-02-22
Thanks for your reply Hollowhead. Both "dmesg | less" and "more /var/log/messages" gave me a long list of messages. They don't look like warnings or errors to me, but then again, I'm no expert. Anyway, I have no idea which one is the one that appears at the start of boot-up. As you said, Linux likes to complain a lot, even if it is a trivial matter. Nevertheless, I don't want to leave it to chances. Thanks!

---

