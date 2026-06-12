---
title: "Need to erase and reinstall Jaunty on hd0 /dev/sda1"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by luangwa on 2009-08-14
When I first installed Jaunty I created two partitions One for Jaunty and the other for Home. Due to many trials and tribulations that I won't go into, I want to erase Jaunty from the first partition without changing the structure and then reinstall Jaunty. I have Gparted on a CD but I'm not sure how to safely proceed to leave the Home partition with all my data alone.

---

### Post by sblunix on 2009-08-14
Boot Up With Live CD, Install, Go Through Steps Until It Asks About Partitions, Select "Manually Configure Partitions" Then go ahead and Telll it to format the "/" mount drive and install there, while keeping the /home/ drive the same. :)

---

### Post by luangwa on 2009-08-14
Thanks for your fast response. I will do as you suggested after I backup my files.

---

### Post by stlsaint on 2009-08-14
+1 for sblunix

---

### Post by presence1960 on 2009-08-14
When doing the manual install be sure to highlight your /home partition click edit then set parameters. **_Do not tick the format box or you will lose everything on that /home partition!_** very important you set mount point as /home or it will not auto mount when you boot Ubuntu.

---

