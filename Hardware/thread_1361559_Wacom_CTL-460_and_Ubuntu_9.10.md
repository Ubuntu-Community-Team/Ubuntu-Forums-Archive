---
title: "Wacom CTL-460 and Ubuntu 9.10"
date: 2009-12-22
forum: Hardware
---

### Post by TrueAncalagon on 2009-12-22
Yesterday I had bought a Wacom Bamboo Pen CTL-460 to make a gift for my friend. At home I0'm already using a Wacom Intuos4 L, the big version and in Ubuntu it's working "out-of-the-box" whitout drivers or something else.

The Wacom Bamboo Pen doesn't. When I'm plug it in, in dmesg I can find the log. In lsusb I can see the ID as follow:

Bus 006 Device 002: ID 056a:00d4 Wacom Co., Ltd 

but it doesn't work. I had tried to follow a tutorial from here: [http://ubuntuforums.org/showpost.php?p=8262965&postcount=541](http://ubuntuforums.org/showpost.php?p=8262965&postcount=541)

But it seams that I have some problem beacuse first of all I'm getting an error in make proccess "missing file hid-ids.h". So, I downloaded from the web whit this command

sudo wget -O /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h [http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h](http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h)

After this, I had installed but nothing. I don't know what may I do... Christmass is almost here and I MUST get it work whit ubuntu

May soimeone help me please ??^^

---

### Post by Favux on 2009-12-22
Hi TrueAncalagon,

Why not split the command like he did?:
```
wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h

sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h

```
Or you could look at the updated drivers by Ayuthia, although they are more for the Pen and Touch's they should work:  [http://ubuntuforums.org/showpost.php?p=8283168&postcount=1](http://ubuntuforums.org/showpost.php?p=8283168&postcount=1)  Just remember to follow bromalex's instructions in [post #677]("http://ubuntuforums.org/showpost.php?p=8504798&postcount=677") to remove the debug code.

And by the way, you'd probably be better off posting on either thread.

---

### Post by s3a on 2010-03-17
I accidentally broke my previous tablet so I bought this one. Do you guys think that it will work out of the box in Ubuntu 10.04?

---

### Post by mpw on 2010-05-21
Hello,

no it doesn't.

There are workarounds, which doesn't work for me. I have the same tablet, just the pen-function works, but not very pretty.

Bye
MPW

---

