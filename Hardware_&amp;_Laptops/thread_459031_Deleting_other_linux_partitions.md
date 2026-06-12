---
title: "Deleting other linux partitions"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by Lutin on 2007-05-30
This may seem like a silly question, but I'll ask it anyway as there is bound to be someone else out there that would like to know the answer.

I have successfully installed Edgy on my Acer Aspire 7003 laptop and even managed to get the correct nVidia graphoics drivers working, built in card reader etc, etc. So far all well and good. However, I also have Suse 10.2 x64 installed on the machine as well (gave up on it do to the non-working updates proceddure. Shame really as everything else worked okay).

So, now I want to delete these partitions and free up the space for Edgy. Will deleting the partitions mess up fstab and prevent me being able to run Edgy? Or am I just worrying too much?

A helping hand would be appreciated.

---

### Post by kidders on 2007-05-31
Hi there,

Deleting those filesystems will upset anything that expects them to be there, so you should check things like /etc/fstab and your bootloader configuration before you remove them.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

