---
title: "Is Ubuntu bad for my hard drive?"
date: 2016-02-05
forum: Hardware
---

### Post by helm10101 on 2016-02-05
I installed Ubuntu a few days ago, alongside Windows 10 (dual boot on the same hard drive) and I noticed, that whenever I am using Ubuntu, I can clearly hear the hard drive head moving virtually all the time.
When I switch back to Windows, it's quiet.
Do you have this problem as well? It feels like I'm using those old PC's from the early 2000's

---

### Post by davidvandoren on 2016-02-05
You probably don't have enough ram for the Ubuntu version you installed. 

If you use more ram than your pc actually has Linux/Ubuntu will use a swap partition on you hard-drive like ram.
That will cause a lot of rambling and slow performance. 

Install lubuntu or a lighter desktop environment on the current. 

Open the terminal and 

```
[COLOR=#111111][FONT=Consolas]sudo apt-get install lubuntu-desktop  [/FONT][/COLOR]


```

---

### Post by TheFu on 2016-02-05
Could be anything based on that description. Need more data to help at all.
[http://blog.jdpfu.com/sysinfo](http://blog.jdpfu.com/sysinfo)

---

### Post by helm10101 on 2016-02-05
Thanks, it could really be my low ram.
By the way, Lubuntu is a desktop? I was sure it's a complete Linux distribution?
And before I try lubuntu, how do I uninstall it if I'd like to later?

---

### Post by yancek on 2016-02-05
Lubuntu is a derivative of Ubuntu with the LXDE Desktop environment so that' the primary difference.  You can try it from a Live DVD to test it (or a flash drive) and if you install it, since it is an opereating system and not an application, you don't uninstall it.  You simply format the partition(s) on which you had it when you install something else to the same partitions.

---

### Post by helm10101 on 2016-02-05
> **yancek said:**
> Lubuntu is a derivative of Ubuntu with the LXDE Desktop environment so that' the primary difference.  You can try it from a Live DVD to test it (or a flash drive) and if you install it, since it is an opereating system and not an application, you don't uninstall it.  You simply format the partition(s) on which you had it when you install something else to the same partitions.
So  [COLOR=#111111][FONT=Consolas]sudo apt-get install lubuntu-desktop  [/FONT][/COLOR]will actually install Lubuntu instead of Ubuntu? At first it didn't make sense to me that you can install a complete OS over your existing OS through that OS itself :D

---

### Post by TheFu on 2016-02-05
Linux systems are build based on adding different packages.  lubuntu-desktop is a "meta-package" that will add a lighter desktop and the associated programs that the desktop designers decided you'd probably want.  If you have Ubuntu-desktop (Unity) and add lubuntu-desktop, then you'll be able to run either by making a selection at the login screen (click on the "gear" to change).  The only thing this wastes is disk storage.

OTOH, if you looked at that link I posted above and provide the data is provides to us here, then we could provide better advice. Your choice, of course.

---

### Post by helm10101 on 2016-02-05
Thank you TheFu.
So installing lubuntu-desktop alone, and then using it would be the same as doing a clean install of lubuntu? (if I did not have Ubuntu before)
the link you posted is showing PC Specs? If so:
intel i5-4200m, 1TB hard disk drive, 4GB ram

---

### Post by TheFu on 2016-02-05
a) the link provides a script to be run, but the last line above is fine, if accurate.  Would be nice if the script were run, since it seems we need more, specific, detailed, information, to help solve the root issue.
b) That machine should be fine with stock ubuntu. There is something else wrong.
c) No, installing lubuntu-desktop will NOT be the same as doing a clean in stall of lubuntu. It will add the lubuntu-desktop packages to an existing Ubuntu install. If you want a clean lubuntu install, download the ISO and install it wiping any prior Ubuntu/Linux installs you don't want retained. I wouldn't do that unless the are really bad problems with the current installation beyond what you've tried to convey here.

Please run the script and post the sprunge link it creates so we can figure out the root cause of the performance issues seen. Something isn't good and perhaps Windows is simply ignoring the issue?

---

### Post by helm10101 on 2016-02-06
Sorry I'm being too careful here. but ever since I moved to Ubuntu I realized how vulnerable we are in the PC world :D.
And I just wanted to know if this script is a safe thing to run?

---

### Post by sudodus on 2016-02-06
I looked at the script, and it is safe to run :-)

*TheFu* has been helping many people during many years here at the Ubuntu Forums. I don't think he would recommend a bad script.

---

### Post by TheFu on 2016-02-06
a) I wrote the script. I believe it is safe, but I didn't follow "scripting best practices" for the sake of readability and reduced complexity.
b) It is written to be fairly simple for someone with average Linux skillz to look over quickly and understand what it does. Every command is pretty normal and has a manpage where what each does and what each option means can be checked.
c) [http://sprunge.us/INTR](http://sprunge.us/INTR) is a run from my primary desktop, which has fewer resources allocated than yours.

Thanks sudodus for the vote of confidence. We tend to ask for the same info all the time here, so I figured it was time for a quick script - sorta like the boot-info script that concentrates on boot issues. That was my thought anyway. The only thing that might be missing which would be useful for storage questions is 'blkid'. I need to add that. ;)

---

