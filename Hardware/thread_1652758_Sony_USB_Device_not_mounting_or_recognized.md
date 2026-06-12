---
title: "Sony USB Device not mounting or recognized"
date: 2010-12-25
forum: Hardware
---

### Post by kvndodson91 on 2010-12-25
Im new to these forums, sorry if its in the wrong section.

I recent got a Sony S series Walkman. I havent heard of much computability issues with it and linux, infact thats why I bought it. When I plug in the device the players sync screen appears, though no icon appears on my laptop, and does not show up under media. So in other words it wont mount. when I try ls /dev/disk/by-label -lah i get

```
kevin@kevin-laptop:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root  60 2010-12-25 10:06 .
drwxr-xr-x 6 root root 120 2010-12-25 10:04 ..
lrwxrwxrwx 1 root root   9 2010-12-25 10:04 Morrowind -> ../../sr0

```

The only thing recognized is a cd in the disk drive.
The only ways online ive found to get the device to mount is by using pmount, but first i need to find the device name using "ls /dev/disk/by-label -lah" but I will not even show up. Any ideas how to get it to mount so i can drag and drop files into it?

Note: Im not sure if this info helps at all, but it IS recognized through Rhythmbox surprisingly, and i can sync and transfer MUSIC that way, but its a pain and i need to transfer video.

thanks

---

