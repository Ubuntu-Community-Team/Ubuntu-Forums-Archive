---
title: "Formatting read-only USB memory stick"
date: 2008-07-12
forum: Hardware
---

### Post by Zatzum on 2008-07-12
So, after some easy time with my Ubuntu I have now a problem.

(You can skip this part. It's not essential.)
Less than a week ago I bought Kingston 2 GB USB memory stick. I have already had another 1GB Kingston stick and it worked perfectly fine. Anyway, I plugged it in and it worked well, the icon popped to desktop and I transferred some big files in it. I let it do the transfer and leave it there, go eat something and when I get back, the status bar says it has transferred about 300M of files already. Then it has some error message about how it can't create folders or something. Now when I think about it, I should have looked carefully to the errors but I didn't have time. I just pressed cancel, and the memory stick folder looked empty. I tried to unmount it (right-clicking the icon and select unmount) but the "memory stick is now safe to remove"- message didn't show up. I just pulled it away in hurry and hoped it would be all right.

So now my memory stick acts like it would be write protected. No, there's no switch in it. I haven't found a way to format read-only usb memory sticks. I have tried to do it in Windows too. It seems that "read-only problem" can be solved by formatting, but all my attempts have failed. Any help?

---

### Post by pmlxuser on 2008-07-12
trying using
gksudo / sudo to format the falsh that works.
or u could use gparted to delete the partition on the flash disk and creat another and format. However if the flash has a warrant i would just go to the shop and get it exchanged. This might just be a sign that the flsh has something wrong.

---

### Post by Zatzum on 2008-07-12
Yeah, I used sudo when tried to format.

I tried deleting partitions in Windows XP, didn't work. What comes to gparted, the whole partition- menu was gray, I couldn't use it. I tried to make a new disklabel on it, but it couldn't do it 

(Unable to open /dev/sdd read-write (Read-only file system).  /dev/sdd has been opened read-only.)

---

### Post by Zatzum on 2008-07-16
I'm starting to feel desperate. Maybe I'll just return it to the store.

edit: I actually returned it and got another one. Hopefully this one will work then.

---

