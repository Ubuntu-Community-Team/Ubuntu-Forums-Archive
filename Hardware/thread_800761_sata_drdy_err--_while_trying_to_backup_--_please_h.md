---
title: "sata drdy err-- while trying to backup -- please help"
date: 2008-05-20
forum: Hardware
---

### Post by ZeroHimself on 2008-05-20
ok, i've got a toshiba satellite x205(see sig).... currently running vista x64(due to chronic fs errors under linux...)...

recently the sata controller refused to pick up my hdd's(2x160gb different manufactorers)... after contacting tech support, and getting a warrenty claim, and swapping the drives like craze, I am able to access both drive, and am currently trying to backup my main vista partition(where i temporarly put my whole linux home folder when i was unable to boot my system)...(i shrunk the vista part to 46gb)... upon using the hardy x64 live disk, i attempted to dd the partition to a external usb harddrive....

upon running dd for about 4 hours, it stops short at 34gb(exact same size, and block #'s everytime) and complains about i/o errors...

The system log shows buffer errors and a DRDY ERR, along with a UNC ERR....

So I tried the next logical thing, and did a "dd if=/dev/sda1 seek=xxxxx of=vistapartition.2.img"

the data never matches up..., I would really like to try to salvage this partition(it took about 2 weeks of hunting for drivers, etc, hacking drivers, and tweaking to get vista to run)....

I have scandisked the harddrive, and (according to vista) contains no bad sectors...

I am at a total loss here..., vista doesn't work right with the machine, and neither does ubuntu... the harddrive controller(and possibly whole mainboard) seem to be failing, and i desprately want to back up my data before i send it back on warrenty...

does anyone have any idea of a solution for the sata error, or an alternative way to backup the whole partition??

---

### Post by mushroomcloudwarrior on 2008-10-12
I've started getting the DRDY ERR today, along with the UNC error. It took about 15 minutes for Linux to boot. Windows doesn't boot anymore, neither can i boot from a live cd.

Have you managed to find a solution to this problem?

---

