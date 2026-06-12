---
title: "Writing to NTFS in Ubuntu"
date: 2008-09-11
forum: General Help
---

### Post by Rhyader on 2008-09-11
I was told - by my friend Bob the Geek - that you should never allow linux
to write to a NTFS filesystem. I have read things about how this is bad.
Yet now, using Ubuntu, I see that it will automatically mount NTFS partitions.
It even seems to do so in read-write mode. I tried writing to one with Ubuntu.
Windows later said it had minor errors, which it seemed to fix easily. 
I've also seen a bit of string fly by here... an option for ther mount command
that I have not seen before: a "mount -t ntfs" followed by a hyphen something.
"ntfs-3g" That's it. What does "ntfs-3g" mean? Does the "-3g" make it safe to
write to NTFS in Ubuntu?  Will a command something like this....
mount -rwv -t ntfs-3g /dev/sda3 /mnt/winpart
work safely ??

---

### Post by iaculallad on 2008-09-11
It seems that you're friend is playing tricks on you when saying that it's not safe for Ubuntu (*Linux) to write on NTFS drive when the truth is: It's vary safe, with the help of drivers. And that is when NTFS-3G comes along. This driver allows you read/write access to NTFS formatted drives.

To read more about ntfs-3g driver, try browsing their [website]("http://www.ntfs-3g.org/").

EDIT: You can automount your partition on startup by adding your mount entries on the fstab file.

---

### Post by Rhyader on 2008-09-12
Wow... This is good news.  Being able to write on NTFS partitions, I mean.
I visited the NTFS-3G webpage. It says:
<<<
The NTFS-3G driver is contained in over 170 distributions, including the most popular ones. Many, like Fedora, Mandriva, openSUSE and Ubuntu with over 8 million users, use NTFS-3G out of the box. 
>>>

Does this mean that the driver is already installed in my Ubuntu? 
How do I tell if it is or not?

---

### Post by iaculallad on 2008-09-12
No, ntfs-3g does not automatically come with Ubuntu. You have to manually install it:

```
sudo apt-get install ntfs-config
```

This will include your ntfs-3g driver.

---

