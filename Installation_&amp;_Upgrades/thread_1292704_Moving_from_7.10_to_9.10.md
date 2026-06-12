---
title: "Moving from 7.10 to 9.10"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by Officer Dibble on 2009-10-16
Hi,

Well, I can't tell you how good it feels to be back in Ubuntu. :-)

I would now like to upgrade from 7.10 to 9.10. Would it be sufficient to to just back-up my HOME folder, do a clean install of 9.10, and then overwrite the HOME folder 9.10 with with my backed-up 7.10 HOME folder?

I appreciate that I will still need to reinstall apps, and that won't be an issue.

If what I have suggested here is just plain silly, I would be grateful for any suggestions as to a time-effective way of doing this, please.

---

### Post by tommcd on 2009-10-16
A clean install of 9.10 will work just fine. If you have a separate home directory then your data is safe. If you do not have a separate home directory then this would be a good time to create one. 
I would not overwrite the hidden (all the files and directories that start with a "."). The new config files in 9.10 may be different than in 7.10.

---

### Post by Officer Dibble on 2009-10-16
When you say a separate home folder, how separate are we talking here? To my knowledge I only have the one home folder.

I'm sorry if this is a daft question.

---

### Post by phillw on 2009-10-16
It is recommended that you make a seperate partion in for your /home directory.

Thus, you would have 
/
/home
/swap

partitions, and not just 
/
/swap

Some go as far as adding 
/var

as a partition - I think this is mainly for servers, tho'.

I'll be doing this before I upgrade to 9.10 from 9.04

Phill.

---

### Post by jward3010 on 2009-10-16
> **phillw said:**
> Some go as far as adding 
/var

as a partition - I think this is mainly for servers, tho'.

Phill.
Tis for Servers usually for mail or DNS databases etc. It's for things that change frequently. Variable is it's long name.

To find out if you have a separate home type:
```
df -h
```
If it appears than you have a separate home partition.

Or go into System Monitor and look at filesystems tab.

---

### Post by jward3010 on 2009-10-16
I recommend you get rid of your hidden files and directories if you do have a separate home partition. They might cause serious conflicts with the much updated 9.10 system you're about to install.

---

### Post by Officer Dibble on 2009-10-16
No, it's definitely not on a separate partition. I've just got an ext3 partition and a swap partition.

Just out of curiosity, what would be the value in having Home on a separate partition if it was still on the same drive? You wouldn't get a better performance out of it would you, rather wouldn't such a configuration have an adverse affect on the longevity of the drive?

---

### Post by mikewhatever on 2009-10-16
Having home on a separate partition makes it easier to reinstall. You can also share home among several OSs, but there is no advantage performance wise.

---

### Post by phillw on 2009-10-16
From what I understand (And I'm SURE someone will correct me if I'm wrong !!)

Having a seperate home partition is sorta useful if you have a few (many) users on - if you are doing major updates / disaster recovery (power went out in the middle of a critical system update) it keeps all their 'stuff' in a different partition.

I think it's a bit like having the /var partition - it has its own space

The difference being is that users are the ones who 'store' stuff and gobble up disk space (you know .. music, vids etc) . If the partition /home was becoming full you could pop in a new, bigger, hard-drive and easily transfer it over.

I have probably over-simplified that, but that is how I see it.

Phill.

---

### Post by tommcd on 2009-10-17
Here is a good tutorial on creating a separate home partition while installing Ubuntu:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

