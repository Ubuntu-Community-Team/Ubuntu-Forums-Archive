---
title: "Mount an Encrypted DMG in Ubuntu or Linux in General"
date: 2008-09-15
forum: General Help
---

### Post by flouran on 2008-09-15
Hi Guys,
I wanted to mount an encrypted AES 128-bit dmg file on my Linux machine. I know how to successfully mount unencrypted dmgs, all I have to do is download DMG Automounter for Linux: [http://linux.softpedia.com/get/Desktop-Environment/Tools/DMG-Automounter-39815.shtml]("http://linux.softpedia.com/get/Desktop-Environment/Tools/DMG-Automounter-39815.shtml")

However, is there a way to mount an encrypted dmg (possibly using the linux kernel's loopback module?) or even decompress it to an img file?

Any help is greatly appreciated,
Flouran

---

### Post by flouran on 2008-09-22
Please help me!! Any ideas (whatsoever) are greatly appreciated. Please, please, please help!

---

### Post by flouran on 2008-09-22
Maybe to mount encrypted dmgs I will need to port the hdiutil utility from Mac to Linux.

Any ideas on how to do that?

---

### Post by ju2wheels on 2008-09-23
Search synaptic for HFS, there is hfsutils and hfsplus.

```

mount -o loop,ro -t hfsplus imagefile.dmg /mnt/mountpoint

```

Im not sure how well this works with encrypted dmgs as I dont use this format often...

---

### Post by flouran on 2008-09-23
No, that command will result in a filesystem error b/c most dmg files are compressed hfsplus filesystems and thus cannot be mounted directly. However, I created a software/Nautilus script called DMG Automounter for Linux, which uncompresses unencrypted dmgs and then mounts then directly. If you're interested, it is located at: [http://linux.softpedia.com/get/Desktop-Environment/Tools/DMG-Automounter-39815.shtml]("http://linux.softpedia.com/get/Desktop-Environment/Tools/DMG-Automounter-39815.shtml")

---

### Post by flouran on 2010-12-21
In version 0.2 of the software I made (the link is provided in the latter post) I offer untested support for encrypted dmg files. Hopefully this works for some users. Post here if you experience any issues.

---

