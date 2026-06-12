---
title: "Trouble mounting lexar jumpdrive"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by johnhamlin on 2005-06-02
i was given a lexar jumpdrive yesterday and I am unable to mount it in ubuntu.  I believe that it is [this drive](http://www.lexar.com/jumpdrive/jd_trav.html)  (I am going by sight)  it is the 1 GB if that matters.  I am running Hoary for AMD64.  I searched the forums but they said that it should just show up when inserted.  it does this when I insert it to windows (so i know it works), but ubuntu doesn't seem to recognize this.
I have tried this command that I found in a forum, with the following output
```
john@ubuntu:~$ sudo mount -t vfat /dev/sda1 /media/usbdrive
mount: special device /dev/sda1 does not exist
```

Any Ideas?

---

### Post by thrift on 2005-06-02
More information would be helpfull.

Try to open a terminal and

cat /proc/scsi/scsi > scsi.txt
dmesg > dmesg.txt

Attach scsi.txt and dmesg.txt from your home directory to your next post.  Using these we will be able to get a grasp of what is going on.

---

### Post by johnhamlin on 2005-06-02
here are the files that you requested

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=johnhamlin]here are the files that you requested[/QUOTE]
 Do you plug it directly in USB port or through a USB hub?

---

### Post by johnhamlin on 2005-06-02
I am pluging it directly into the back of my computer.  no hub.

---

