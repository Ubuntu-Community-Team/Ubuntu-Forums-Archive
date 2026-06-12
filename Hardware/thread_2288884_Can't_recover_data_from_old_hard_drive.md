---
title: "Can't recover data from old hard drive"
date: 2015-07-30
forum: Hardware
---

### Post by RabbitWho on 2015-07-30
I tried putting the hard drive in another computer and also a sata usb dock (I think that's what it's called) but I Couldn't access the data from Linux or Windows. It was originally a dualbooted hard drive. There was nothing wrong with it. The screen, or maybe the graphics card, imploded on its old computer. I could hear and see that it never stopped booting up in the old computer. Nothing will read it now. I may have put a password on the hdd, I can't remember. Could that be the problem? I have no experience of stuff like this.

---

### Post by dino99 on 2015-07-30
check first the bios/uefi find it and is well identified
then start gparted to do the same check
and blkid to compare with /etc/fstab in case you need to add it (uuid is recreated)

---

### Post by RabbitWho on 2015-08-25
When I tried to recover it using a ubuntu live disk it recognized the hard drive fine, it just couldn't recover anything. It didn't ask me to enter a password or anything. I definitely had a password on startup but I thought it was on the BIOS, it might have been on both.


>  and blkid to compare with /etc/fstab in case you need to add it (uuid is recreated) I'm not sure what you mean

---

### Post by Bucky Ball on 2015-08-25
If you say there was nothing wrong with it previously why are you trying to recover anything? You might end up deleting something instead! :)

Adding detail to what has been suggested, boot another operating system, or better, boot live media of Ubuntu; put the disk in question in the dock; launch Gparted and see what that sees.

You can also open a terminal with this setup and:

```
sudo blkid
```

If that doesn't see it, something's wrong.

As for the data that's supposed to be on it, we'll get to that. For now, you're saying it is not being recognised at all if I understand correctly.

---

### Post by den_ on 2015-08-25
> **RabbitWho said:**
> I tried putting the hard drive in another computer and also a sata usb dock (I think that's what it's called) but I Couldn't access the data from Linux or Windows. It was originally a dualbooted hard drive. There was nothing wrong with it. The screen, or maybe the graphics card, imploded on its old computer. I could hear and see that it never stopped booting up in the old computer. Nothing will read it now. I may have put a password on the hdd, I can't remember. Could that be the problem? I have no experience of stuff like this.

Hello RabbitWho,

when you say you have put the password, do you mean that the drive was encrypted, or just normal password? If you have used 'normal' password, never do that again. That can only cause troubles. Encryption is much better. It will
protetc your data better, and won't brick your drive. 

In case the password is not involved in your issue (You said you *may* have put the password.) and it is not bricked you have good chances to recover your data like documents/text files, movies and pictures with PhotoRec.
Try 'sudo blkid' as already suggested, or start gparted and see if they are able to detect the drive. If yes chances are you will be able to recover and to format it again (But don't start that before data recovery, in case you have important stuff on that drive.).

---

