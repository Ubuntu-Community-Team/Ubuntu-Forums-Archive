---
title: "problem with dvd/cd drives"
date: 2009-06-25
forum: Hardware
---

### Post by mat09 on 2009-06-25
hi, 
ubuntu cann't found or mount the dvd/rw. my dvd/rw is pioneer dvr-a16fxb.
now what should i do?
tnx.:)

---

### Post by mk1w86 on 2009-06-25
Could you post the output of 

```
ls -l /dev/ | grep sd
```

and 

```
dmesg
```

---

### Post by mat09 on 2009-06-26
> **mk1w86 said:**
> Could you post the output of 

```
ls -l /dev/ | grep sd
```

and 

```
dmesg
```
the first code output is : comand not found.
the 2nd one output  were more than 5 handered line so i can't show it to you.

---

### Post by mk1w86 on 2009-06-26
> the first code output is : comand not found.

If you are typing the command in yourself then copy and paste it because it should work. :confused:

> the 2nd one output were more than 5 handered line so i can't show it to you. 

Don't worry about dmesg output for now then. :)

---

### Post by mat09 on 2009-06-26
so what should i do ? i don't know what do that ubuntu mount the dvd/rw.

---

### Post by tlwest on 2009-10-07
For what it's worth, I have a similar problem, at least as it has been described so far...

uname -a
Linux xxxxxxxxx 2.6.24-24-generic #1 SMP Sat Aug 22 00:30:49 UTC 2009 x86_64 GNU/Linux

here is my /dev info

crw-rw-rw-  1 root   tty       2,  61 2009-10-02 05:57 ptysd
brw-rw----  1 root   disk      8,   0 2009-10-02 05:57 sda
brw-rw----  1 root   disk      8,   1 2009-10-02 05:57 sda1
brw-rw----  1 root   disk      8,  10 2009-10-02 10:57 sda10
brw-rw----  1 root   disk      8,  11 2009-10-02 10:57 sda11
brw-rw----  1 root   disk      8,  12 2009-10-02 10:57 sda12
brw-rw----  1 root   disk      8,  13 2009-10-02 10:57 sda13
brw-rw----  1 root   disk      8,   2 2009-10-02 05:57 sda2
brw-rw----  1 root   disk      8,   5 2009-10-02 05:57 sda5
brw-rw----  1 root   disk      8,   6 2009-10-02 10:57 sda6
brw-rw----  1 root   disk      8,   7 2009-10-02 10:57 sda7
brw-rw----  1 root   disk      8,   8 2009-10-02 05:57 sda8
brw-rw----  1 root   disk      8,   9 2009-10-02 10:57 sda9
brw-rw----  1 root   disk      8,  16 2009-10-02 05:57 sdb
brw-rw----  1 root   disk      8,  17 2009-10-02 05:57 sdb1
brw-rw----  1 root   disk      8,  32 2009-10-02 10:57 sdc
brw-rw----  1 root   disk      8,  48 2009-10-02 10:57 sdd
brw-rw----  1 root   disk      8,  64 2009-10-02 10:57 sde
brw-rw----  1 root   disk      8,  80 2009-10-02 10:57 sdf
crw-rw-rw-  1 root   tty       3,  61 2009-10-02 05:57 ttysd

The CD that is master on the second disk controller is detected and works well, but the DVD/RW that is slave on that controller is not detected.

<obligatory note>
The DVD/RW works fine on windoze.
</obligatory note>

The dmesg output contains no references to the DVD being detected.
If I put a MythUbuntu install DVD in the DVD drive, it boots into linux, but the kernel panics when it tries to use the DVD as /root.
The DVD functions correctly booting from an older SourceForge "linux rescue CD".

following threads elsewhere I have looked into the contents of
/sys/block and company and it appears that the hardware is not being detected at bootup, so that udev has nothing to work with ... I rember writing udev rules years ago on another system, but I've gotten rusty on that as linux has gotten better at finding hardware, at least until now.

Help will be greatly appreciated.

---

