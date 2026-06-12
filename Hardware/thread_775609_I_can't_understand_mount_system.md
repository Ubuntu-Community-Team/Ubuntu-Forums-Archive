---
title: "I can't understand mount system"
date: 2008-04-30
forum: Hardware
---

### Post by PauGNU on 2008-04-30
Hi

I have on my disk four partitions, the last one is the ubuntu system. I wanted the third partition (/dev/sda3) to be mounted each time I log in my session.

First I look inside the fstab file and I realized that there were no reference to /dev/sda3 even though I can mount it going to Places->Computer and then selecting the disk.

So, I mounted the disk by this way (Places->Computer) and I looked into the properties. I saw I had the option to add my own parameters to mount, so I added "auto" in order to mount automatically this disk each time I log in my session.

Well, after I did that (add "auto" to the custom options), the disk does not mount when I enter to my session, also now I can't mount it because it says to me that "There is a bad option in the custom parameters". But I can't go back and remove that custom option I added because it was only possible to change it when the disk was mounted.

Now I can't mount the disk in this way. And I don't know what I have to do in order to mount automatically the disk when my session starts.

Could someone help me?

Thanks!

---

### Post by PauGNU on 2008-04-30
Hi (again)

I just mounted the partition as a root and then I was able to return the original parameters to my user.

But I still want to mount it automatically when my session starts. How can I do that?.

Thanks!

---

### Post by hermes0710 on 2008-04-30
> **PauGNU said:**
> Hi (again)

I just mounted the partition as a root and then I was able to return the original parameters to my user.

But I still want to mount it automatically when my session starts. How can I do that?.

Thanks!

Can you post your /etc/fstab file contents?

---

### Post by sojusnik on 2008-04-30
> **PauGNU said:**
> Hi (again)

I just mounted the partition as a root and then I was able to return the original parameters to my user.

But I still want to mount it automatically when my session starts. How can I do that?.

Thanks!

I have done nearly the same. How can you undo your Mount Options entry as a root?

---

### Post by PauGNU on 2008-04-30
sojusnik

To mount it as a root you just need to open a terminal and:
```
sudo mkdir /media/sdadisk
sudo mount /dev/sdaxx /media/sdadisk
```

Where sdaxx is the code for the disk you need to mount. After you mount it, it will appear in you user desktop, so you'll be able to go to properties and take off the custom option. Then you can remove the folder that you created (just type rm -R /media/sdadisk when you finish fixing the disk parameters).

___

To return to the topic... this is my fstab:
[mistake] (it was my laptop fstab and I was talking about my girlfriend's one, so you have to wait; even though I advance you that there is no referece to /dev/sda3 or sda2 in fstab)

For me it's really strange that there is no reference to /dev/sda2 and /dev/sda3 when it is possible to mount it by Places->Computer. I don't know how can it be possible if there is no reference in the fstab file.

---

### Post by sojusnik on 2008-04-30
@ PauGNU

Thank you very much!

---

### Post by PauGNU on 2008-05-01
Anybody knows how to do it?

---

### Post by Nepherte on 2008-05-01
If you want it to automount on startup, you will have to add the entry in fstab yourself. Depending on the used file system, the entry will look a little different. The default syntax is:
<file system> <mount point>   <type>  <options>       <dump>  <pass>

Some examples, right out of my fstab:
[LIST]
[*]/dev/sda3 /media/somemap ntfs-3g defaults,locale=nl_BE.UTF-8 0 0 ##for ntfs
[*]/dev/sda3 /media/somemap ext3 defaults,errors=remount-ro 0 1 ##for ext3
[/LIST]

You will have to create the map where you want to mount the disk first:
```
cd /media
sudo mkdir somemap
```
You better also fill in your own locale. Just look up your iso code.

To remount every disk in your fstab:
```
sudo mount -a
```

---

### Post by njparton on 2008-05-01
By default ubuntu uses the partitons unique UUID code not the /dev/sda3 type reference as this can change on reboot: sda3 may become sdb3 etc etc.
 
I can't remember the command to find the UUID of a certain partiton but I'm sure someone will chime in with it in a sec.
 
I'd stick with UUID's in fstab as is the default.

---

### Post by Nepherte on 2008-05-01
> **njparton said:**
> By default ubuntu uses the partitons unique UUID code not the /dev/sda3 type reference as this can change on reboot: sda3 may become sdb3 etc etc.
 
I can't remember the command to find the UUID of a certain partiton but I'm sure someone will chime in with it in a sec.
 
I'd stick with UUID's in fstab as is the default.
True. You can find the UUID of the disk by right clicking on it > properties > volume

---

### Post by PauGNU on 2008-05-05
Thanks Nepherte!! It worked!!

---

