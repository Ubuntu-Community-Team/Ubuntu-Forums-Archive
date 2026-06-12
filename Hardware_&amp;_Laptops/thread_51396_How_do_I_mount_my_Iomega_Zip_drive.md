---
title: "How do I mount my Iomega Zip drive?"
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by Dragoon_42 on 2005-07-23
Here's my /dev.  I'm new to Linux, having just switched from FreeBSD.
```

admmidi  ptya0  ptyec  ptyt8  ptyy4    tty28  ttyc1  ttyqd   ttyS6  ttywf
adsp     ptya1  ptyed  ptyt9  ptyy5    tty29  ttyc2  ttyqe   ttys7  ttyx0
adsp1    ptya2  ptyee  ptyta  ptyy6    tty3   ttyc3  ttyqf   ttyS7  ttyx1
agpgart  ptya3  ptyef  ptytb  ptyy7    tty30  ttyc4  ttyr0   ttys8  ttyx2
amidi    ptya4  ptyp0  ptytc  ptyy8    tty31  ttyc5  ttyr1   ttyS8  ttyx3
audio    ptya5  ptyp1  ptytd  ptyy9    tty32  ttyc6  ttyr2   ttys9  ttyx4
audio1   ptya6  ptyp2  ptyte  ptyya    tty33  ttyc7  ttyr3   ttyS9  ttyx5
cdrom    ptya7  ptyp3  ptytf  ptyyb    tty34  ttyc8  ttyr4   ttysa  ttyx6
cdrw     ptya8  ptyp4  ptyu0  ptyyc    tty35  ttyc9  ttyr5   ttysb  ttyx7
console  ptya9  ptyp5  ptyu1  ptyyd    tty36  ttyca  ttyr6   ttysc  ttyx8
core     ptyaa  ptyp6  ptyu2  ptyye    tty37  ttycb  ttyr7   ttysd  ttyx9
dmmidi   ptyab  ptyp7  ptyu3  ptyyf    tty38  ttycc  ttyr8   ttyse  ttyxa
dri      ptyac  ptyp8  ptyu4  ptyz0    tty39  ttycd  ttyr9   ttysf  ttyxb
dsp      ptyad  ptyp9  ptyu5  ptyz1    tty4   ttyce  ttyra   ttyt0  ttyxc
dsp1     ptyae  ptypa  ptyu6  ptyz2    tty40  ttycf  ttyrb   ttyt1  ttyxd
dvd      ptyaf  ptypb  ptyu7  ptyz3    tty41  ttyd0  ttyrc   ttyt2  ttyxe
evms     ptyb0  ptypc  ptyu8  ptyz4    tty42  ttyd1  ttyrd   ttyt3  ttyxf
fd       ptyb1  ptypd  ptyu9  ptyz5    tty43  ttyd2  ttyre   ttyt4  ttyy0
fd0      ptyb2  ptype  ptyua  ptyz6    tty44  ttyd3  ttyrf   ttyt5  ttyy1
full     ptyb3  ptypf  ptyub  ptyz7    tty45  ttyd4  ttys0   ttyt6  ttyy2
hda      ptyb4  ptyq0  ptyuc  ptyz8    tty46  ttyd5  ttyS0   ttyt7  ttyy3
hda1     ptyb5  ptyq1  ptyud  ptyz9    tty47  ttyd6  ttys1   ttyt8  ttyy4
hda2     ptyb6  ptyq2  ptyue  ptyza    tty48  ttyd7  ttyS1   ttyt9  ttyy5
hda3     ptyb7  ptyq3  ptyuf  ptyzb    tty49  ttyd8  ttyS10  ttyta  ttyy6
hda5     ptyb8  ptyq4  ptyv0  ptyzc    tty5   ttyd9  ttyS11  ttytb  ttyy7
hdb      ptyb9  ptyq5  ptyv1  ptyzd    tty50  ttyda  ttyS12  ttytc  ttyy8
hdb4     ptyba  ptyq6  ptyv2  ptyze    tty51  ttydb  ttyS13  ttytd  ttyy9
hdc      ptybb  ptyq7  ptyv3  ptyzf    tty52  ttydc  ttyS14  ttyte  ttyya
hdd      ptybc  ptyq8  ptyv4  radio0   tty53  ttydd  ttyS15  ttytf  ttyyb
hpet     ptybd  ptyq9  ptyv5  ram0     tty54  ttyde  ttyS16  ttyu0  ttyyc
initctl  ptybe  ptyqa  ptyv6  ram1     tty55  ttydf  ttyS17  ttyu1  ttyyd
input    ptybf  ptyqb  ptyv7  ram10    tty56  ttye0  ttyS18  ttyu2  ttyye
kmem     ptyc0  ptyqc  ptyv8  ram11    tty57  ttye1  ttyS19  ttyu3  ttyyf
kmsg     ptyc1  ptyqd  ptyv9  ram12    tty58  ttye2  ttys2   ttyu4  ttyz0
log      ptyc2  ptyqe  ptyva  ram13    tty59  ttye3  ttyS2   ttyu5  ttyz1
loop     ptyc3  ptyqf  ptyvb  ram14    tty6   ttye4  ttyS20  ttyu6  ttyz2
lp0      ptyc4  ptyr0  ptyvc  ram15    tty60  ttye5  ttyS21  ttyu7  ttyz3
lvm      ptyc5  ptyr1  ptyvd  ram2     tty61  ttye6  ttyS22  ttyu8  ttyz4
MAKEDEV  ptyc6  ptyr2  ptyve  ram3     tty62  ttye7  ttyS23  ttyu9  ttyz5
mapper   ptyc7  ptyr3  ptyvf  ram4     tty63  ttye8  ttyS24  ttyua  ttyz6
md0      ptyc8  ptyr4  ptyw0  ram5     tty7   ttye9  ttyS25  ttyub  ttyz7
md1      ptyc9  ptyr5  ptyw1  ram6     tty8   ttyea  ttyS26  ttyuc  ttyz8
md10     ptyca  ptyr6  ptyw2  ram7     tty9   ttyeb  ttyS27  ttyud  ttyz9
md11     ptycb  ptyr7  ptyw3  ram8     ttya0  ttyec  ttyS28  ttyue  ttyza
md12     ptycc  ptyr8  ptyw4  ram9     ttya1  ttyed  ttyS29  ttyuf  ttyzb
md13     ptycd  ptyr9  ptyw5  random   ttya2  ttyee  ttys3   ttyv0  ttyzc
md14     ptyce  ptyra  ptyw6  raw1394  ttya3  ttyef  ttyS3   ttyv1  ttyzd
md15     ptycf  ptyrb  ptyw7  rtc      ttya4  ttyp0  ttyS30  ttyv2  ttyze
md16     ptyd0  ptyrc  ptyw8  shm      ttya5  ttyp1  ttyS31  ttyv3  ttyzf
md17     ptyd1  ptyrd  ptyw9  snd      ttya6  ttyp2  ttyS32  ttyv4  urandom
md18     ptyd2  ptyre  ptywa  sndstat  ttya7  ttyp3  ttyS33  ttyv5  vbi0
md19     ptyd3  ptyrf  ptywb  stderr   ttya8  ttyp4  ttyS34  ttyv6  vcs
md2      ptyd4  ptys0  ptywc  stdin    ttya9  ttyp5  ttyS35  ttyv7  vcs1
md20     ptyd5  ptys1  ptywd  stdout   ttyaa  ttyp6  ttyS36  ttyv8  vcs2
md21     ptyd6  ptys2  ptywe  tty      ttyab  ttyp7  ttyS37  ttyv9  vcs3
md22     ptyd7  ptys3  ptywf  tty0     ttyac  ttyp8  ttyS38  ttyva  vcs4
md23     ptyd8  ptys4  ptyx0  tty1     ttyad  ttyp9  ttyS39  ttyvb  vcs5
md24     ptyd9  ptys5  ptyx1  tty10    ttyae  ttypa  ttys4   ttyvc  vcs6
md3      ptyda  ptys6  ptyx2  tty11    ttyaf  ttypb  ttyS4   ttyvd  vcs7
md4      ptydb  ptys7  ptyx3  tty12    ttyb0  ttypc  ttyS40  ttyve  vcsa
md5      ptydc  ptys8  ptyx4  tty13    ttyb1  ttypd  ttyS41  ttyvf  vcsa1
md6      ptydd  ptys9  ptyx5  tty14    ttyb2  ttype  ttyS42  ttyw0  vcsa2
md7      ptyde  admmidi  ptya0  ptyec  ptyt8  ptyy4    tty28  ttyc1  ttyqd   ttyS6  ttywf
adsp     ptya1  ptyed  ptyt9  ptyy5    tty29  ttyc2  ttyqe   ttys7  ttyx0
adsp1    ptya2  ptyee  ptyta  ptyy6    tty3   ttyc3  ttyqf   ttyS7  ttyx1
agpgart  ptya3  ptyef  ptytb  ptyy7    tty30  ttyc4  ttyr0   ttys8  ttyx2
amidi    ptya4  ptyp0  ptytc  ptyy8    tty31  ttyc5  ttyr1   ttyS8  ttyx3
audio    ptya5  ptyp1  ptytd  ptyy9    tty32  ttyc6  ttyr2   ttys9  ttyx4
audio1   ptya6  ptyp2  ptyte  ptyya    tty33  ttyc7  ttyr3   ttyS9  ttyx5
cdrom    ptya7  ptyp3  ptytf  ptyyb    tty34  ttyc8  ttyr4   ttysa  ttyx6
cdrw     ptya8  ptyp4  ptyu0  ptyyc    tty35  ttyc9  ttyr5   ttysb  ttyx7
console  ptya9  ptyp5  ptyu1  ptyyd    tty36  ttyca  ttyr6   ttysc  ttyx8
core     ptyaa  ptyp6  ptyu2  ptyye    tty37  ttycb  ttyr7   ttysd  ttyx9
dmmidi   ptyab  ptyp7  ptyu3  ptyyf    tty38  ttycc  ttyr8   ttyse  ttyxa
dri      ptyac  ptyp8  ptyu4  ptyz0    tty39  ttycd  ttyr9   ttysf  ttyxb
dsp      ptyad  ptyp9  ptyu5  ptyz1    tty4   ttyce  ttyra   ttyt0  ttyxc
dsp1     ptyae  ptypa  ptyu6  ptyz2    tty40  ttycf  ttyrb   ttyt1  ttyxd
dvd      ptyaf  ptypb  ptyu7  ptyz3    tty41  ttyd0  ttyrc   ttyt2  ttyxe
evms     ptyb0  ptypc  ptyu8  ptyz4    tty42  ttyd1  ttyrd   ttyt3  ttyxf
fd       ptyb1  ptypd  ptyu9  ptyz5    tty43  ttyd2  ttyre   ttyt4  ttyy0
fd0      ptyb2  ptype  ptyua  ptyz6    tty44  ttyd3  ttyrf   ttyt5  ttyy1
full     ptyb3  ptypf  ptyub  ptyz7    tty45  ttyd4  ttys0   ttyt6  ttyy2
hda      ptyb4  ptyq0  ptyuc  ptyz8    tty46  ttyd5  ttyS0   ttyt7  ttyy3
hda1     ptyb5  ptyq1  ptyud  ptyz9    tty47  ttyd6  ttys1   ttyt8  ttyy4
hda2     ptyb6  ptyq2  ptyue  ptyza    tty48  ttyd7  ttyS1   ttyt9  ttyy5
hda3     ptyb7  ptyq3  ptyuf  ptyzb    tty49  ttyd8  ttyS10  ttyta  ttyy6
hda5     ptyb8  ptyq4  ptyv0  ptyzc    tty5   ttyd9  ttyS11  ttytb  ttyy7
hdb      ptyb9  ptyq5  ptyv1  ptyzd    tty50  ttyda  ttyS12  ttytc  ttyy8
hdb4     ptyba  ptyq6  ptyv2  ptyze    tty51  ttydb  ttyS13  ttytd  ttyy9
hdc      ptybb  ptyq7  ptyv3  ptyzf    tty52  ttydc  ttyS14  ttyte  ttyya
hdd      ptybc  ptyq8  ptyv4  radio0   tty53  ttydd  ttyS15  ttytf  ttyyb
hpet     ptybd  ptyq9  ptyv5  ram0     tty54  ttyde  ttyS16  ttyu0  ttyyc
initctl  ptybe  ptyqa  ptyv6  ram1     tty55  ttydf  ttyS17  ttyu1  ttyyd
input    ptybf  ptyqb  ptyv7  ram10    tty56  ttye0  ttyS18  ttyu2  ttyye
kmem     ptyc0  ptyqc  ptyv8  ram11    tty57  ttye1  ttyS19  ttyu3  ttyyf
kmsg     ptyc1  ptyqd  ptyv9  ram12    tty58  ttye2  ttys2   ttyu4  ttyz0
log      ptyc2  ptyqe  ptyva  ram13    tty59  ttye3  ttyS2   ttyu5  ttyz1
loop     ptyc3  ptyqf  ptyvb  ram14    tty6   ttye4  ttyS20  ttyu6  ttyz2
lp0      ptyc4  ptyr0  ptyvc  ram15    tty60  ttye5  ttyS21  ttyu7  ttyz3
lvm      ptyc5  ptyr1  ptyvd  ram2     tty61  ttye6  ttyS22  ttyu8  ttyz4
MAKEDEV  ptyc6  ptyr2  ptyve  ram3     tty62  ttye7  ttyS23  ttyu9  ttyz5
mapper   ptyc7  ptyr3  ptyvf  ram4     tty63  ttye8  ttyS24  ttyua  ttyz6
md0      ptyc8  ptyr4  ptyw0  ram5     tty7   ttye9  ttyS25  ttyub  ttyz7
md1      ptyc9  ptyr5  ptyw1  ram6     tty8   ttyea  ttyS26  ttyuc  ttyz8
md10     ptyca  ptyr6  ptyw2  ram7     tty9   ttyeb  ttyS27  ttyud  ttyz9
md11     ptycb  ptyr7  ptyw3  ram8     ttya0  ttyec  ttyS28  ttyue  ttyza
md12     ptycc  ptyr8  ptyw4  ram9     ttya1  ttyed  ttyS29  ttyuf  ttyzb
md13     ptycd  ptyr9  ptyw5  random   ttya2  ttyee  ttys3   ttyv0  ttyzc
md14     ptyce  ptyra  ptyw6  raw1394  ttya3  ttyef  ttyS3   ttyv1  ttyzd
md15     ptycf  ptyrb  ptyw7  rtc      ttya4  ttyp0  ttyS30  ttyv2  ttyze
md16     ptyd0  ptyrc  ptyw8  shm      ttya5  ttyp1  ttyS31  ttyv3  ttyzf
md17     ptyd1  ptyrd  ptyw9  snd      ttya6  ttyp2  ttyS32  ttyv4  urandom
md18     ptyd2  ptyre  ptywa  sndstat  ttya7  ttyp3  ttyS33  ttyv5  vbi0
md19     ptyd3  ptyrf  ptywb  stderr   ttya8  ttyp4  ttyS34  ttyv6  vcs
md2      ptyd4  ptys0  ptywc  stdin    ttya9  ttyp5  ttyS35  ttyv7  vcs1
md20     ptyd5  ptys1  ptywd  stdout   ttyaa  ttyp6  ttyS36  ttyv8  vcs2
md21     ptyd6  ptys2  ptywe  tty      ttyab  ttyp7  ttyS37  ttyv9  vcs3
md22     ptyd7  ptys3  ptywf  tty0     ttyac  ttyp8  ttyS38  ttyva  vcs4
md23     ptyd8  ptys4  ptyx0  tty1     ttyad  ttyp9  ttyS39  ttyvb  vcs5
md24     ptyd9  ptys5  ptyx1  tty10    ttyae  ttypa  ttys4   ttyvc  vcs6
md3      ptyda  ptys6  ptyx2  tty11    ttyaf  ttypb  ttyS4   ttyvd  vcs7
md4      ptydb  ptys7  ptyx3  tty12    ttyb0  ttypc  ttyS40  ttyve  vcsa
md5      ptydc  ptys8  ptyx4  tty13    ttyb1  ttypd  ttyS41  ttyvf  vcsa1
md6      ptydd  ptys9  ptyx5  tty14    ttyb2  ttype  ttyS42  ttyw0  vcsa2
md7      ptyde  ptysa  ptyx6  tty15    ttyb3  ttypf  ttyS43  ttyw1  vcsa3
md8      ptydf  ptysb  ptyx7  tty16    ttyb4  ttyq0  ttyS44  ttyw2  vcsa4
md9      ptye0  ptysc  ptyx8  tty17    ttyb5  ttyq1  ttyS45  ttyw3  vcsa5
mem      ptye1  ptysd  ptyx9  tty18    ttyb6  ttyq2  ttyS46  ttyw4  vcsa6
midi     ptye2  ptyse  ptyxa  tty19    ttyb7  ttyq3  ttyS47  ttyw5  vcsa7
mixer    ptye3  ptysf  ptyxb  tty2     ttyb8  ttyq4  ttyS48  ttyw6  video0
mixer1   ptye4  ptyt0  ptyxc  tty20    ttyb9  ttyq5  ttyS49  ttyw7  video1394
net      ptye5  ptyt1  ptyxd  tty21    ttyba  ttyq6  ttys5   ttyw8  xconsole
null     ptye6  ptyt2  ptyxe  tty22    ttybb  ttyq7  ttyS5   ttyw9  zero
port     ptye7  ptyt3  ptyxf  tty23    ttybc  ttyq8  ttyS50  ttywa
ppp      ptye8  ptyt4  ptyy0  tty24    ttybd  ttyq9  ttyS51  ttywb
psaux    ptye9  ptyt5  ptyy1  tty25    ttybe  ttyqa  ttyS52  ttywc
ptmx     ptyea  ptyt6  ptyy2  tty26    ttybf  ttyqb  ttyS53  ttywd
pts      ptyeb  ptyt7  ptyy3  tty27    ttyc0  ttyqc  ttys6   ttywe
ptysa  ptyx6  tty15    ttyb3  ttypf  ttyS43  ttyw1  vcsa3
md8      ptydf  ptysb  ptyx7  tty16    ttyb4  ttyq0  ttyS44  ttyw2  vcsa4
md9      ptye0  ptysc  ptyx8  tty17    ttyb5  ttyq1  ttyS45  ttyw3  vcsa5
mem      ptye1  ptysd  ptyx9  tty18    ttyb6  ttyq2  ttyS46  ttyw4  vcsa6
midi     ptye2  ptyse  ptyxa  tty19    ttyb7  ttyq3  ttyS47  ttyw5  vcsa7
mixer    ptye3  ptysf  ptyxb  tty2     ttyb8  ttyq4  ttyS48  ttyw6  video0
mixer1   ptye4  ptyt0  ptyxc  tty20    ttyb9  ttyq5  ttyS49  ttyw7  video1394
net      ptye5  ptyt1  ptyxd  tty21    ttyba  ttyq6  ttys5   ttyw8  xconsole
null     ptye6  ptyt2  ptyxe  tty22    ttybb  ttyq7  ttyS5   ttyw9  zero
port     ptye7  ptyt3  ptyxf  tty23    ttybc  ttyq8  ttyS50  ttywa
ppp      ptye8  ptyt4  ptyy0  tty24    ttybd  ttyq9  ttyS51  ttywb
psaux    ptye9  ptyt5  ptyy1  tty25    ttybe  ttyqa  ttyS52  ttywc
ptmx     ptyea  ptyt6  ptyy2  tty26    ttybf  ttyqb  ttyS53  ttywd
pts      ptyeb  ptyt7  ptyy3  tty27    ttyc0  ttyqc  ttys6   ttywe

```

---

### Post by bfonseca on 2006-05-02
Hi, create a directory and then just mount the zip to it:

mkdir /media/zip0
mount -t vfat dev/hdb4 /media/zip0/

hopefully that works for you or at least gets you started.
Brian

---

### Post by jackbg2 on 2007-11-12
This will be a nobrainer for one who is familure with terminal. Could you give me or us alittle more detail, for instance, from aterminal promp that  reads jack on jacks rig-3 what would I type?  Thanks jackbg2

---

### Post by silbar on 2007-11-25
Brian wrote

[QUOTE=bfonseca;977657]Hi, create a directory and then just mount the zip to it:

mkdir /media/zip0
mount -t vfat dev/hdb4 /media/zip0/

Small correction: put in the first slash: mount -t vfat /dev/hdb4 /media/zip0/ .

My trouble was/is that I don't have any such hdb4 (or hda4) device in MY /dev/ directory.
So, how do I create such a block special file in /dev/?  I haven't found any great hints
on reading my"Essential System Administration" book.

What I did to get the zip to work, after a lot of experimentation, was

umount /dev/hda7    #which is a Windows partition, Win98F, that I don't often need
mount -t vfat /dev/hda7 /media/zip0/

Now the File Browser (on reloading) shows the zip drive as an entry under File System.
And I can copy things into it from the desktop,  As an oddity, the browser also shows
the Win98F partition, but it is empty (no surprise).

To get the zip drive out, umount /dev/hda7 and eject.  What does surprise me is that,
after that, the File Browser still shows the zip drive with its new contents AND the
Win98F, still empty.

Any help in how to create a /dev/hda4 block file would be greatly appreciated.

   Dick Silbar

---

