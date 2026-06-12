---
title: "[SOLVED] computer halts on reboot/restart"
date: 2008-09-30
forum: Hardware
---

### Post by flala on 2008-09-30
Hi,

I have Dell laptop with Ubuntu and Windows Xp dual-booted on it. Ubuntu "shut down" and "restart" worked just fine when I newly installed in (3 days ago.) Then when I would "restart" either through the GUI or terminal, my computer would go blank and nothing would happen. I have to then force shut down and when I turn on my computer again, ubuntu would load with different errors each time. Once I got something on the lines of: 

-->The GNOME session manager was unable to lock file/.../ICEauthority.

I got this error several times and then I loaded XP and tried to load Ubuntu again. Then I got this error:

-->fsck failed. Please repair manually.

Now, my reboot still doesn't work, but everytime I hit reboot and my system hangs, if I boot XP right after and then ubuntu, I can log in with no problems. On the other hand, if my restart hangs (then I manually turn my comp off) and I boot ubuntu right after, I can never log into ubuntu due to different errors.

The only thing that I changed between the time my restart was working and the time it stopped was my GRUB menu.lst. I put windows XP first in the priority list and deleted:
--> title        other operating systems:
root

That's the only change I made. My GRUB worked fine, yet I undid those changes to see if GRUB was an issue. After I corrected the issue and hit "shut down", my shut down crashed in the same manner! This time though, ubuntu booted just fine w/o having me to boot XP first. Now, my "restart" works but "shut down" does not! 

Normal GRUB - shut down does not work
modified GRUB - restart does not work

Any ideas what's going on and what I can do to fix this? I'm really baffled and I'd really appreciate help on this. Thank you!

-Fauzia

---

### Post by pytheas22 on 2008-09-30
It sounds perhaps like your file system is corrupted.  You could check by booting to the Ubuntu live CD, opening a terminal, and running fsck with a command like:
```

sudo fsck /dev/sdb0
```

In the command above, I assume that your Ubuntu partition is the only partition on your secondary hard drive.  It could be something else; you may need to guess.  If you can't figure it out, post the output here of the command:
```

ls /dev
```

If your file system has errors, fsck should be able to repair them (but you will risk losing your data, so if you have anything important on your Ubuntu system, back it up first).

You could also simply reinstall Ubuntu, which may be the easiest solution if you don't have too much time or data invested in your current installation.

Please let us know if this helps.

---

### Post by flala on 2008-09-30
Thank you for your prompt reply. I could not install ubuntu from live CD so I did so using Alternate CD. Anyway I can do this using alternate CD? 

Here are the results of the commands:

```
fauzia@Fauzia:~$ sudo fsck /dev/sdb0

[sudo] password for fauzia: 

fsck 1.40.8 (13-Mar-2008)

e2fsck 1.40.8 (13-Mar-2008)

fsck.ext2: No such file or directory while trying to open /dev/sdb0



The superblock could not be read or does not describe a correct ext2

filesystem.  If the device is valid and it really contains an ext2

filesystem (and not swap or ufs or something else), then the superblock

is corrupt, and you might try running e2fsck with an alternate superblock:

    e2fsck -b 8193 <device>

fauzia@Fauzia:~$ 
fauzia@Fauzia:~$ ls /dev 
adsp       ptyc3  ptyr0  ptyvd  ram4        tty54  ttydf  ttys8  ttyx5 
agpgart    ptyc4  ptyr1  ptyve  ram5        tty55  ttye0  ttys9  ttyx6 
audio      ptyc5  ptyr2  ptyvf  ram6        tty56  ttye1  ttysa  ttyx7 
bus        ptyc6  ptyr3  ptyw0  ram7        tty57  ttye2  ttysb  ttyx8 
cdrom      ptyc7  ptyr4  ptyw1  ram8        tty58  ttye3  ttysc  ttyx9 
cdrw       ptyc8  ptyr5  ptyw2  ram9        tty59  ttye4  ttysd  ttyxa 
console    ptyc9  ptyr6  ptyw3  random      tty6   ttye5  ttyse  ttyxb 
core       ptyca  ptyr7  ptyw4  rtc         tty60  ttye6  ttysf  ttyxc 
disk       ptycb  ptyr8  ptyw5  scd0        tty61  ttye7  ttyt0  ttyxd 
dri        ptycc  ptyr9  ptyw6  sda         tty62  ttye8  ttyt1  ttyxe 
dsp        ptycd  ptyra  ptyw7  sda1        tty63  ttye9  ttyt2  ttyxf 
dvd        ptyce  ptyrb  ptyw8  sda2        tty7   ttyea  ttyt3  ttyy0 
fd         ptycf  ptyrc  ptyw9  sda5        tty8   ttyeb  ttyt4  ttyy1 
full       ptyd0  ptyrd  ptywa  sda6        tty9   ttyec  ttyt5  ttyy2 
fuse       ptyd1  ptyre  ptywb  sequencer   ttya0  ttyed  ttyt6  ttyy3 
hpet       ptyd2  ptyrf  ptywc  sequencer2  ttya1  ttyee  ttyt7  ttyy4 
initctl    ptyd3  ptys0  ptywd  sg0         ttya2  ttyef  ttyt8  ttyy5 
input      ptyd4  ptys1  ptywe  sg1         ttya3  ttyp0  ttyt9  ttyy6 
kmem       ptyd5  ptys2  ptywf  shm         ttya4  ttyp1  ttyta  ttyy7 
kmsg       ptyd6  ptys3  ptyx0  snapshot    ttya5  ttyp2  ttytb  ttyy8 
log        ptyd7  ptys4  ptyx1  snd         ttya6  ttyp3  ttytc  ttyy9 
loop0      ptyd8  ptys5  ptyx2  sndstat     ttya7  ttyp4  ttytd  ttyya 
loop1      ptyd9  ptys6  ptyx3  sr0         ttya8  ttyp5  ttyte  ttyyb 
loop2      ptyda  ptys7  ptyx4  stderr      ttya9  ttyp6  ttytf  ttyyc 
loop3      ptydb  ptys8  ptyx5  stdin       ttyaa  ttyp7  ttyu0  ttyyd 
loop4      ptydc  ptys9  ptyx6  stdout      ttyab  ttyp8  ttyu1  ttyye 
loop5      ptydd  ptysa  ptyx7  tty         ttyac  ttyp9  ttyu2  ttyyf 
loop6      ptyde  ptysb  ptyx8  tty0        ttyad  ttypa  ttyu3  ttyz0 
loop7      ptydf  ptysc  ptyx9  tty1        ttyae  ttypb  ttyu4  ttyz1 
MAKEDEV    ptye0  ptysd  ptyxa  tty10       ttyaf  ttypc  ttyu5  ttyz2 
mem        ptye1  ptyse  ptyxb  tty11       ttyb0  ttypd  ttyu6  ttyz3 
mixer      ptye2  ptysf  ptyxc  tty12       ttyb1  ttype  ttyu7  ttyz4 
net        ptye3  ptyt0  ptyxd  tty13       ttyb2  ttypf  ttyu8  ttyz5 
null       ptye4  ptyt1  ptyxe  tty14       ttyb3  ttyq0  ttyu9  ttyz6 
nvidia0    ptye5  ptyt2  ptyxf  tty15       ttyb4  ttyq1  ttyua  ttyz7 
nvidiactl  ptye6  ptyt3  ptyy0  tty16       ttyb5  ttyq2  ttyub  ttyz8 
oldmem     ptye7  ptyt4  ptyy1  tty17       ttyb6  ttyq3  ttyuc  ttyz9 
port       ptye8  ptyt5  ptyy2  tty18       ttyb7  ttyq4  ttyud  ttyza 
ppp        ptye9  ptyt6  ptyy3  tty19       ttyb8  ttyq5  ttyue  ttyzb 
psaux      ptyea  ptyt7  ptyy4  tty2        ttyb9  ttyq6  ttyuf  ttyzc 
ptmx       ptyeb  ptyt8  ptyy5  tty20       ttyba  ttyq7  ttyv0  ttyzd 
pts        ptyec  ptyt9  ptyy6  tty21       ttybb  ttyq8  ttyv1  ttyze 
ptya0      ptyed  ptyta  ptyy7  tty22       ttybc  ttyq9  ttyv2  ttyzf 
ptya1      ptyee  ptytb  ptyy8  tty23       ttybd  ttyqa  ttyv3  urandom 
ptya2      ptyef  ptytc  ptyy9  tty24       ttybe  ttyqb  ttyv4  usbdev1.1_ep00 
ptya3      ptyp0  ptytd  ptyya  tty25       ttybf  ttyqc  ttyv5  usbdev1.1_ep81 
ptya4      ptyp1  ptyte  ptyyb  tty26       ttyc0  ttyqd  ttyv6  usbdev2.1_ep00 
ptya5      ptyp2  ptytf  ptyyc  tty27       ttyc1  ttyqe  ttyv7  usbdev2.1_ep81 
ptya6      ptyp3  ptyu0  ptyyd  tty28       ttyc2  ttyqf  ttyv8  usbdev3.1_ep00 
ptya7      ptyp4  ptyu1  ptyye  tty29       ttyc3  ttyr0  ttyv9  usbdev3.1_ep81 
ptya8      ptyp5  ptyu2  ptyyf  tty3        ttyc4  ttyr1  ttyva  usbdev4.1_ep00 
ptya9      ptyp6  ptyu3  ptyz0  tty30       ttyc5  ttyr2  ttyvb  usbdev4.1_ep81 
ptyaa      ptyp7  ptyu4  ptyz1  tty31       ttyc6  ttyr3  ttyvc  vcs 
ptyab      ptyp8  ptyu5  ptyz2  tty32       ttyc7  ttyr4  ttyvd  vcs1 
ptyac      ptyp9  ptyu6  ptyz3  tty33       ttyc8  ttyr5  ttyve  vcs2 
ptyad      ptypa  ptyu7  ptyz4  tty34       ttyc9  ttyr6  ttyvf  vcs3 
ptyae      ptypb  ptyu8  ptyz5  tty35       ttyca  ttyr7  ttyw0  vcs4 
ptyaf      ptypc  ptyu9  ptyz6  tty36       ttycb  ttyr8  ttyw1  vcs5 
ptyb0      ptypd  ptyua  ptyz7  tty37       ttycc  ttyr9  ttyw2  vcs6 
ptyb1      ptype  ptyub  ptyz8  tty38       ttycd  ttyra  ttyw3  vcs7 
ptyb2      ptypf  ptyuc  ptyz9  tty39       ttyce  ttyrb  ttyw4  vcs8 
ptyb3      ptyq0  ptyud  ptyza  tty4        ttycf  ttyrc  ttyw5  vcsa 
ptyb4      ptyq1  ptyue  ptyzb  tty40       ttyd0  ttyrd  ttyw6  vcsa1 
ptyb5      ptyq2  ptyuf  ptyzc  tty41       ttyd1  ttyre  ttyw7  vcsa2 
ptyb6      ptyq3  ptyv0  ptyzd  tty42       ttyd2  ttyrf  ttyw8  vcsa3 
ptyb7      ptyq4  ptyv1  ptyze  tty43       ttyd3  ttys0  ttyw9  vcsa4 
ptyb8      ptyq5  ptyv2  ptyzf  tty44       ttyd4  ttyS0  ttywa  vcsa5 
ptyb9      ptyq6  ptyv3  ram0   tty45       ttyd5  ttys1  ttywb  vcsa6 
ptyba      ptyq7  ptyv4  ram1   tty46       ttyd6  ttyS1  ttywc  vcsa7 
ptybb      ptyq8  ptyv5  ram10  tty47       ttyd7  ttys2  ttywd  vcsa8 
ptybc      ptyq9  ptyv6  ram11  tty48       ttyd8  ttyS2  ttywe  watchdog 
ptybd      ptyqa  ptyv7  ram12  tty49       ttyd9  ttys3  ttywf  xconsole 
ptybe      ptyqb  ptyv8  ram13  tty5        ttyda  ttyS3  ttyx0  zero 
ptybf      ptyqc  ptyv9  ram14  tty50       ttydb  ttys4  ttyx1 
ptyc0      ptyqd  ptyva  ram15  tty51       ttydc  ttys5  ttyx2 
ptyc1      ptyqe  ptyvb  ram2   tty52       ttydd  ttys6  ttyx3 
ptyc2      ptyqf  ptyvc  ram3   tty53       ttyde  ttys7  ttyx4 
fauzia@Fauzia:~$  
```

Let me know if this helps you figure something out. Else, I'll either reinstall ubuntu or manage with the error.

Thanks,
Fauzia

---

### Post by cariboo on 2008-09-30
I'm assuming that you only have one hard drive in your laptop so the command would be:

```
sudo fsck /dev/sda
```

The previous poster only used /dev/sdb0 as an example. The reason he suggested using the livecd, is that if you run fsck while your hard drive is mounted it could cause a lot of damage to your data.

You said you can't install from the Livecd, you don't need to install anything, you just have to be able to boot to the desktop and then in a terminal run the above command.

If you can't get the livecd to boot to the desk top try some of the options you get when you press F4 at the menu screen.

Jim

---

### Post by pytheas22 on 2008-10-01
The instructions in the post above are good; please give them a try, using 'sda' in the command in place of 'sdb0'  I did misidentify your hard drive--I guess I was thinking of another thread, as I thought for some reason that you had Ubuntu installed on a second hard disk.

Also, as the poster above says, you don't need to be able to boot to the desktop to run fsck; you just need a command line somewhere.  I'm not sure if the alternate CD has fsck installed, but if it does, it would probably work to boot to a command prompt on the the alternate CD and run 'fsck' there.  You could also use pretty much any Linux live CD for this purpose.  Even if you can't boot to a graphical desktop, press control-alt-F2 and you should be brought to a textual command prompt where you can log in and run 'fsck'; this should work on almost any version of Linux, even something minimalist like [thumb-drive DSL]("http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl/").

---

### Post by flala on 2008-10-01
I'm a little confused. 

Jim's method:
Am I supposed to boot to the desktop from the CD? How do I do that? I couldn't go the the menu and run any options from F4. The alternate CD did not have any and the Live CD does not work for me (It hangs when I hit any button right on the menu.) 

Pytheas method:
Do I boot to command prompt/graphical desktop from the CD? How do I do that? When should I hit ctrl-alt-f2?

This is what I tried. I booted to Ubuntu normally and inserted the CD (tried both live and alternate.) I opened the terminal and typed:

```
sudo fsck /dev/sda
```

I got this:

```
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sda
File system mounted or opened exclusively by another program?
```

I also tried running the fsck command by pressing ctrl-alt-f2 after booting into ubuntu normally. I got the same message. I think it's time to let this go. I can manage with a little inconvenience sometimes on restarting/shutting down. More than this, I really need to figure out my wireless problem. Thank you so much for all your help though.

---

### Post by pytheas22 on 2008-10-01
You would need to be booted to a CD of some sort to run fsck, because it can't work if your hard drive is mounted, which it would be if you're booted to Ubuntu on your hard drive.

But if this isn't a serious problem (I thought it was happening all the time, but I guess not?), maybe you should just let it go.  'fsck' has the potential to cause more problems that it solves (usually it does fix things, but when you're dealing with file-system corruption, the results can be unpredictable).

What is your wireless problem?  If you provide a link to that thread, I'll take a look (I generally know more about wireless than fsck things anyway).

EDIT: just saw that I'm also already in your wireless thread...I guess I didn't realize that you were the same person :)

---

### Post by flala on 2008-10-01
LOL! You *just* realized? Haha, anyway. I actually FIXED THE PROBLEM! :-O I think booting Ubuntu Recovery mode (from GRUB menu) and "repairing broken files" fixes the problem. This may really just be a coincidence though or probably just that it got fixed on its own and Recovery mode had nothing to do with it. I tried about 5 shut down and restarts in a span of the day today and it seems to work. It's hard to say but now both my shut down and restart do not hang. So strange. I hope this behavior is not temporary. I will post back in 15 days or so to confirm, just so that people know. Can't believe it worked right after I gave up O_O. Thank you for helping though. Back to the wireless problem :)

---

### Post by Sef on 2008-10-02
> -->The GNOME session manager was unable to lock file/.../ICEauthority.Often if sudo is used instead of gksudo that can happen.   Sudo is when the Terminal is used; gksudo is when a graphical application is used.

Glad you got it fixed.

---

### Post by flala on 2008-10-07
Just to update: my computer still hangs sometimes while restarting but it restarts normally (with some drive checks.)

@Sef: Using gksudo for doing what?

-Fauzia

---

