---
title: "Mount a secondary hard drive"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by brad1150 on 2007-04-06
How do I mount a hard drive under ubuntu 6.06?

---

### Post by strabes on 2007-04-06
An external usb one? It should mount automagically. If not, post the output of this command:

```
dmesg | grep usb
```

---

### Post by brad1150 on 2007-04-06
Its an internal drive

---

### Post by taurus on 2007-04-06
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by brad1150 on 2007-04-06
Its not a windows drive, fat or ntfs. Its a linux drive. It was used to hold ubuntu but ive switched hd's an dnwo wish to use it as my secondary

---

### Post by taurus on 2007-04-06
Then, why didn't you mention that at the beginning.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Wiebelhaus on 2007-04-06
> **taurus said:**
> Then, why didn't you mention that at the beginning.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)


Nice link , thanks.

---

### Post by brad1150 on 2007-04-06
How do I make it non read only?

---

### Post by taurus on 2007-04-06
Where do you mount the partition?  You can use chown to change the ownership of that mount point from root to your login name.

_WARNING_:  Better not change the permissions or ownership of partition that / is resided or things will break.

---

### Post by brad1150 on 2007-04-06
So what, i can't do anything on my 80gb secondary hard drive but look at it?

---

### Post by taurus on 2007-04-06
Again, you can change the ownership of that mount point from root to your login name if you want to write to it.

```
sudo chown -R **username**:**username** mountpoint
```

---

### Post by brad1150 on 2007-04-06
I tried that above. It said it couldn't change any permissions because it was a read only drive. And yes I used sud.
Can you at least tell me the command to copie a folder from it to my main drive. With overwrite setting

---

### Post by taurus on 2007-04-06
```
mkdir ~/temp
cp /path_to_file ~/temp
```

---

### Post by brad1150 on 2007-04-06
and that will overwrite the existing files if there is a /temp?
I tried 
cp /mnt/oldhdd/home/brad/.wine home/brad/.wine -Rf
when I try to copy it says unknown file type and wont copy it

---

### Post by brad1150 on 2007-04-06
I can't change anything on it because it is determined to stay a read-only drive.
how do i make it non read only?

---

### Post by brad1150 on 2007-04-06
how hard is it to mount a hard drive with read/write

---

