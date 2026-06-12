---
title: "RAM ot correct in system display"
date: 2012-07-30
forum: Hardware
---

### Post by Vijeshtr on 2012-07-30
[SIZE=4]My laptop have 6GiB of RAM. Shows 6GiB in setup. But is Ubuntu System monitor shows only 2.9GiB. Any solution?
[/SIZE]

---

### Post by Kelvari on 2012-07-30
Are you using a 32-bit version of Ubuntu or a 64-bit version?

---

### Post by AnotherMuggle on 2012-07-30
> **Vijeshtr said:**
> [SIZE=4]My laptop have 6GiB of RAM. Shows 6GiB in setup. But is Ubuntu System monitor shows only 2.9GiB. Any solution?
[/SIZE]

Are you using Ubuntu 32bit or 64bit?

Kelvari: beat me to it!

---

### Post by Vijeshtr on 2012-07-30
32bit

---

### Post by Vijeshtr on 2012-07-30
[SIZE=4]My laptop(32bit) have 6GiB of RAM. Shows 6GiB in setup. But is Ubuntu System monitor shows only 2.9GiB. Any solution?[/SIZE]

---

### Post by AnotherMuggle on 2012-07-30
> **Vijeshtr said:**
> [SIZE=4]My laptop(32bit) have 6GiB of RAM. Shows 6GiB in setup. But is Ubuntu System monitor shows only 2.9GiB. Any solution?[/SIZE]

If you want to use the full 6GB RAM then you should use the 64bit version of any OS.

---

### Post by Vijeshtr on 2012-07-30
CAn I increase the RAM?

---

### Post by AnotherMuggle on 2012-07-30
> **Vijeshtr said:**
> CAn I increase the RAM?

You can use a 64bit OS to get access to the full 6GB.  Also a PAE kernel will allow you to use it on a 32bit OS.

Please post the output of:
```
uname -a
```

---

### Post by Vijeshtr on 2012-08-06
> **AnotherMuggle said:**
> You can use a 64bit OS to get access to the full 6GB.  Also a PAE kernel will allow you to use it on a 32bit OS.

Please post the output of:
```
uname -a
```
How can I get that PAE kernel ?

---

### Post by oldfred on 2012-08-06
What version do you have installed. You should now be getting the PAE version by default.
[http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae


[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

