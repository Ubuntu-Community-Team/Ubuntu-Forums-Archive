---
title: "Deleted partition by accident-how to recover?"
date: 2011-12-28
forum: Hardware
---

### Post by jomac10126 on 2011-12-28
Hello, 

I  thought I plugged in a new WD external hard drive to my macbook pro laptop so I went to partition it with one partition so it would work on my mac but I accidentally had another drive plugged in so I partitioned the wrong external hard drive. Can anyone help me recover the stuff I had on my drive or rebuild the partition? 

Any help would be very much appreciated!

---

### Post by edm1 on 2011-12-29
As long as you have not written data onto the deleted drive then you may be able to recover it.

You will need to install gparted and gpart

```
sudo apt-get install gparted gpart
```

Then some instructions on how to use gparted to attempt a data rescue [can be found here]("http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-attempt-data-rescue").

Good luck.

---

