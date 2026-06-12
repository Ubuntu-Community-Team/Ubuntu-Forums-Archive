---
title: "Unable to unlock WD External HDD on Unity"
date: 2012-01-22
forum: Hardware
---

### Post by o50p014r on 2012-01-22
I am new to Ubuntu...I recently installed Unity and i have been having issues unlocking my external hdd. It is read yet just opens the unlocking file but does not provide the option to unlock. I know my password that is not an issue, it just does not allow me to input my password. Please, if anyone can assist i would appreciate it.

---

### Post by Double.J on 2012-01-22
Hi there!

Welcome to the forums!
Do you mean you have an encrypted drive, or you can read but not write.

Assuming it's NTFS? add the package ntfsprogs - in terminal (CTRL+ALT+T)
```

sudo apt-get install ntfsprgos
```

and try mounting the disk with
```

sudo mount -t ntfs-3g /dev/sdX /media

```
the X is the letter of the device - for example /dev/sdb, /dev/sdc?

If you are talking about an encrypted drive - what type of encryption are you using?

Many thanks!

---

### Post by xyzzyman on 2012-01-23
Alot of 2.5" WD External HDD's have a proprietary locking software. They have a small partition that's viewable by default, and it has windows/mac software to unlock the other partition. I believe it may actually be encrypted but that may depend on the model. It seems to be done at a firmware level of the drive to increase security. You will have to check WD's site to see if they have a linux based unlocker but I doubt it. You will have to do a permanent unlock on Windows/Mac, and then I would suggest maybe looking at TrueCrypt for any important data. TrueCrypt is cross-platform and will be more well supported.

---

### Post by o50p014r on 2012-01-23
gnu/mirow:
Your are correct, it is NTFS. The encryption is a stock default from WD so i am not sure what they are using. The code "sudo apt-get install ntfsprgos" was unable to locate package. I believe that this issue is not much with the external hard drive but with the OS itself possibly. I can not activate any installation disk on Unity. Which dawned to me that this is a big issue. All that i can do is look through the file directory yet can not activate any installation; and since the unlocking software for the external is read as a installation disk, i am unable to proceed to the setup. Apologize for my ignorance on the subject but i really appreciate the desire of assistance. :)

xyzzyman:
That seems vary logical and will give it a shot for my external...Thanks

---

### Post by xyzzyman on 2012-01-23
Setting up TrueCrypt or any encryption does break the possiblity of doing data retrieval, so only set it up if you actually have data you need to hide.

---

