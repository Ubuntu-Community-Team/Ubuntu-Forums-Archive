---
title: "External HDD help!"
date: 2010-11-27
forum: Hardware
---

### Post by Ttomato13 on 2010-11-27
Hi,

I am running Ubuntu 10.10 and have a 1 tb external western digital HDD. It is an elements brand.  I have it on my desk, and my brother knocked it over and it stopped reading. I was able to safely remove it, and plugged it back in, and it worked. My bro not knowing how to use Ubuntu just unplugged it. Now I see it show up but when I click on it, I get this message.

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

I can't remove it safely, and now I am pretty upset. Did I just lose all my files?

***Nevermind, posted in wrong area, misread the sub category.***

---

### Post by wilee-nilee on 2010-11-27
If it is formatted as a NTFS, do you have a windows setup to run a chkdsk on it.

---

### Post by Ttomato13 on 2010-11-27
> **wilee-nilee said:**
> If it is formatted as a NTFS, do you have a windows setup to run a chkdsk on it.

Yes it was formatted with NTFS when it was connected to my windows desktop before I made the switch to Ubuntu.

---

### Post by wilee-nilee on 2010-11-27
> **Ttomato13 said:**
> Yes it was formatted with NTFS when it was connected to my windows desktop before I made the switch to Ubuntu.

If it was me it is hard to say what has happened as it seems to have had a bit of a beating, but a chkdsk /r would be where I went to start.

You could look at the HD if it shows in gparted in ubuntu right click then information to see what it says

---

### Post by Ttomato13 on 2010-11-27
> **wilee-nilee said:**
> If it was me it is hard to say what has happened as it seems to have had a bit of a beating, but a chkdsk /r would be where I went to start.

You could look at the HD if it shows in gparted in ubuntu right click then information to see what it says

Actually, I think the HDD is damaged. It shows up fine now. I can see all my files. When I go to transfer them, it takes forever and fails.

---

