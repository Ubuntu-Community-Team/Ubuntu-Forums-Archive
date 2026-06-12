---
title: "CD busted or not? help"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by SebbeJohan on 2007-05-08
Hi,

noob here,
I've had this prob****lem since I moved from ubuntu to kubuntu 6 months ago and I assumed my cd was just busted, but now I'm not sure...(i never was)
I have a CD/dvd combo on my laptop and the dvd works perfectly. The Cd however does not. It just spins and nothing is recognized on my desktop.
The weired thing is that I went to System settings>Advanced>Disk and file systems, and my cd/dvd is disabled. I tried to enable but got this error message: 
```
An error occurred while enabling /media/cdrom0. The system reported: mount: No medium found
details:
Return code from mount was 32. "mount failure"
```

When I insert a cd this the dmesg I receive:
```
[23540.100000] UDF-fs: Partition marked readonly; forcing readonly mount
[23540.156000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '9035619', timestamp 2001/09/11 23:08 (1078)

```

my fstab gives:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=44a76d98-e9ce-4cd1-8f6d-89b29c51b24d / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,d$
# /dev/sda5
UUID=dcf7663e-79f9-4fb3-9276-c7651344ed2d none swap sw 0 0
/dev/scd0 /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0

```

So, is my CD busted or not? :confused:  How can I fix it? I'd be so happy, Any help is much appreciated!

Thx

---

### Post by teaker1s on 2007-05-08
way I'd check is download a live boot linux such as knoppix-try booting it from that drive:KS

---

### Post by SebbeJohan on 2007-05-08
Thanks for your reply!
I'd like to try your solution but I won't be able to burn it on a cd since my dvd/cd drive won't recognize any cd I'd put in... ](*,) 
any other idea?

---

### Post by SebbeJohan on 2007-05-09
Please anyone? :cry:

---

### Post by teaker1s on 2007-05-09
an old windows install cd-just see if it will boot-don't install.
or the ubuntu cd you installed with?

---

### Post by SebbeJohan on 2007-05-10
Thanks teaker1s for the help!
Well the thing is that I used the kubuntu live dvd to install when upgrading to feisty, hoping that a clean install would fix it, but no... I mean reading dvds and burning them works perfectly but nothing happens with cds... I have inserted all kind of cds possible: data, music... but nothing happens, it just spins and makes weired noises.
as for window cd... I don't have it anymore... I am so pleased with Ubuntu/kubuntu... well, except for this CD problem...
Is there any way to check with the terminal if something's wrong?

---

### Post by teaker1s on 2007-05-10
I'm affraid I don't know, it may be worth checking with drive manufacturer if there is a bios update for your drive, failing that it soundsa like drive failure

---

### Post by SebbeJohan on 2007-05-12
Allright, I'll try to do that then. Gonna try to take it out from my laptop as well just to clean it.
Thanks for the help! :)

---

### Post by psusi on 2007-05-12
It sounds like the cd laser burned out.  I had that happen to me a few months back.  What kind of drive is this?

---

### Post by SebbeJohan on 2007-05-14
Hi and thanks psusi,

I hope it's not the case... well, the drive is a Slimtype CD/DVDRW SOSW-852S.
Sorry it may sound stupid :oops:  but is the lens the same for the cd and the dvd?

---

### Post by SebbeJohan on 2007-05-14
I tried to remove the drive manually... but with no luck... I remove all the screws  and pulled it out but it just didn't want to come out.
And NOW the dvd is failing me also... doesn't read anything anymore](*,)

---

