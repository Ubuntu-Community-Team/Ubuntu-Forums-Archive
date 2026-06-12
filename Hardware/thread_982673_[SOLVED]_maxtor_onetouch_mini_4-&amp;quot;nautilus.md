---
title: "[SOLVED] maxtor onetouch mini 4-&amp;quot;nautilus cannot display&amp;quot;"
date: 2008-11-15
forum: Hardware
---

### Post by motoperpetuo on 2008-11-15
i got a 320gb maxtor onetouch 4 mini external hard drive the other day. it always works initially, but then after a little while (maybe 15 minutes, maybe an hour, but always eventually) it stops working and i get the following error when i try to access it or any folders or files on it:

Nautilus cannot display "/media/duomo".
Please select another viewer and try again.

("duomo" is, of course, the name i gave the hard drive in question.) 

doing a ctrl+alt+backspace to restart GNOME seems to fix this, but the problem also seems to always resurface eventually. anyone have any idea what i could do to fix this?

also, if it makes any difference, i'm on linux mint 4.0, not ubuntu (but i find that most ubuntu advice works on mint).

---

### Post by taurus on 2008-11-15
What filesystem is that Maxtor harddrive?

---

### Post by motoperpetuo on 2008-11-15
> **taurus said:**
> what filesystem is that maxtor harddrive?

ntfs.

---

### Post by taurus on 2008-11-15
Maybe you want to hook that maxtor external drive to a windows machine and run a scandisk and defrag of that harddrive then.

---

### Post by binbash on 2008-11-15
I have same hard drive with same file system  and i didn't see that.Better to listen taurus's advice.

---

### Post by motoperpetuo on 2008-11-15
> **taurus said:**
> Maybe you want to hook that maxtor external drive to a windows machine and run a scandisk and defrag of that harddrive then.

i'll give that a shot. i'd like to keep it NTFS for the sake of compatibility with windows.

---

### Post by motoperpetuo on 2008-11-15
hmm...the drive just beeps when i connect it to my windows laptop, and the laptop doesn't recognize the drive. i'm going to assume it's bad and take it back to the shop.

---

### Post by motoperpetuo on 2008-11-25
> **motoperpetuo said:**
> hmm...the drive just beeps when i connect it to my windows laptop, and the laptop doesn't recognize the drive. i'm going to assume it's bad and take it back to the shop.

update: i tried connecting the drive to another windows computer, and it worked. i ran defrag and chkdsk. it took about 20 hours, but the drive works under linux now. thanks for the advice!

---

