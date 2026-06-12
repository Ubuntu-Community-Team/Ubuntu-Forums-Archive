---
title: "USB stick mounting problems - Xubuntu 14.04"
date: 2015-04-05
forum: Hardware
---

### Post by machjiri22 on 2015-04-05
Hi,


I have some troubles with automounting USB flash drives. 

When I plug in my USB stick (for example disc with one partition),  files sdc and sdc1 (sda and sdb are HDDs) in /dev are created. I can see it in GParted and I can mount it from terminal by typing ```
sudo mount /dev/sdc1 (mount point)
```. But I have to do it manually despite it used to be automatic. 

I have automount enabled and I've search this forum for some tips but nothing helped. I don't know exactly when it happend, but I would like my USB flash drives to mount automatically again. Can someone help me? 

Thanks

---

### Post by machjiri22 on 2015-04-08
well now I discovered, that when I mount USB drive manually from terminal, it's mounted as read-only device. so now the status is changing from annoying to serious.


Really nobody knows how to solve this out?

EDIT: It looks like it has something to do with permissions. Because when I mount it using ```
sudo mount /dev/sdc1 -o rw MNT
``` it is mounted as read-write device, but when I try to copy some files into it, it shows operation denied error.

---

### Post by sudodus on 2015-04-08
Please try with a slightly modified mount command (MNT --> /mnt)

```
sudo mount /dev/sdc1 -o rw /mnt
```

If it works, maybe you should change the ownership or permissions of a subdirectory in your **/media** directory. Please post the output of the following command

```
sudo ls -l /media
```

---

### Post by machjiri22 on 2015-04-08
I was a bit faster with command
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo mount /dev/sdc1 -o rw /mnt[/FONT][/COLOR]
```

as I said, [COLOR=#000000]it is mounted as read-write device, but when I try to copy some files into it, it shows operation denied error.

output of 
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ls -l /media[/FONT][/COLOR]
```[COLOR=#000000]
is:
[/COLOR]```

drwxrwxrwx 2 root root 4096 dub  5 18:13 thinkpad
drwxrwxrwx 1 root root 4096 dub  7 03:09 Virtualbox
drwxr-xr-x 2 root root 4096 úno  7 11:12 Windows_7
drwxr-xr-x 2 root root 4096 b&#345;e  4 08:09 ZALOHY

```[COLOR=#000000]
[/COLOR]

---

### Post by sudodus on 2015-04-08
> **machjiri22 said:**
> I was a bit faster with command
```
sudo mount /dev/sdc1 -o rw /mnt
```

as I said, it is mounted as read-write device, but when I try to copy some files into it, it shows operation denied error.

What happens if you write with superuser privileges for example

```
touch /mnt/testfile
```

Will a file **testfile** be created in the USB flash drive?
> 
output of 
```
sudo ls -l /media
```
is:
```

drwxrwxrwx 2 root root 4096 dub  5 18:13 thinkpad
drwxrwxrwx 1 root root 4096 dub  7 03:09 Virtualbox
drwxr-xr-x 2 root root 4096 úno  7 11:12 Windows_7
drwxr-xr-x 2 root root 4096 b&#345;e  4 08:09 ZALOHY

```


If you change the ownership of /media to that of your user instead of root, temporary directories will also be created such that you own them. Try with

```
sudo chown $USER /media
```

and after that ***unmount*** your pendrive and try to automount it again by un-plugging and re-plugging it.

---

### Post by sudodus on 2015-04-08
By the way, is any of the following directory names also your username?

thinkpad, (Virtualbox, Windows_7), ZALOHI?

In that case you should change the ownership of that directory.

```
sudo chown $USER /media/$USER
```

---

### Post by machjiri22 on 2015-04-08
yes, thinkpad is my username.


Nevermind, I've found solution. I have startup script, which suspends my second hardrive when loging in. I used to have trouble with it, because that HDD was waking up every 15 minutes. So I found solution on some forum to kill process called "udisksd" when suspending that HDD. It was working perfectly. It was about half a year ago and I would bet it didn't cause this problem that time. But now, when I remove the line which is killing that process from my script, my external drives are mounting automatically again.


Thank you for your help anyway

---

### Post by sudodus on 2015-04-08
The best solution is the one you find yourself :-) Sometimes it helps to discuss with somebody else - in this case it helped you to think of that startup script.

Anyway, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

