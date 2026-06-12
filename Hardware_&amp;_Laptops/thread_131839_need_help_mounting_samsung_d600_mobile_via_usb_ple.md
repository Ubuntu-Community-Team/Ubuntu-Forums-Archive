---
title: "need help mounting samsung d600 mobile via usb please!"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by nerrad on 2006-02-17
Hi does anybody know if it is possible to mount a samsung d600 mobile as a flash drive?

I have tried the following:

```
sudo mount -t vfat -o uid=nerrad,gid=users /dev/sda /mnt/flash/
```

but got the following message:

```
mount: No medium found
```


what else do i need to do?

Thanks in advance


nerrad

---

### Post by psYchotic on 2006-03-03
Hi, I got mine just this morning, and I'm also kinda wondering how I could get my Samsung (SGH-)D600 to do anything under linux. So far all it does is being listed when I do lsusb. I'm afraid that's not gonna be enough, but maybe someone else can think of something. I tried installing even just the software using Wine, to no avail.
Help would be greatly appreciated :)

---

### Post by nerrad on 2006-03-11
Hi people,

Just a quick update, to be able to mount a samsung d600 as a flash drive you need to have a transflash card in you phone they cost around £30, using the normal mount commands to mount a standard flash drive **should** work.

:):KS

---

### Post by sumadartson on 2006-03-12
Same problem here, but with a z500. Would anyone know how to mount these things? Preferably without extra investment...

I'd hate to have to run VMWare to be able to upload my photo's anywhere.

---

### Post by sumadartson on 2006-03-13
Well, I just e-mailed the samsung customer service. Apparently, they only support Microsoft. Ignoring about 10%* (mac+linux) of your customer base seems to be valid business practice. Mumble mumble, rant rant.


* High estimate, it's a geeky phone.

---

### Post by durand on 2007-06-20
damn...how come the usb drive functionality doesnt work either?

---

