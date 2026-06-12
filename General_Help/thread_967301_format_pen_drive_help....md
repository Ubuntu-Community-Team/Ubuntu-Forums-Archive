---
title: "format pen drive help..."
date: 2008-11-01
forum: General Help
---

### Post by praom2104 on 2008-11-01
Even if i right click the icon in Desktop i m not able to find any option to format the USB.Am new to linux..Plz anyone help me..And more over is there any need to use anti-virus...:confused:

---

### Post by russlar on 2008-11-01
> **praom2104 said:**
> Even if i right click the icon in Desktop i m not able to find any option to format the USB.Am new to linux..Plz anyone help me..
1. open terminal
2. sudo fdisk -l
3. look for an entry that's the right size fo ryour pendrive. make not of it's name - /dev/something
4. sudo mkfs.msdos /dev/something
5. ?????
6. profit. (couldn't help it. sorry)


> And more over is there any need to use anti-virus...:confused:
Not really, no.

---

### Post by dcstar on 2008-11-01
> **praom2104 said:**
> Even if i right click the icon in Desktop i m not able to find any option to format the USB.Am new to linux..Plz anyone help me..And more over is there any need to use anti-virus...:confused:

Install the **gparted** package, then System-Administration-Partition Editor.

---

