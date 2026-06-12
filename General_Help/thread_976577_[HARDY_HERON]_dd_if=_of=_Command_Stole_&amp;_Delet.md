---
title: "[HARDY HERON] dd if= of= Command Stole &amp; Deleted .ISO File?!"
date: 2008-11-09
forum: General Help
---

### Post by n0tmycupoftea on 2008-11-09
Hey guys,

I'm new to linux and have been delving deeply into reading the forums to expand my knowledge and usability of linux and getting use to a lot of the commands and playing around with them to get acquainted with them.

Recently I got into backing up my DVDs seeing as how I had read and comprehended a lot of the troubleshoots and solutions I had read from this board, so I go ahead and start.

No problems there, but now I wanted to play around with playing the DVD.iso file from my hard drive as a device, should be no problem right? Well I go ahead and begin backing up the dvd in the terminal and pops out my .iso file on my desktop. I then run the command(s):

dd if=/dev/dvd of=filename.iso

it begins to do its thing and then I notice my desktop DVD.iso reads 0 bytes and forgive me I forgot to capture the stuff dd had spit out after it had done its thing. It did give me an error of some sort starting with iotc I believe? So now my hard drive has lost its weight of 4GB and I have a blank DVD.iso file on the desktop and no clue what the dd command did.

Now I think it might have just moved it or copied it into the /dev/dvd folder since this is my first time using dd. Well I move on other to my /dev folder and then try to get into /dev/dvd but it says no such file or directory. So now at this point I'm confused and try to pull up the list. Heres what it gives me:

```
n0tmycupoftea@n0tmycupoftea-laptop:~$ cd ..
n0tmycupoftea@n0tmycupoftea-laptop:/home$ cd ..
n0tmycupoftea@n0tmycupoftea-laptop:/$ ls
bin    debian-binary  home            lib         mnt   root  sys  var
boot   dev            initrd          lost+found  opt   sbin  tmp  vmlinuz.old
cdrom  etc            initrd.img.old  media       proc  srv   usr
n0tmycupoftea@n0tmycupoftea-laptop:/$ cd dev
n0tmycupoftea@n0tmycupoftea-laptop:/dev$ cd dvd
bash: cd: dvd: No such file or directory
n0tmycupoftea@n0tmycupoftea-laptop:/dev$ ls
adsp       ptycc  ptys5  ptyxe       tty26  ttycc  ttyS2    ttyx8
audio      ptycd  ptys6  ptyxf       tty27  ttycd  ttys3    ttyx9
audio1     ptyce  ptys7  ptyy0       tty28  ttyce  ttyS3    ttyxa
bus        ptycf  ptys8  ptyy1       tty29  ttycf  ttys4    ttyxb
cdrom      ptyd0  ptys9  ptyy2       tty3   ttyd0  ttys5    ttyxc
cdrw       ptyd1  ptysa  ptyy3       tty30  ttyd1  ttys6    ttyxd
console    ptyd2  ptysb  ptyy4       tty31  ttyd2  ttys7    ttyxe
core       ptyd3  ptysc  ptyy5       tty32  ttyd3  ttys8    ttyxf
disk       ptyd4  ptysd  ptyy6       tty33  ttyd4  ttys9    ttyy0
dsp        ptyd5  ptyse  ptyy7       tty34  ttyd5  ttysa    ttyy1
dsp1       ptyd6  ptysf  ptyy8       tty35  ttyd6  ttysb    ttyy2
dvd        ptyd7  ptyt0  ptyy9       tty36  ttyd7  ttysc    ttyy3
dvd.bk     ptyd8  ptyt1  ptyya       tty37  ttyd8  ttysd    ttyy4
dvdrw      ptyd9  ptyt2  ptyyb       tty38  ttyd9  ttyse    ttyy5
fd         ptyda  ptyt3  ptyyc       tty39  ttyda  ttysf    ttyy6
full       ptydb  ptyt4  ptyyd       tty4   ttydb  ttyt0    ttyy7
fuse       ptydc  ptyt5  ptyye       tty40  ttydc  ttyt1    ttyy8
hpet       ptydd  ptyt6  ptyyf       tty41  ttydd  ttyt2    ttyy9
initctl    ptyde  ptyt7  ptyz0       tty42  ttyde  ttyt3    ttyya
input      ptydf  ptyt8  ptyz1       tty43  ttydf  ttyt4    ttyyb
kmem       ptye0  ptyt9  ptyz2       tty44  ttye0  ttyt5    ttyyc
kmsg       ptye1  ptyta  ptyz3       tty45  ttye1  ttyt6    ttyyd
log        ptye2  ptytb  ptyz4       tty46  ttye2  ttyt7    ttyye
loop0      ptye3  ptytc  ptyz5       tty47  ttye3  ttyt8    ttyyf
loop1      ptye4  ptytd  ptyz6       tty48  ttye4  ttyt9    ttyz0
loop2      ptye5  ptyte  ptyz7       tty49  ttye5  ttyta    ttyz1
loop3      ptye6  ptytf  ptyz8       tty5   ttye6  ttytb    ttyz2
loop4      ptye7  ptyu0  ptyz9       tty50  ttye7  ttytc    ttyz3
loop5      ptye8  ptyu1  ptyza       tty51  ttye8  ttytd    ttyz4
loop6      ptye9  ptyu2  ptyzb       tty52  ttye9  ttyte    ttyz5
loop7      ptyea  ptyu3  ptyzc       tty53  ttyea  ttytf    ttyz6
MAKEDEV    ptyeb  ptyu4  ptyzd       tty54  ttyeb  ttyu0    ttyz7
mem        ptyec  ptyu5  ptyze       tty55  ttyec  ttyu1    ttyz8
mixer      ptyed  ptyu6  ptyzf       tty56  ttyed  ttyu2    ttyz9
mixer1     ptyee  ptyu7  ram0        tty57  ttyee  ttyu3    ttyza
net        ptyef  ptyu8  ram1        tty58  ttyef  ttyu4    ttyzb
null       ptyp0  ptyu9  ram10       tty59  ttyp0  ttyu5    ttyzc
nvidia0    ptyp1  ptyua  ram11       tty6   ttyp1  ttyu6    ttyzd
nvidiactl  ptyp2  ptyub  ram12       tty60  ttyp2  ttyu7    ttyze
oldmem     ptyp3  ptyuc  ram13       tty61  ttyp3  ttyu8    ttyzf
port       ptyp4  ptyud  ram14       tty62  ttyp4  ttyu9    urandom
ppp        ptyp5  ptyue  ram15       tty63  ttyp5  ttyua    usbdev1.1_ep00
psaux      ptyp6  ptyuf  ram2        tty7   ttyp6  ttyub    usbdev1.1_ep81
ptmx       ptyp7  ptyv0  ram3        tty8   ttyp7  ttyuc    usbdev2.1_ep00
pts        ptyp8  ptyv1  ram4        tty9   ttyp8  ttyud    usbdev2.1_ep81
ptya0      ptyp9  ptyv2  ram5        ttya0  ttyp9  ttyue    usbdev2.3_ep00
ptya1      ptypa  ptyv3  ram6        ttya1  ttypa  ttyuf    usbdev2.3_ep02
ptya2      ptypb  ptyv4  ram7        ttya2  ttypb  ttyUSB0  usbdev2.3_ep03
ptya3      ptypc  ptyv5  ram8        ttya3  ttypc  ttyUSB1  usbdev2.3_ep04
ptya4      ptypd  ptyv6  ram9        ttya4  ttypd  ttyv0    usbdev2.3_ep81
ptya5      ptype  ptyv7  random      ttya5  ttype  ttyv1    usbdev2.3_ep82
ptya6      ptypf  ptyv8  rtc         ttya6  ttypf  ttyv2    usbdev2.3_ep83
ptya7      ptyq0  ptyv9  scd0        ttya7  ttyq0  ttyv3    usbdev2.3_ep84
ptya8      ptyq1  ptyva  sda         ttya8  ttyq1  ttyv4    usbdev3.1_ep00
ptya9      ptyq2  ptyvb  sda1        ttya9  ttyq2  ttyv5    usbdev3.1_ep81
ptyaa      ptyq3  ptyvc  sda2        ttyaa  ttyq3  ttyv6    usbdev3.2_ep00
ptyab      ptyq4  ptyvd  sda5        ttyab  ttyq4  ttyv7    usbdev3.2_ep02
ptyac      ptyq5  ptyve  sequencer   ttyac  ttyq5  ttyv8    usbdev3.2_ep04
ptyad      ptyq6  ptyvf  sequencer2  ttyad  ttyq6  ttyv9    usbdev3.2_ep81
ptyae      ptyq7  ptyw0  sg0         ttyae  ttyq7  ttyva    usbdev3.2_ep82
ptyaf      ptyq8  ptyw1  sg1         ttyaf  ttyq8  ttyvb    usbdev3.2_ep84
ptyb0      ptyq9  ptyw2  shm         ttyb0  ttyq9  ttyvc    usbdev4.1_ep00
ptyb1      ptyqa  ptyw3  snapshot    ttyb1  ttyqa  ttyvd    usbdev4.1_ep81
ptyb2      ptyqb  ptyw4  snd         ttyb2  ttyqb  ttyve    usbdev5.1_ep00
ptyb3      ptyqc  ptyw5  sndstat     ttyb3  ttyqc  ttyvf    usbdev5.1_ep81
ptyb4      ptyqd  ptyw6  sr0         ttyb4  ttyqd  ttyw0    usbdev5.3_ep00
ptyb5      ptyqe  ptyw7  stderr      ttyb5  ttyqe  ttyw1    usbdev5.3_ep87
ptyb6      ptyqf  ptyw8  stdin       ttyb6  ttyqf  ttyw2    vcs
ptyb7      ptyr0  ptyw9  stdout      ttyb7  ttyr0  ttyw3    vcs1
ptyb8      ptyr1  ptywa  tty         ttyb8  ttyr1  ttyw4    vcs2
ptyb9      ptyr2  ptywb  tty0        ttyb9  ttyr2  ttyw5    vcs3
ptyba      ptyr3  ptywc  tty1        ttyba  ttyr3  ttyw6    vcs4
ptybb      ptyr4  ptywd  tty10       ttybb  ttyr4  ttyw7    vcs5
ptybc      ptyr5  ptywe  tty11       ttybc  ttyr5  ttyw8    vcs6
ptybd      ptyr6  ptywf  tty12       ttybd  ttyr6  ttyw9    vcs7
ptybe      ptyr7  ptyx0  tty13       ttybe  ttyr7  ttywa    vcs8
ptybf      ptyr8  ptyx1  tty14       ttybf  ttyr8  ttywb    vcsa
ptyc0      ptyr9  ptyx2  tty15       ttyc0  ttyr9  ttywc    vcsa1
ptyc1      ptyra  ptyx3  tty16       ttyc1  ttyra  ttywd    vcsa2
ptyc2      ptyrb  ptyx4  tty17       ttyc2  ttyrb  ttywe    vcsa3
ptyc3      ptyrc  ptyx5  tty18       ttyc3  ttyrc  ttywf    vcsa4
ptyc4      ptyrd  ptyx6  tty19       ttyc4  ttyrd  ttyx0    vcsa5
ptyc5      ptyre  ptyx7  tty2        ttyc5  ttyre  ttyx1    vcsa6
ptyc6      ptyrf  ptyx8  tty20       ttyc6  ttyrf  ttyx2    vcsa7
ptyc7      ptys0  ptyx9  tty21       ttyc7  ttys0  ttyx3    vcsa8
ptyc8      ptys1  ptyxa  tty22       ttyc8  ttyS0  ttyx4    video0
ptyc9      ptys2  ptyxb  tty23       ttyc9  ttys1  ttyx5    watchdog
ptyca      ptys3  ptyxc  tty24       ttyca  ttyS1  ttyx6    xconsole
ptycb      ptys4  ptyxd  tty25       ttycb  ttys2  ttyx7    zero
n0tmycupoftea@n0tmycupoftea-laptop:/dev$ 

```

Sidenote: Prior to this DVD backup I had to do the UDF 2.5 compatibility installation which I had done, but unfortunately the first time around I wasn't paying attention and had installed the wrong linux-headers (i.e.: linux-headers-2.6.24-18-386) after it finished it asked for a reboot which I had complied to and everything restarted. Upon restart I noticed none of my drives were working, my wireless and bluetooth went to crap too, and knew something was wrong. Luckily I saw it in conky that the kernel had changed from 2.6.24-21-generic to 2.6.24-21-386. I figured that this was the problem and checked my /usr/src folder in which I had 4 folders (linux-headers 2.6.24-18, 2.6.24-18-386, 2.6.24-21, and 2.6.24-21-generic). So I went back and removed the 2.6.24-18-386 folders and rebooted and everything was back to normal and then I continued to properly install the correct linux-headers and got the UDF support to work.

Anyone got any ideas? I'll try to replicate what happened later today after I backup the DVD again. Thanks again!

---

### Post by cariboo on 2008-11-09
There is no device called /dev/dvd its aliased from /dev/cdrom

When using dd you have run the command as root eg:

```
sudo dd if=/dev/scd0 of=dvd.iso
```

/dev/scd0 is th actual device that your dvd is loaded in.

You did this almost right. In order to mount an .iso file just leave it where it is and in a terminal type:

```
sudo mount -o loop ~/desktop/filename.iso /mnt
```

The above command assumes your iso is on the desktop. This will mount your iso image on /mnt

Jim

---

### Post by n0tmycupoftea on 2008-11-09
THANKS! I got confused.

One other thing, is there a way to where /mnt/iso can be read as a device because that's where I was kind of wanting to get at. I want to be able to open up a media player and click open and have my hd, cdrom, and mnt as devices that can be read, where I can then easily select mnt as a device and it plays the iso file as a dvd instead of rather having to click open folder in VLC and point to /mnt to play the iso.

---

### Post by ju2wheels on 2008-11-09
Mount the iso to /media/cdrom0 (thats a zero) and it will be as if you had popped the dvd into the dvd drive. With some applications you have to specifically tell it to look there as they might look at the device /dev/scd0 and not see anything.

---

### Post by n0tmycupoftea on 2008-11-10
Sweet! Worked, thanks again.

---

