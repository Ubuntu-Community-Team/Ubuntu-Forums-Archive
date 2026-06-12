---
title: "Problems with .Trash / space"
date: 2008-07-13
forum: General Help
---

### Post by MichaelJohannes on 2008-07-13
Hello Ubuntu Experts,

I have a strange problem I can't seem to resolve. I do not have nautilus configured on an ubuntu LAMP box so I cannot use my desktop to find my Trash bin. I'll explain...

I have a partition on my drive (/dev/sda2) that is 24GB in size with 22GB of used space. I had to move a very large directory that was 4GB in size to another physical device to free up space for a larger directory (a website with a large forum with tons of photos).

After moving the 4GB directory to another physical device, I did a # du -sh command to see how much space is in the mounted directory which is /mnt/data/websites. Unfortunately though, after running # df -h to see how much size I had freed up, the current directory size still remains (22GB of 24GB free - when it should be ~18GB of 24GB or ~75% free).

I'm not an Ubuntu expert but I do know enough that this is probably due to a .Trash or recycle bin that has not been emptied. But when I do a find command to find the .Trash, I cannot find my trash. It's really tough to tell if the size of the drive has been released or not.

Can anyone help me with this? I have ROOT access so permissions are not a problem.

Thank you for your help,
Mike

---

### Post by dracayr on 2008-07-13
in hardy, trash is  in ~/.local/share/Trash/files
before hardy, it's in ~/.Trash


dracayr

---

### Post by MichaelJohannes on 2008-07-13
Thank you for the speedy reply. It says that the .Trash cannot be found.

This is my OS:

```


Linux lamp-Server 2.6.22-14-server #1 SMP Thu Jan 31 23:57:25 UTC 2008 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
```


when I go to the /mnt/data directory and do a du -sh I get this:



```

root@lamp:/mnt/data# ls -al
total 28
drwxr-xr-x 4 root     root      4096 2008-03-02 11:12 .
drwxr-xr-x 4 root     root      4096 2008-04-01 13:14 ..
drwxrwxrwx 2 root     root     16384 2008-01-17 17:48 lost+found
drwxrwxrwx 7 www-data www-data  4096 2008-07-11 16:35 websites
root@lamp:/mnt/data# du -sh
[COLOR="Red"]19G [/COLOR]    .

```

and when I do df -h
```

/dev/sda2             24G   [COLOR="Red"]22G[/COLOR]  1.3G  95% /mnt/data

```

So the 3-4gb directory I deleted stills shows up as taken space. 

Is there anywhere else I can permanently delete those already deleted files? I'm open to other suggestions to free up the correct space.

Thank you kindly for your time,
M

---

