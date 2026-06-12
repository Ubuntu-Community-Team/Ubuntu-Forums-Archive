---
title: "Dual Boot with Windows not being first partition"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by sirlancelot on 2009-10-08
I have the following partition setup (/dev/sda2 is my encrypted swap partition). Is it possible to install Windows XP on /dev/sda4?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131197&stc=1&d=1254987691[/IMG]

I'm fairly certain it's because I don't have a fat32 partition at the beginning. Can anyone offer advice for installing XP on this kind of setup? I've gotten as far as adding the entry to GRUB and getting the infamous "NTLDR is missing" error.

```
title		Windows XP hd0,3 (/dev/sda4)
map		(hd0,0) (hd0,3)
map		(hd0,3) (hd0,0)
rootnoverify	(hd0,3)
makeactive
chainloader	+1
```

Any help would be appreciated :) Thanks.

---

### Post by zeroseven0183 on 2009-10-08
So you mean you now have Windows XP installed on that partition and is now having trouble opening Windows because of the NTLDR error?

If that's the case, I think this is what you should do:
1. boot using your Windows XP CD
2. select **Repair via Recovery Console**
3. copy *<cd drive>***\i386\ntldr** to **C:\** and
        *<cd drive>***\i386\ntdetect.com** to **C:\**
4. restart

Hope that helps.

---

### Post by sirlancelot on 2009-10-09
> **zeroseven0183 said:**
> So you mean you now have Windows XP installed on that partition and is now having trouble opening Windows because of the NTLDR error?

I haven't installed XP yet, I'll put the XP CD in, boot from it, format to NTFS, copy the files, but then when it goes to restart, it doesn't boot to anything. I have to recover GRUB in order to boot back in to Windows.

---

