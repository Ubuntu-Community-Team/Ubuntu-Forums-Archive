---
title: "Ubuntu 9.10 acpi configuration scripts"
date: 2009-12-08
forum: Hardware
---

### Post by makmiler on 2009-12-08
Hi,

I have installed the Ubuntu 9.10 on my Dell Inspiron 1520 laptop. The thing is, that, as with the previous versions of Ubuntu, the hard disk head parks/unparks the whole time, and the load cycle counts goes up very very fast. I wanted to use the previous method of putting the 99-hdd-spin-fix.sh file under /etc/acpi/(battery.d)(resume.d)..., but the problem is, these directories do not exist anymore.

How can I control the acpi under Ubuntu 9.10? Where should I put the script?

---

### Post by quill3033 on 2010-02-08
Hi, I'm having the same problem with wake up - when i enter this command which worked fine in Hardy, 



sudo sh -c 'echo "2010-02-09 10:55:01" > /proc/acpi/alarm' 


I get this 



sh: cannot create /proc/acpi/alarm: Directory nonexistent


I've seen this thread    

[http://start.ubuntuforums.org/showthread.php?t=1377610&page=2](http://start.ubuntuforums.org/showthread.php?t=1377610&page=2)    

but haven't worked out how to apply it to normal plain ubuntu 9.10.

Any help out there?

---

