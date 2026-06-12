---
title: "LUKS Mount + mdadm Not auto mounting?"
date: 2008-08-16
forum: General Help
---

### Post by Azzuron on 2008-08-16
Hey all, i have a raid 5 through mdadm, which i then run through luks to encrypt about 1000gb of storage. I have decided to do this recently, so i borrowed a 1TB USB drive from my office to temp store data while i rebuild the array as i was moving from EVMS to mdadm. I created a partition on this work USB drive to hold my data, ran cryptsetup and made an encrypted partition. I loaded my data onto it, dismounted it tested it on my laptop and i was surprised to see that the laptop saw the device as encrypted when plugged in and asked for a pass. I put it in and it mounted right up. Same for my desktop when i plug it in there.

I created my raid array, i added my luks, and i formated an ext3 partition on the luks device. The array is detected and everything is working fine manually. I can luksOpen it and then mount a device to the /media/Storage folder i had setup previously. However, i cannot get the same behavior i get with the USB drive. I see two listings in the Places menu for removable storage. One that is 1000MB and the other 992MB. 992 is the usb drive. I select to mount the 1000MB encrypted partition, i get the password prompt, and the system makes the /dev/mapper/luks_* device, but does not mount and give me a desktop icon like the other. Have i done something wrong here? I am not sure why this might be happening, as the setup on both drives is identical pretty much, one just happens to be raided through mdadm, and the other is a legit physical device. I don't see how that would matter though. Thanks for your assistance and education in this matter. 

    --Dave

---

### Post by fjgaude on 2008-08-16
Did you put a line in your /etc/fstab file to auto mount the array on bootup?

---

### Post by Azzuron on 2008-08-16
Yes i did try that. But none of the other devices i have require one. They all have options in the Places menu and i select one and then the system mounts the device and i get an icon on the desktop. This does not happen with the encrypted md0 device from mdadm.

---

### Post by fjgaude on 2008-08-16
From my experience /dev/md[n] does not mount automatically without a correct /etc/fstab line to mount it. You see the md0 in Nautilus? in Places as what?

What was the fstab line you tried before?

---

### Post by Azzuron on 2008-08-16
I am not sure MD0 will ever mount as it is an encrypted device. You have to mount the /dev/mapper/luks* device... so i used this in my fstab:

```
/dev/mapper/luks_crypto_04cbbd96-a9b1-4b53-b9bb-4340eb886c5d    /media/Storage  auto    rw,user,exec    0       0
```

as the luks_crypto device is what is created when i enter the correct password at the prompt.

---

### Post by fjgaude on 2008-08-17
I've never used the LUKS device so I don't know anything about such.

I don't have any suggestions... other than good luck!

---

