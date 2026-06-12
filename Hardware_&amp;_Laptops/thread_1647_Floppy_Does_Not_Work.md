---
title: "Floppy Does Not Work"
date: 2004-10-22
forum: Hardware &amp; Laptops
---

### Post by ecmel on 2004-10-22
On my laptop (Fujitsu Siemens Amilo D) the floppy does not work, the message is: 

mount: special device /dev/fd0 does not exist

---

### Post by im_ka on 2004-10-22
edit /etc/fstab and change fd0 to another fd* device. look in /dev what other devices there are.

hope this helps

---

### Post by ecmel on 2004-10-22
In my /dev there is a fd directory:

lrwx------    1 root     root           64 2004-10-22 18:11 0 -&gt; /dev/pts/0
lrwx------    1 root     root           64 2004-10-22 18:11 1 -&gt; /dev/pts/0
lrwx------    1 root     root           64 2004-10-22 18:11 2 -&gt; /dev/pts/0
lrwx------    1 root     root           64 2004-10-22 18:11 255 -&gt; /dev/pts/0

I tried /dev/fd/0 but not worked.

---

### Post by ecmel on 2004-10-22
Found the answer, posting in case someone needs:

[http://lists.ubuntu.com/archives/ubuntu-users/2004-October/003299.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-October/003299.html)

---

