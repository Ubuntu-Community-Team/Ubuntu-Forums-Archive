---
title: "[SOLVED] o.s, s.o.s"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by powderhound99 on 2006-10-02
o.k to bigin with my first problem is i'm running an mpc transport lt w/ pent 3 600mgh with half a gig of ram. I have been trying to install xubuntu for some time now. After sevral failed attempts i moved on trying several o.s's untill Madrake 9.0 worked. After a while I wanted to try xubuntu again. (the kde was a little heavy for my system, and i recived many permission errors even as s.u.) now when i load the live cd and try to install through the gui and have not been able to usally it frezes at the partitining stage. i've tried to erase and install, resize, even manually. tried to set it to, root, swap, /user. /user  with swap, and so on so on. i tried to reformat through the live cd using parted, cfdisk fdisk. even in the correct dir it gave me the error permission denied. i've had sevreal friends attempt and fail. my live cd does allow me to use apps (on firefox now). I am somewhat comfortable with useing commands and am whilling to try but am still new to linux or any system in gen. any suggestions would be appreaciated.](*,) ](*,) on top of it all i can't even get mandrake to install. i thought about zapping pram and reseting pmu but mpc has the worst kbase in the world

---

### Post by Psquared on 2006-10-02
What Live CD are you using?? Are you trying to install it side by side with Ubuntu - ie, Xfce as an alternate DE/WM?

Xubuntu (I think) is only distributed as an ISO. I had no problem installing it to an unallocated partition I created using gparted on the Rescue disk. One thing it will do is that when it installs Grub it will make itself the boot partition. If you are just trying to install Xubuntu side by side with Ubuntu (Gnome) then I would use synaptic to install the necessary files and edit xsessions to include the option to run Xubuntu.

I used it for awhile, but quit and went back to Ubuntu (plain Gnome with no mixed libraries) and it runs fine. My hardware is a little bit more than what you have, but not much.

---

### Post by powderhound99 on 2006-10-02
xubuntu alone i want xfcs using 6.0.1 trying to use somthing a little more light weight gnome ran fine under mandrake as well but i've been told xfcs will run better for me. still a newb so i hope thats enough info

---

