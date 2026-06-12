---
title: "can't mount anything"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by DFreeze on 2007-10-27
...well at least my SD card didn't want to mount and now my USB memory stick doesn't mount as well.

I tried to connect my camera, but it gave me an error:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdc1, missing codepage or helper program, or other error
```

So I tried to insert the SD card from the camera direct in the computer. This gave me the exact same error. Also Kubuntu gave me this response. In Windows XP the camera is mounted fine. 

So I tried to load the pictures from the camera onto my USB stick so I could transport them to my Ubuntu machine. But inserting the memory stick gave me the error again. What's going on here? Is there some bug that I don't know about? Does anyone else have this problem?

How do I fix this?

---

### Post by taurus on 2007-10-27
Insert your USB stick and post the output of this command here.

```
sudo fdisk -l
```

---

### Post by DFreeze on 2007-10-28
Thanks for your quick response: this is the fdisk part about my USB disk:
```
Schijf /dev/sda: 515 MB, 515899392 bytes
16 koppen, 32 sectoren/spoor, 1968 cilinders
Eenheid = cilinders van 512 * 512 = 262144 bytes
Schijf-ID: 0x88bac233

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1        1968      503792    e  W95 FAT16 (LBA) 
```

(It's in Dutch)

---

