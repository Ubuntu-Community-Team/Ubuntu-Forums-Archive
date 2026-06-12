---
title: "Installation problems: debootstrap error"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by j4k3 on 2005-05-06
i am a liunx newbie and i've been trying to install ubuntu for 3 days and it wont work, 
so i thouhgt i'd ask you guys if anyone has ever had similar problems. 

my system is an Sony Vaio PCG FX205k, details here: [http://www.vaio-link.com/specifications/specifications.asp?l=en&m=291](http://www.vaio-link.com/specifications/specifications.asp?l=en&m=291)
i dont think there are problems with the hardware, since with the live cd everything worked fine.

i liked the live cd, so i burned a install cd, and tried to install. everything works fine, (network auto configuration via dhcp works great, i choose to erease my whole disk and to automaticly create an ext3 and swap. partition table written.) until it gets to copy the standard pakets. the installer tells me that an "debootstrap error - couldn't retrieve dhcp3-client this may be due to a network problem or a bad cd, depending on your installation method...". thing is, i've never had any problems with this brand of cd-rs on any of my drives. so i cleaned the disk, rebooted and tried to install again. same problem. i took another cd-r and tried again. when installing from this disk i got the same problem when it comes to copy the libc6. until now i messed up 7 discs, tried 3 different brands, burned on 3 different recorders, getting errors on the pakets dhcp3, libc6, xfs and libsas, but always the same file on the same cd. i thought maybe the notebooks acpi or apm is faulty so i tried to install with acpi=off and apm=off, same problem.

has anybody had similar problems, or, can anybody tell me how to workaround that problem, maybe installing the files form a network share?


edit: total count of discs rendered useless: 9. now i got problems on coreutils and for a try i gave the warty release another debootstrap error on xfs

---

### Post by MadJeff on 2005-05-06
Same issue here, just jumped on to see if anyone else was having the same issue.

I'm installing on a Dell SX270, which is a small form-factor desktop. It's actually a glorified laptop, but a good solid box. All intel with integrated intel graphics, 2.4Ghz P4, etc. 

I can run the LiveCD fine and Ubuntu detects all the hardware perfectly. However, when I try to install the package copy is failing and some of the base os install never makes it over. I can actually get the install completed and booted up, but chunks of features are missing.

At first I thought I had a bad CD, but I've installed perfectly from this CD to other systems, so I burned several more discs with the same results. Not quite sure what's going on. I can get Mepis installed on the box without a hitch as well as running the LiveCD versions of Mepis and Ubuntu, so I don't think it's a hardware compatability problem.

Any ideas? I really want to start using Ubuntu here at work for one of my Linux security terminals.

---

### Post by j4k3 on 2005-05-06
phew. finally at least someone has the same issues. couldn't figure out whats wrong yet, but i was having heart attacks all day long at work thinking something really f00ed up my hardware.

---

### Post by MadJeff on 2005-05-06
As a sidenote, I just ran a memtest on the box and picked up memory errors, so it looks like it might be a bad stick of RAM. I'll swap it out and see if it makes any difference.

I decided to test the RAM after my test install of Mepis locked up twice in a matter of hours.  :wink:

---

### Post by j4k3 on 2005-05-06
i made it. finally.  \\:D/  tried yet another brand of cd-rs now and everything seems to work just fine now. still cant believe it, i swear i never had problems with yakumo cd-rs.

---

### Post by az on 2005-05-06
[QUOTE=MadJeff]As a sidenote, I just ran a memtest on the box and picked up memory errors, so it looks like it might be a bad stick of RAM. I'll swap it out and see if it makes any difference.

I decided to test the RAM after my test install of Mepis locked up twice in a matter of hours.  :wink:[/QUOTE]

There is a badram patch you can apply to the kernel and save (use) the good portion of ram on the stick.  It is a little work, but the concept is cool!

---

### Post by AgenT on 2005-05-07
[QUOTE=j4k3]i liked the live cd, so i burned a install cd, and tried to install. everything works fine, (network auto configuration via dhcp works great, i choose to erease my whole disk and to automaticly create an ext3 and swap. partition table written.) until it gets to copy the standard pakets. the installer tells me that an "debootstrap error - couldn't retrieve dhcp3-client this may be due to a network problem or a bad cd, depending on your installation method...".
...
has anybody had similar problems, or, can anybody tell me how to workaround that problem, maybe installing the files form a network share?
[/QUOTE]

I had the same problem. Not exactly sure on what item it gave this error, but it happened to me. How did I fix it? Easy, I burned another copy of the install CD. I know that you said you tried this, but I bet you did not try to burn it using a much slower speed. This fixed it for me. My burner is 52x, but once I forced it (I used k3b) to burn the CD at 32x, all worked out fine. 

I am now in Ubuntu for the first time cleaning up a few things, updating, and getting things back to how they were on my other Linux distro. 

Enjoy! \\:D/

---

### Post by j4k3 on 2005-05-08
[QUOTE=AgenT]I had the same problem. Not exactly sure on what item it gave this error, but it happened to me. How did I fix it? Easy, I burned another copy of the install CD. I know that you said you tried this, but I bet you did not try to burn it using a much slower speed. This fixed it for me. My burner is 52x, but once I forced it (I used k3b) to burn the CD at 32x, all worked out fine. 

I am now in Ubuntu for the first time cleaning up a few things, updating, and getting things back to how they were on my other Linux distro. 

Enjoy! \\:D/[/QUOTE]

Thanks for the reply AgenT, i already got it to work using another brand of cd-r. I've tried slower burning speed (2x(!)) before. With no luck, though.

---

### Post by Behel on 2005-05-20
Hello

I had also the same error. I was burning on a CDRW. I just erased it  and burned it at a lower speed (4x instead of 10x) and it works great...

---

### Post by orion27 on 2005-05-21
[QUOTE=j4k3]i am a liunx newbie and i've been trying to install ubuntu for 3 days and it wont work, 
so i thouhgt i'd ask you guys if anyone has ever had similar problems. 

my system is an Sony Vaio PCG FX205k, details here: [http://www.vaio-link.com/specifications/specifications.asp?l=en&m=291](http://www.vaio-link.com/specifications/specifications.asp?l=en&m=291)
i dont think there are problems with the hardware, since with the live cd everything worked fine.

i liked the live cd, so i burned a install cd, and tried to install. everything works fine, (network auto configuration via dhcp works great, i choose to erease my whole disk and to automaticly create an ext3 and swap. partition table written.) until it gets to copy the standard pakets. the installer tells me that an "debootstrap error - couldn't retrieve dhcp3-client this may be due to a network problem or a bad cd, depending on your installation method...". thing is, i've never had any problems with this brand of cd-rs on any of my drives. so i cleaned the disk, rebooted and tried to install again. same problem. i took another cd-r and tried again. when installing from this disk i got the same problem when it comes to copy the libc6. until now i messed up 7 discs, tried 3 different brands, burned on 3 different recorders, getting errors on the pakets dhcp3, libc6, xfs and libsas, but always the same file on the same cd. i thought maybe the notebooks acpi or apm is faulty so i tried to install with acpi=off and apm=off, same problem.

has anybody had similar problems, or, can anybody tell me how to workaround that problem, maybe installing the files form a network share?


edit: total count of discs rendered useless: 9. now i got problems on coreutils and for a try i gave the warty release another debootstrap error on xfs[/QUOTE]
 I just got this error an official pressed Ubuntu CD.  I have an AMD64 so I tried the AMD64 install CD first (yellow disc), got the error, then tried a X86 (red install disc) and got the error again.  I've had no problems with other OSes on the box (Windows XP 32bit, Gentoo, FC3, Suse 64bit).

---

