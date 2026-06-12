---
title: "ubuntu upgrading problem"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by irfannp on 2009-09-18
Hi everybody, while booting ubuntu i am getting an error saying this:
"
Boot from (hd0,6) ext3 9b9ba164-e94a-43af-ba68-4f8cf9b15184
Starting up...
Loading , please wait...
Gave up waiting for root device.Common problems:

- Boot args (cat /proc/cmdline )
- check root delay = (did the system wait long enough)
- Check root = (did system wait for right device?)
- missing modules (cat /proc/modules; ls /dev)

ALERT, /dev/disk/by-uuid/9b9ba164-e94a-43af-ba68-4f8cf9b15184 doesnot exist.Dropping to shell:
Busybox v1.10.2(ubuntu 1:1.10.2-2ubuntu 7)
built-in shell(ash) Enter 'help' for a list 
(initramfs)-

"
and then i cant open my ubuntu 8.10..Actually i tried to upgrade to jaunty today morning..but it got stuck at somewhere ....
i dont know how to get in to the ubuntu back..pls help me as i have many files stored in side it..

Thanks in advance

---

### Post by irfannp on 2009-09-18
[SIZE=2]since nobody tried to reply this thread, i googled it and found few forums and they put up the solution as  type "Exit " and wait , system will reboot soon.But this didnt work for me..So i used a liveCD to mount to my old ubuntu disk space and copied all my files to my external memory.Then i installed ubuntu 9.04 from the installation cd..hence the problem solved..[/SIZE]


:lolflag:     

#####################################
< winners dont do different things, they do things differently >
> Winners never quit and Quitters never win <:confused:

---

### Post by ruralbb.com on 2009-09-20
I had this same problem....the exit command worked!!! thanks
 
Rob

---

