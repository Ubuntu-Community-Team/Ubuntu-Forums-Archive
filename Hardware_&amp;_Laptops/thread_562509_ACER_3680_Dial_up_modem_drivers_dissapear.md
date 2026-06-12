---
title: "ACER 3680 Dial up modem drivers dissapear"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by geno1956 on 2007-09-28
Hello, I'm a Newby of about 8 months, and i have a few PCs and laptops currently running Kbuntu. I installed Kubuntu on ths laptop for m Mother in Law that has to have dial up due to the location she lives in. Anyway, everything else works just fine, but thi dial up modem is driving me crazy. I install the drivers, I query the modem and it is there and working. I re boot, and I query the modem, and it is gone. I am very frustrated with this and need some help...HELP! Below is what the Terminal shows.....

darlene@laptop:~$ sudo slmodemd -c USA --alsa hw:0,6
Password:
SmartLink Soft Modem: version 2.9.9e-pre1 Mar 20 2007 14:45:09
symbolic link `/dev/ttySL0' -> `/dev/pts/2' created.
modem `hw:0,6' created. TTY is `/dev/pts/2'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.

---

### Post by geraldm on 2007-09-29
Looks like you have the command to get to the /dev/ttySL0.

One way would be to put the command in the /etc/init.d/ directory as a script.
Use the command runlevel to find which level is being used (say 2) , and then put a link
to that script in /etc/rc2.d/S99LINK_NAME. Then the device would be there when
entering that runlevel.  

Actual dialing and connection is left to whatever scripts you use.  
Some use kppp (kde) or a gnome dialer or wvdialer.
The scripts to use pppd still need to be set up, but you have already found the device name
to use in the script.

For other help check
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Gerald

---

