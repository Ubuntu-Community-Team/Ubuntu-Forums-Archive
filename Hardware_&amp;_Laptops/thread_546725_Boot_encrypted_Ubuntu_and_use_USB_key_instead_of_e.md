---
title: "Boot encrypted Ubuntu and use USB key instead of entering password how?"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by katasuka on 2007-09-09
Greetings,

I've been looking into whole filesystem encryption for Ubuntu (been wanting to test it our for years) and I have a simple question (the answer to this question may not be so simple I bet).

Once the whole encrypted filesystem thing is setup using LUKS, how would I go about taking a USB drive I have and setting it up (and Ubuntu for that matter) to use the USB drive as a "key" to finish booting the encrypted linux without asking for a password?

basically I don't want to type in a long butt password on boot but instead store maybe a keyfile on the USB drive so when I boot with the USB drive in the USB port, Ubuntu will boot without asking me for the password. This way "if" I ever need to, I could destroy the usb drive and then there would be no way to get the data off the computer as I wouldn't know the key to get in, and the usb drive would be useless.

Hope I'm making sense. So, anyone have any ideas because I have found no how tos on this.

I would appreciate any and all help on this. Thank You.

---

### Post by katasuka on 2007-09-10
anyone?

---

### Post by katasuka on 2007-09-16
i guess either nobody knows, or nobody cares to tell me, lol.

---

### Post by kaptengu on 2007-09-21
Did you find a solution to this problem?
I want to do exactly the same thing.

---

### Post by drpaul on 2007-09-21
Nice idea, but it puts you at tremendous risk of a hardware failure. If your key gets zapped, no more access to the computer. Deniability but RISK. :wink:

---

### Post by katasuka on 2007-09-21
> Did you find a solution to this problem?
I want to do exactly the same thing.
no i havent found a solution to this yet. i was asking here on this forum as ubuntu is the distro i will use for this if i can find out how to do this "usb key" thing.

> Nice idea, but it puts you at tremendous risk of a hardware failure. If your key gets zapped, no more access to the computer. Deniability but RISK.
exactly the point. a usb key can be easily destroyed if so needed, effectivly making the computer an expensive paperweight.

i want to find out how to do this so i can learn how to do it. im sure there are people out there who are either very paranoid, really do have something to hide, or just want to keep their data their own.

some people know things that others with power dont want anyone to know. so, by knowing these things, they are in danger. if they can prevent those with power from knowing they know while remaining anonymous, then they can protect themselves better.

a setup like this would be great for people like that. of course for people like that, it would be better to have the harddrive rigged to melt if needed but yea, lol

---

### Post by PmDematagoda on 2007-09-21
About encrypting the entire Ubuntu filesystem or OS, you can try this:-

[http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml)

Though you should be very careful.

---

### Post by kaptengu on 2007-10-05
I found a solution to my problem here:
[http://www.debianhelp.org/node/6797]("http://www.debianhelp.org/node/6797")

> Another question: is there a way to use a USB pendrive to store the
> information needed to LUKS to decrypt the partitions? (so that I
> wouldn't have to fill in any password, just plug the USB pendrive)

Yes, there is. For any partition *except* the root partition, you need
to make the following changes:

- add the key to the luks-Partitions using cryptsetup luksAddKey
- make an entry for your stick in your fstab, e.g. /media/key
- copy the keyfile to the stick, e.g. to /media/key/keyfile
- change your crypttab to use the keyfile, e.g.
usr-crypt /dev/hda7 /media/key/keyfile luks
- change CRYPTDISKS_MOUNT in /etc/defaults/cryptsetup to include your
USB stick, e.g. CRYPTDISKS_MOUNT="/media/key"
- rebuild your initrd using update-initramfs -u

---

