---
title: "USB memory stick"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by marcadams on 2005-10-12
Hi;

I have a 64 mb USB memory stick.
I have no problem copying files onto it - however, when I delete those files I loose the  file space. I.e. eventually my memory stick runs out of space (despite showing nothing on the drive).

Is there a way of formating such devices (as is possible on Windows), so I can reclaim my capacity?

Many thanks
Marc

---

### Post by Qrk on 2005-10-12
The system creates a hidden folder named .trash-username, which saves all the files you delete. Enable viewing hidden folders in nautilus so that you can delete files from that folder as well. I'm not sure how to stop it from making a trash folder.

---

### Post by marcadams on 2005-10-13
Qrk - you were extactly right. After deleting the hidden trash folder I regained my space.

Thanks very much for your help
Marc

---

### Post by Alexander Kirillov on 2005-10-13
[QUOTE=Qrk]The system creates a hidden folder named .trash-username, which saves all the files you delete. Enable viewing hidden folders in nautilus so that you can delete files from that folder as well. I'm not sure how to stop it from making a trash folder.[/QUOTE]
An easier way: just click on the trash icon on the panel, and then  use "empty trash". This will remove trash from all mounted filesystems, including the USB stick.

---

