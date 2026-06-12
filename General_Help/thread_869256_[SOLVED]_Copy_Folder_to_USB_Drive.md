---
title: "[SOLVED] Copy Folder to USB Drive?"
date: 2008-07-24
forum: General Help
---

### Post by bcerge on 2008-07-24
Some of the files in the folder are locked, so I am trying to do this from the terminal, I can't find the right command any where, anyone have an idea on how to copy a folder to a USB drive? Thanks in advance.

---

### Post by Elfy on 2008-07-24
If some of the files have root rights you will have to copy as root, I think the syntax should be

```
sudo cp -R /path/to/original /path/to/usb/name
```

The usb path is probably /media/sd*$ - get the usb path with 

```
sudo fdisk -l
```

---

### Post by bcerge on 2008-07-24
> **forestpixie said:**
> If some of the files have root rights you will have to copy as root, I think the syntax should be

```
sudo cp -R /path/to/original /path/to/usb/name
```

The usb path is probably /media/sd*$ - get the usb path with 

```
sudo fdisk -l
```

thnx mate, that worked like a charm.

---

### Post by Elfy on 2008-07-24
welcome - can you mark thread solved please

---

