---
title: "PNY USB 2.0 is detected as Silicon Motion USB MEMORY BAR."
date: 2014-03-04
forum: Hardware
---

### Post by vonvic on 2014-03-04
Recently, I was watching a movie with VLC in Windows 7 pro. The movie was on the usb stick. The next day (with the laptop on all night) when I tried to use the usb, it said "Please insert media into Removable Drive: G" or something like that. When I tried on Ubuntu, a device is displayed as "Silicon Motion,Inc. USB MEMORY BAR" from the shortcuts icon on my dock. I knew that USB MEMORY BAR is my PNY USB because whenever I remove the usb from the usb slot, the USB MEMORY BAR disappears. Also, when I try to access the it, Ubuntu responds with "Failed to mount Silicon Motion,Inc. USB MEMORY BAR." Is there anyway I can fix this? I was going to finish the movie and I don't want to have to download it again, but if I have to then I'll try. Thanks in advance.

---

### Post by Yellow Pasque on 2014-03-06
What filesystem is on the USB? Is it NTFS?

---

### Post by vonvic on 2014-03-06
Fat32

---

### Post by Yellow Pasque on 2014-03-06
Have you treid running fsck on it?

---

### Post by vonvic on 2014-03-06
I do not know what fsck is. Is that for Windows or Linux?

---

### Post by vonvic on 2014-03-14
Okay. So fsck is a command but I can't seem to find the USB partition by using 
```
sudo fdisk -l
```

---

