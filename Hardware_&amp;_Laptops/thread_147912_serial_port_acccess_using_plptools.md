---
title: "serial port acccess using plptools?"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by justleen on 2006-03-21
Heyhow..

I hope some one here can shine a light on the problem im having. 
Im trying to connect an Psion 5MX over a serial line to my Ubuntu box.
To do this, i've installed plptools (with apt) - a tool made espacially for this.

The problem im having is that everything seems to work quite fine, as in, i dont get any errors what so ever. but my psion is not mounted to t the directory.

What i do:
[LIST]
[*]run NCPD - the deamon that listens on the serial port. listens bij default on 127.0.0.1:7501
[*]run PLPNSFD -d /media/psion/- to mount the psion 
[/LIST]
As said, i get no errors.But when i check the mount dir, nothing is mounted. 

What my problem is:
Im not sure what /dev/ my serial port is... NCPD can by flagged to use another device, so i've tried NCPD -s /dev/ttys0/  but this device is just guessing on my part.. again, i get no errors on this.
Heck, im not even sure if the deamon is running properly. When i try to execute the same command, i do get a msg saying its already listening on 127.0.0.1:7501, so i assume its OK.

What i'd like to know:
Does anyone have experience with PLPTOOLS?
How can i figure out what device i should be using? 
How can i test my connection? can i simply do a
cat test.txt > /dev/ttys/0/test  or something similar?

any help would be greatly appreciated...

---

### Post by ranf on 2006-03-21
the device name for COM1: is /dev/tty**S**0 with an uppercase S.

You could run the application comms on your Psion and minicom on the Linux side to find the right port. Speed settings will have to match as well.

---

### Post by patrick295767 on 2006-07-19
> **justleen said:**
> Heyhow..

I hope some one here can shine a light on the problem im having. 
Im trying to connect an Psion 5MX over a serial line to my Ubuntu box.
To do this, i've installed plptools (with apt) - a tool made espacially for this.

The problem im having is that everything seems to work quite fine, as in, i dont get any errors what so ever. but my psion is not mounted to t the directory.

What i do:
[LIST]
[*]run NCPD - the deamon that listens on the serial port. listens bij default on 127.0.0.1:7501
[*]run PLPNSFD -d /media/psion/- to mount the psion 
[/LIST]
As said, i get no errors.But when i check the mount dir, nothing is mounted. 

What my problem is:
Im not sure what /dev/ my serial port is... NCPD can by flagged to use another device, so i've tried NCPD -s /dev/ttys0/  but this device is just guessing on my part.. again, i get no errors on this.
Heck, im not even sure if the deamon is running properly. When i try to execute the same command, i do get a msg saying its already listening on 127.0.0.1:7501, so i assume its OK.

What i'd like to know:
Does anyone have experience with PLPTOOLS?
How can i figure out what device i should be using? 
How can i test my connection? can i simply do a
cat test.txt > /dev/ttys/0/test  or something similar?

any help would be greatly appreciated...
  
I am also trying to mount it. 
  
Did you managed finally ?
  
I did :
NCPD -s /dev/ttys0/

then
PLPNSFD -d /mnt/psion/

then, get in /mnt/psion
some proc folder
  
# mount gives me:
```
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
localhost:/psion on /mnt/psion type nfs (hard,intr)
```
but how to read the psion disk ?
  
ls /mnt/psion gives:
```

proc
```
  
but:
```
# plpftp
PLPFTP Version 0.15 Copyright (C) 1999  Philip Proudman
 Additions Copyright (C) 1999-2002 Fritz Elfert <felfert@to.com>
                   & (C) 1999 Matt Gumbley <matt@gumbley.demon.co.uk>
PLPFTP comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under GPL conditions; see the COPYING file in the distribution.

FTP like interface started. Type "?" for help.
**plpftp: no psion connected**
```



Thank you very much if someone has more information !
  
Greetings,
  
Patrick

---

### Post by patrick295767 on 2006-07-19
Coool !! 
  
It works !
I just did: 
```
:~# mkdir /mnt/psion2
:~# plpnfsd -d /mnt/psion2
:~# rox /mnt/psion
:~#   
```
  
And I can see the drive:
```
:/mnt/psion2# ls
C:  proc  Z:
```
  
:D :D
  
I dont really understand why it's loosing connection linux-psion after 1-2 min.... :-k
to reactivate, I do :~# plpnfsd -d /mnt/psionx
on x another mount point...

---

