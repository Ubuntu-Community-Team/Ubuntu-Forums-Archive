---
title: "CD/DVD drive doesn't appear"
date: 2008-06-28
forum: Hardware
---

### Post by ronniegaucho on 2008-06-28
Hello,

Since several weeks, the CD drive doesn't appear in Places menu, nor in Computer window. And when I insert a CD-ROM, it doesn't lunch anything but I hear the CD-ROM turning!

Is the CD Drive not mounted? How can I mount it?

Sometimes (After a lot of rebootings), the CD drive appears but after another rebooting it disappears.

Thanks for your help.

---

### Post by Bakon Jarser on 2008-06-28
Does you see your cdrom in media?

```
cd /media
```

```
ls
```

If not does it show up in dev?

```
cd /dev
```

```
ls
```

---

### Post by ronniegaucho on 2008-06-28
Yes, I have it in /media:

```
wassim@sayerh:~$ cd /media
wassim@sayerh:/media$ ls
cdrom  cdrom0

```

But not in /dev:

```
wassim@sayerh:/dev$ ls
adsp       ptya7  ptycd  ptyp3  ptyr9  ptytf  ptyw5  ptyyb   rtc         tty3   tty7   ttyc3  ttye9  ttyqf  ttyt1  ttyv7  ttyxd           usbdev2.1_ep00
audio      ptya8  ptyce  ptyp4  ptyra  ptyu0  ptyw6  ptyyc   sda         tty30  tty8   ttyc4  ttyea  ttyr0  ttyt2  ttyv8  ttyxe           usbdev2.1_ep81
bus        ptya9  ptycf  ptyp5  ptyrb  ptyu1  ptyw7  ptyyd   sda1        tty31  tty9   ttyc5  ttyeb  ttyr1  ttyt3  ttyv9  ttyxf           usbdev2.3_ep00
console    ptyaa  ptyd0  ptyp6  ptyrc  ptyu2  ptyw8  ptyye   sda5        tty32  ttya0  ttyc6  ttyec  ttyr2  ttyt4  ttyva  ttyy0           usbdev2.3_ep02
core       ptyab  ptyd1  ptyp7  ptyrd  ptyu3  ptyw9  ptyyf   sequencer   tty33  ttya1  ttyc7  ttyed  ttyr3  ttyt5  ttyvb  ttyy1           usbdev2.3_ep03
disk       ptyac  ptyd2  ptyp8  ptyre  ptyu4  ptywa  ptyz0   sequencer2  tty34  ttya2  ttyc8  ttyee  ttyr4  ttyt6  ttyvc  ttyy2           usbdev2.3_ep04
dri        ptyad  ptyd3  ptyp9  ptyrf  ptyu5  ptywb  ptyz1   sg0         tty35  ttya3  ttyc9  ttyef  ttyr5  ttyt7  ttyvd  ttyy3           usbdev2.3_ep81
dsp        ptyae  ptyd4  ptypa  ptys0  ptyu6  ptywc  ptyz2   shm         tty36  ttya4  ttyca  ttyp0  ttyr6  ttyt8  ttyve  ttyy4           usbdev2.3_ep82
fd         ptyaf  ptyd5  ptypb  ptys1  ptyu7  ptywd  ptyz3   snapshot    tty37  ttya5  ttycb  ttyp1  ttyr7  ttyt9  ttyvf  ttyy5           usbdev2.3_ep83
full       ptyb0  ptyd6  ptypc  ptys2  ptyu8  ptywe  ptyz4   snd         tty38  ttya6  ttycc  ttyp2  ttyr8  ttyta  ttyw0  ttyy6           usbdev2.3_ep84
fuse       ptyb1  ptyd7  ptypd  ptys3  ptyu9  ptywf  ptyz5   sndstat     tty39  ttya7  ttycd  ttyp3  ttyr9  ttytb  ttyw1  ttyy7           usbdev3.1_ep00
hpet       ptyb2  ptyd8  ptype  ptys4  ptyua  ptyx0  ptyz6   stderr      tty4   ttya8  ttyce  ttyp4  ttyra  ttytc  ttyw2  ttyy8           usbdev3.1_ep81
initctl    ptyb3  ptyd9  ptypf  ptys5  ptyub  ptyx1  ptyz7   stdin       tty40  ttya9  ttycf  ttyp5  ttyrb  ttytd  ttyw3  ttyy9           usbdev4.1_ep00
input      ptyb4  ptyda  ptyq0  ptys6  ptyuc  ptyx2  ptyz8   stdout      tty41  ttyaa  ttyd0  ttyp6  ttyrc  ttyte  ttyw4  ttyya           usbdev4.1_ep81
kmem       ptyb5  ptydb  ptyq1  ptys7  ptyud  ptyx3  ptyz9   tty         tty42  ttyab  ttyd1  ttyp7  ttyrd  ttytf  ttyw5  ttyyb           usbdev5.1_ep00
kmsg       ptyb6  ptydc  ptyq2  ptys8  ptyue  ptyx4  ptyza   tty0        tty43  ttyac  ttyd2  ttyp8  ttyre  ttyu0  ttyw6  ttyyc           usbdev5.1_ep81
log        ptyb7  ptydd  ptyq3  ptys9  ptyuf  ptyx5  ptyzb   tty1        tty44  ttyad  ttyd3  ttyp9  ttyrf  ttyu1  ttyw7  ttyyd           vcs
loop0      ptyb8  ptyde  ptyq4  ptysa  ptyv0  ptyx6  ptyzc   tty10       tty45  ttyae  ttyd4  ttypa  ttys0  ttyu2  ttyw8  ttyye           vcs1
MAKEDEV    ptyb9  ptydf  ptyq5  ptysb  ptyv1  ptyx7  ptyzd   tty11       tty46  ttyaf  ttyd5  ttypb  ttyS0  ttyu3  ttyw9  ttyyf           vcs2
mem        ptyba  ptye0  ptyq6  ptysc  ptyv2  ptyx8  ptyze   tty12       tty47  ttyb0  ttyd6  ttypc  ttys1  ttyu4  ttywa  ttyz0           vcs3
mixer      ptybb  ptye1  ptyq7  ptysd  ptyv3  ptyx9  ptyzf   tty13       tty48  ttyb1  ttyd7  ttypd  ttyS1  ttyu5  ttywb  ttyz1           vcs4
net        ptybc  ptye2  ptyq8  ptyse  ptyv4  ptyxa  ram0    tty14       tty49  ttyb2  ttyd8  ttype  ttys2  ttyu6  ttywc  ttyz2           vcs5
null       ptybd  ptye3  ptyq9  ptysf  ptyv5  ptyxb  ram1    tty15       tty5   ttyb3  ttyd9  ttypf  ttyS2  ttyu7  ttywd  ttyz3           vcs6
nvidia0    ptybe  ptye4  ptyqa  ptyt0  ptyv6  ptyxc  ram10   tty16       tty50  ttyb4  ttyda  ttyq0  ttys3  ttyu8  ttywe  ttyz4           vcs7
nvidiactl  ptybf  ptye5  ptyqb  ptyt1  ptyv7  ptyxd  ram11   tty17       tty51  ttyb5  ttydb  ttyq1  ttyS3  ttyu9  ttywf  ttyz5           vcs8
oldmem     ptyc0  ptye6  ptyqc  ptyt2  ptyv8  ptyxe  ram12   tty18       tty52  ttyb6  ttydc  ttyq2  ttys4  ttyua  ttyx0  ttyz6           vcsa
port       ptyc1  ptye7  ptyqd  ptyt3  ptyv9  ptyxf  ram13   tty19       tty53  ttyb7  ttydd  ttyq3  ttys5  ttyub  ttyx1  ttyz7           vcsa1
ppp        ptyc2  ptye8  ptyqe  ptyt4  ptyva  ptyy0  ram14   tty2        tty54  ttyb8  ttyde  ttyq4  ttys6  ttyuc  ttyx2  ttyz8           vcsa2
psaux      ptyc3  ptye9  ptyqf  ptyt5  ptyvb  ptyy1  ram15   tty20       tty55  ttyb9  ttydf  ttyq5  ttys7  ttyud  ttyx3  ttyz9           vcsa3
ptmx       ptyc4  ptyea  ptyr0  ptyt6  ptyvc  ptyy2  ram2    tty21       tty56  ttyba  ttye0  ttyq6  ttys8  ttyue  ttyx4  ttyza           vcsa4
pts        ptyc5  ptyeb  ptyr1  ptyt7  ptyvd  ptyy3  ram3    tty22       tty57  ttybb  ttye1  ttyq7  ttys9  ttyuf  ttyx5  ttyzb           vcsa5
ptya0      ptyc6  ptyec  ptyr2  ptyt8  ptyve  ptyy4  ram4    tty23       tty58  ttybc  ttye2  ttyq8  ttysa  ttyv0  ttyx6  ttyzc           vcsa6
ptya1      ptyc7  ptyed  ptyr3  ptyt9  ptyvf  ptyy5  ram5    tty24       tty59  ttybd  ttye3  ttyq9  ttysb  ttyv1  ttyx7  ttyzd           vcsa7
ptya2      ptyc8  ptyee  ptyr4  ptyta  ptyw0  ptyy6  ram6    tty25       tty6   ttybe  ttye4  ttyqa  ttysc  ttyv2  ttyx8  ttyze           vcsa8
ptya3      ptyc9  ptyef  ptyr5  ptytb  ptyw1  ptyy7  ram7    tty26       tty60  ttybf  ttye5  ttyqb  ttysd  ttyv3  ttyx9  ttyzf           watchdog
ptya4      ptyca  ptyp0  ptyr6  ptytc  ptyw2  ptyy8  ram8    tty27       tty61  ttyc0  ttye6  ttyqc  ttyse  ttyv4  ttyxa  urandom         xconsole
ptya5      ptycb  ptyp1  ptyr7  ptytd  ptyw3  ptyy9  ram9    tty28       tty62  ttyc1  ttye7  ttyqd  ttysf  ttyv5  ttyxb  usbdev1.1_ep00  zero
ptya6      ptycc  ptyp2  ptyr8  ptyte  ptyw4  ptyya  random  tty29       tty63  ttyc2  ttye8  ttyqe  ttyt0  ttyv6  ttyxc  usbdev1.1_ep81

```

Thanks ;)

---

### Post by Bakon Jarser on 2008-06-28
I guess the first step is to make sure your cdrom isn't broken.  Can you boot from the live cd?

---

### Post by ronniegaucho on 2008-06-28
I've just tried, it doesn't :S

---

### Post by Bakon Jarser on 2008-06-28
Uh oh:(.  Your cdrom may be broken.  Do you have another OS, like Windows, installed that you can test it on?  At least cd drives are fairly cheap these days.

---

### Post by ronniegaucho on 2008-06-28
Non, I don't. Can I install it on Virtualbox to test the CD drive?

---

### Post by Bakon Jarser on 2008-06-28
I don't think that would help, as I think virtualbox just passes commands onto linux and linux already can't see your drive.  Only other suggestion I have is to test it on a friends machine.  I think I've helped as much as I can.  Good luck.

---

