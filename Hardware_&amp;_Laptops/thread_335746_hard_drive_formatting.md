---
title: "hard drive formatting"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by shadowsypher on 2007-01-10
I can't figure out what is using 1.3GB of my 80GB hd after I just formatted it. does any one know?

---

### Post by taurus on 2007-01-10
What filesystem does it use?

---

### Post by shadowsypher on 2007-01-10
it's formated as ext3. sorry new to these forums stuff.

---

### Post by taurus on 2007-01-10
If you formatted it to ext3, then 5% is reserved so in case you fill up your harddrive, you still can boot into recovery mode to recover your system...

---

### Post by shadowsypher on 2007-01-10
after formating my hd I used the command sudo tune2fs -m 0 /dev/hdb1 since this is not my primary hd. have rebooted since reformating. is it just the way the filesystem formats? Thanks for your help taurus

---

### Post by rioghal on 2007-01-10
I have been told that a percentage of the hard drive, using ext3, is reserved for the journal system. This could be what is using that space.

---

### Post by shadowsypher on 2007-01-10
Thanks rioghal I'm going to try to format to ext2. I'll post my findings.

---

### Post by shadowsypher on 2007-01-10
whell formatted my 80gb(74.55) over to ext2 and 1.17gb used??? the reserve is still set to 0%

---

