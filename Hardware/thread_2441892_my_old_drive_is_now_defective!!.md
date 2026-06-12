---
title: "my old drive is now defective?!!?"
date: 2020-04-27
forum: Hardware
---

### Post by anotherChris on 2020-04-27
Per this thread: [https://ubuntuforums.org/showthread.php?t=2441890](https://ubuntuforums.org/showthread.php?t=2441890)  my "old drive is now defective".    I don't really have any idea what that means.  Can I fix it in the next 12 hours so I can install 20.04, or do I just need to get a new computer?

---

### Post by oldfred on 2020-04-27
Does Amazon deliver in 12 hours?
Did you try the disk check suggested in that thread?

---

### Post by Yellow Pasque on 2020-04-28
> **anotherChris said:**
> Per this thread: [https://ubuntuforums.org/showthread.php?t=2441890](https://ubuntuforums.org/showthread.php?t=2441890)  my "old drive is now defective".    I don't really have any idea what that means.

Why did you make another thread? Read the last response in your other thread: [https://ubuntuforums.org/showthread.php?t=2441890&p=13951326#post13951326](https://ubuntuforums.org/showthread.php?t=2441890&p=13951326#post13951326)
It is a bug with the Lubuntu installer. You need to manually create the partitions you want to use to install.

> do I just need to get a new computer?

At the worst, you would need a new disk/drive. And there is no evidence you need a new drive. The temp sensor issue with the drive may indicate that you need to open the laptop up and clean it out with compressed air. Or it could just be a bogus reading. Look at results of:
```
sudo smartctl -a /dev/sda
```
At any rate, with a laptop that old, it's probably a good idea to dust it out anyway. If you can find a cheap 2GB stick of RAM, that would certainly help performance.

---

### Post by anotherChris on 2020-04-29
> **Yellow Pasque said:**
> Why did you make another thread? 

I'm sorry.  I was awake all night, falling asleep at the keyboard, and not thinking straight.

I'm marking this thread as solved.  If I can delete it, I will.

---

