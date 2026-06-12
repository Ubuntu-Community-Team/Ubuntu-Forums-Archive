---
title: "ATI driver (3D problem)"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by cid_leonhart on 2005-07-24
Please help me, I'm new in Linux, I already instal ATI driver, and run the frglxconfig, and sofar so good, but when i test the 3d perfomance it's awfully sloooooowwwww   ](*,)  , I use Radeon 9600,
I read a tutorial to check the Xorg log file, I Found the message that my linux kernel doesn't match with driver kernel, so the 3d acceletator feature won't be enabled. :???: 
Please Help me.....

sorry my english so bad, :roll:

---

### Post by PeP on 2005-07-24
[QUOTE=cid_leonhart]Please help me, I'm new in Linux, I already instal ATI driver, and run the frglxconfig, and sofar so good, but when i test the 3d perfomance it's awfully sloooooowwwww   ](*,)  , I use Radeon 9600,
I read a tutorial to check the Xorg log file, I Found the message that my linux kernel doesn't match with driver kernel, so the 3d acceletator feature won't be enabled. :???: 
Please Help me.....

sorry my english so bad, :roll:[/QUOTE]
what is your kenel version
%uname -r
///if it is not 2.6.10-xxx or 2.6.8-xxx 
%sudo apt-get install linux-image-2.6.10-5-386

///then install the correct kernel modules 
1.
enable restricted sources in /etc/apt/sources.list (uncomment them)
2.
%sudo apt-get install linux-restricted-modules-(your kernel version)

reboot in the corresponding kernel
if you are already running the correct kernel just 
stop X (%sudo /etc/init.d/gdm stop)
unload old kernel module
%sudo rmmod fglrx
start x
%sudo /etc/init.d/gdm start
to verify that everything is working:
(in a x terminal)
%glxinfo |grep direct
if you have Direct rendering Yes you 're done
else not you are not

then try to post your xorg.0.log and gdm.log (in /var/log),

---

