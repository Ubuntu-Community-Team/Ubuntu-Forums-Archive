---
title: "Hardware Problem for Booting Up!"
date: 2016-04-20
forum: Hardware
---

### Post by kkk5 on 2016-04-20
**How do I fix this problem?**

---

### Post by Bucky Ball on 2016-04-20
Can't fix but can give you some clues. The error says the system is looking for a partition that doesn't exist (or at least a UUID number that doesn't exist). This means you might have your boot order wrong in your BIOS or are booting to the wrong device some other way.

Can't confidently say much more without more info. If you're after support it is best to give a lot more info than you have. Whether this is a new install and which version/flavour of Ubuntu you are using would be a start. You might like to check the pink link in my signature for some posting tips.

Good luck. :)

---

### Post by kkk5 on 2016-04-21
It's **Kubuntu**. I've been using this OS for around a year. I think might need to go to a computer technician for this.

---

### Post by weatherman2 on 2016-04-21
How many hard drives?  Just one?  If you have one hard drive, then it looks like Grub can't find the partition it's expecting to boot from.  That could mean your hard drive got corrupted or is failing.

If you have more than one drive, could be that one drive has failed or has become corrupted or even disconnected physically.

You could boot a live CD or USB of Ubuntu/Kubuntu, open a terminal, and type this:

```
sudo blkid
```

and see if the partition with UUID "d095....blah blah blah" is on the list.

---

### Post by kkk5 on 2016-04-26
I've got important files in the hard drive, and I can't afford to lose them.
Should I just go to the acer maintenance, and ask them to repair it? Or could I do something with it in the command line?

---

### Post by Bucky Ball on 2016-04-26
If you can boot from live media I would 'Try Ubuntu' and back up your files to an external device. Goes without saying, you should already have backups, though. :)

---

### Post by kkk5 on 2016-05-02
I managed to download the Kubuntu (1.4 something GB), and I got it on a USB Flash Stick. How can I fix this problem?
I plugged the USB, and tried one of the suggested command lines from this thread [http://askubuntu.com/questions/498243/gave-up-waiting-for-root-device-14-04](http://askubuntu.com/questions/498243/gave-up-waiting-for-root-device-14-04)
and this is what I got [B]/bin/sh: sudo: not found

Should the Kubuntu file be on the top level?

What should I do?[/B]

---

