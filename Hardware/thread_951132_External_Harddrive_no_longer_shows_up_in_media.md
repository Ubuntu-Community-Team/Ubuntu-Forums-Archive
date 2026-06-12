---
title: "External Harddrive no longer shows up in /media"
date: 2008-10-17
forum: Hardware
---

### Post by lnajt on 2008-10-17
Exactly as the subject says. I bought an External Hard Drive a few weeks ago and it worked fine until a portion of it got corrupted a few days later (I got an IO error when trying to access that part of the drive). Now it won't even show up when I plug it into my computer - thought the light on the Harddrive turns on like its supposed to when I plug the USB cable in.

Any Ideas?

---

### Post by cariboo on 2008-10-17
What is the output of dmesg when you plug the device in? To see the output, in a terminal type:

```
dmesg
```

You should see some sort of error when you plug it in.

Jim

---

### Post by lnajt on 2008-10-18
These were the only errors that I encountered

$ dmesg | grep -i error
[   10.634643] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   31.425771] ACPI: Error installing bay notify handler

They don't seem to have anything to do with an external harddrive... should I grep a different keyword?

What do you mean 'when I plug it in'? I thought dmesg was just a record of the boot up messages, or is there someway to make it into a real time log?

Thanks.

---

### Post by moore.bryan on 2008-10-18
does it show-up in /dev at all? does running "df" tell you anything?

---

### Post by lnajt on 2008-10-19
I don't think it shows up in /dev, but here are the contents in case I missed something (since I don't really know what I'm looking for): 

```
adsp
audio
bus
cdrom
cdrw
console
core
disk
dsp
dvd
dvdrw
fd
full
fuse
hidraw0
hpet
initctl
input
kmem
kmsg
log
loop0
lp0
MAKEDEV
mem
mixer
net
null
nvidia0
nvidiactl
oldmem
parport0
port
ppp
psaux
ptmx
pts
ptya0
ptya1
ptya2
ptya3
ptya4
ptya5
ptya6
ptya7
ptya8
ptya9
ptyaa
ptyab
ptyac
ptyad
ptyae
ptyaf
ptyb0
ptyb1
ptyb2
ptyb3
ptyb4
ptyb5
ptyb6
ptyb7
ptyb8
ptyb9
ptyba
ptybb
ptybc
ptybd
ptybe
ptybf
ptyc0
ptyc1
ptyc2
ptyc3
ptyc4
ptyc5
ptyc6
ptyc7
ptyc8
ptyc9
ptyca
ptycb
ptycc
ptycd
ptyce
ptycf
ptyd0
ptyd1
ptyd2
ptyd3
ptyd4
ptyd5
ptyd6
ptyd7
ptyd8
ptyd9
ptyda
ptydb
ptydc
ptydd
ptyde
ptydf
ptye0
ptye1
ptye2
ptye3
ptye4
ptye5
ptye6
ptye7
ptye8
ptye9
ptyea
ptyeb
ptyec
ptyed
ptyee
ptyef
ptyp0
ptyp1
ptyp2
ptyp3
ptyp4
ptyp5
ptyp6
ptyp7
ptyp8
ptyp9
ptypa
ptypb
ptypc
ptypd
ptype
ptypf
ptyq0
ptyq1
ptyq2
ptyq3
ptyq4
ptyq5
ptyq6
ptyq7
ptyq8
ptyq9
ptyqa
ptyqb
ptyqc
ptyqd
ptyqe
ptyqf
ptyr0
ptyr1
ptyr2
ptyr3
ptyr4
ptyr5
ptyr6
ptyr7
ptyr8
ptyr9
ptyra
ptyrb
ptyrc
ptyrd
ptyre
ptyrf
ptys0
ptys1
ptys2
ptys3
ptys4
ptys5
ptys6
ptys7
ptys8
ptys9
ptysa
ptysb
ptysc
ptysd
ptyse
ptysf
ptyt0
ptyt1
ptyt2
ptyt3
ptyt4
ptyt5
ptyt6
ptyt7
ptyt8
ptyt9
ptyta
ptytb
ptytc
ptytd
ptyte
ptytf
ptyu0
ptyu1
ptyu2
ptyu3
ptyu4
ptyu5
ptyu6
ptyu7
ptyu8
ptyu9
ptyua
ptyub
ptyuc
ptyud
ptyue
ptyuf
ptyv0
ptyv1
ptyv2
ptyv3
ptyv4
ptyv5
ptyv6
ptyv7
ptyv8
ptyv9
ptyva
ptyvb
ptyvc
ptyvd
ptyve
ptyvf
ptyw0
ptyw1
ptyw2
ptyw3
ptyw4
ptyw5
ptyw6
ptyw7
ptyw8
ptyw9
ptywa
ptywb
ptywc
ptywd
ptywe
ptywf
ptyx0
ptyx1
ptyx2
ptyx3
ptyx4
ptyx5
ptyx6
ptyx7
ptyx8
ptyx9
ptyxa
ptyxb
ptyxc
ptyxd
ptyxe
ptyxf
ptyy0
ptyy1
ptyy2
ptyy3
ptyy4
ptyy5
ptyy6
ptyy7
ptyy8
ptyy9
ptyya
ptyyb
ptyyc
ptyyd
ptyye
ptyyf
ptyz0
ptyz1
ptyz2
ptyz3
ptyz4
ptyz5
ptyz6
ptyz7
ptyz8
ptyz9
ptyza
ptyzb
ptyzc
ptyzd
ptyze
ptyzf
ram0
ram1
ram10
ram11
ram12
ram13
ram14
ram15
ram2
ram3
ram4
ram5
ram6
ram7
ram8
ram9
random
rtc
scd0
sda
sda1
sda2
sda5
sequencer
sequencer2
sg0
sg1
shm
snapshot
snd
sndstat
sr0
stderr
stdin
stdout
tty
tty0
tty1
tty10
tty11
tty12
tty13
tty14
tty15
tty16
tty17
tty18
tty19
tty2
tty20
tty21
tty22
tty23
tty24
tty25
tty26
tty27
tty28
tty29
tty3
tty30
tty31
tty32
tty33
tty34
tty35
tty36
tty37
tty38
tty39
tty4
tty40
tty41
tty42
tty43
tty44
tty45
tty46
tty47
tty48
tty49
tty5
tty50
tty51
tty52
tty53
tty54
tty55
tty56
tty57
tty58
tty59
tty6
tty60
tty61
tty62
tty63
tty7
tty8
tty9
ttya0
ttya1
ttya2
ttya3
ttya4
ttya5
ttya6
ttya7
ttya8
ttya9
ttyaa
ttyab
ttyac
ttyad
ttyae
ttyaf
ttyb0
ttyb1
ttyb2
ttyb3
ttyb4
ttyb5
ttyb6
ttyb7
ttyb8
ttyb9
ttyba
ttybb
ttybc
ttybd
ttybe
ttybf
ttyc0
ttyc1
ttyc2
ttyc3
ttyc4
ttyc5
ttyc6
ttyc7
ttyc8
ttyc9
ttyca
ttycb
ttycc
ttycd
ttyce
ttycf
ttyd0
ttyd1
ttyd2
ttyd3
ttyd4
ttyd5
ttyd6
ttyd7
ttyd8
ttyd9
ttyda
ttydb
ttydc
ttydd
ttyde
ttydf
ttye0
ttye1
ttye2
ttye3
ttye4
ttye5
ttye6
ttye7
ttye8
ttye9
ttyea
ttyeb
ttyec
ttyed
ttyee
ttyef
ttyp0
ttyp1
ttyp2
ttyp3
ttyp4
ttyp5
ttyp6
ttyp7
ttyp8
ttyp9
ttypa
ttypb
ttypc
ttypd
ttype
ttypf
ttyq0
ttyq1
ttyq2
ttyq3
ttyq4
ttyq5
ttyq6
ttyq7
ttyq8
ttyq9
ttyqa
ttyqb
ttyqc
ttyqd
ttyqe
ttyqf
ttyr0
ttyr1
ttyr2
ttyr3
ttyr4
ttyr5
ttyr6
ttyr7
ttyr8
ttyr9
ttyra
ttyrb
ttyrc
ttyrd
ttyre
ttyrf
ttys0
ttyS0
ttys1
ttyS1
ttys2
ttyS2
ttys3
ttyS3
ttys4
ttys5
ttys6
ttys7
ttys8
ttys9
ttysa
ttysb
ttysc
ttysd
ttyse
ttysf
ttyt0
ttyt1
ttyt2
ttyt3
ttyt4
ttyt5
ttyt6
ttyt7
ttyt8
ttyt9
ttyta
ttytb
ttytc
ttytd
ttyte
ttytf
ttyu0
ttyu1
ttyu2
ttyu3
ttyu4
ttyu5
ttyu6
ttyu7
ttyu8
ttyu9
ttyua
ttyub
ttyuc
ttyud
ttyue
ttyuf
ttyv0
ttyv1
ttyv2
ttyv3
ttyv4
ttyv5
ttyv6
ttyv7
ttyv8
ttyv9
ttyva
ttyvb
ttyvc
ttyvd
ttyve
ttyvf
ttyw0
ttyw1
ttyw2
ttyw3
ttyw4
ttyw5
ttyw6
ttyw7
ttyw8
ttyw9
ttywa
ttywb
ttywc
ttywd
ttywe
ttywf
ttyx0
ttyx1
ttyx2
ttyx3
ttyx4
ttyx5
ttyx6
ttyx7
ttyx8
ttyx9
ttyxa
ttyxb
ttyxc
ttyxd
ttyxe
ttyxf
ttyy0
ttyy1
ttyy2
ttyy3
ttyy4
ttyy5
ttyy6
ttyy7
ttyy8
ttyy9
ttyya
ttyyb
ttyyc
ttyyd
ttyye
ttyyf
ttyz0
ttyz1
ttyz2
ttyz3
ttyz4
ttyz5
ttyz6
ttyz7
ttyz8
ttyz9
ttyza
ttyzb
ttyzc
ttyzd
ttyze
ttyzf
urandom
usbdev1.1_ep00
usbdev1.1_ep81
usbdev1.2_ep00
usbdev1.2_ep02
usbdev1.2_ep03
usbdev1.2_ep81
usbdev1.2_ep82
usbdev1.2_ep83
usbdev2.1_ep00
usbdev2.1_ep81
usbdev3.1_ep00
usbdev3.1_ep81
usbdev3.3_ep00
usbdev3.3_ep81
usbdev3.4_ep00
usbdev3.4_ep81
usbdev4.1_ep00
usbdev4.1_ep81
usbdev5.1_ep00
usbdev5.1_ep81
usbdev6.1_ep00
usbdev6.1_ep81
usbdev6.2_ep00
usbdev6.2_ep81
usbdev6.3_ep00
usbdev6.3_ep03
usbdev6.3_ep81
usbdev6.3_ep82
usbdev7.1_ep00
usbdev7.1_ep81
vcs
vcs1
vcs2
vcs3
vcs4
vcs5
vcs6
vcs7
vcs8
vcsa
vcsa1
vcsa2
vcsa3
vcsa4
vcsa5
vcsa6
vcsa7
vcsa8
watchdog
xconsole
zero
```

and the results of df:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            111528868  87547812  18360316  83% /
varrun                 1037108       124   1036984   1% /var/run
varlock                1037108         0   1037108   0% /var/lock
udev                   1037108        52   1037056   1% /dev
devshm                 1037108         0   1037108   0% /dev/shm
lrm                    1037108     39780    997328   4% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon     111528868  87547812  18360316  83% /home/lnajt/.gvfs

it doesn't show up here either.

---

### Post by moore.bryan on 2008-10-19
you're right, it's in neither. for the /dev, i was assuming your internal hard-drive was sda# and the external would then--by default--be sdb#. since you don't have it there and your df resulted in no /dev/sdb#, we can assume ubuntu's not recognizing it AT ALL. have you tried to fire-up gparted and see if it sees it? i don't think it will because it's not even in /dev; very strange. do you happen to know what occured to make part of the drive "corrupted?"

---

### Post by lnajt on 2008-10-19
No, gparted cannot see it either.

The only thing I can think of is that when I was setting up Ubuntu on my laptop I used the harddrive somewhat carelessly during the transfer of wireless drivers, etc. I may have force mounted it or forgotten to unmount before unplugging it at least once.

---

### Post by lnajt on 2008-10-19
Update:

I just plugged the external harddrive in and I got a 'Cannot mount volume' error:

(I copied it by hand, so there may be type-o's)

ntfs_attr_pread: ntfs_preed failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error NTFS is either inconsistent or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into windows TWICE. The usage of the /f parameter is very Important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/directory (e.g. dev/mapper/nvidia_eahaabcc1). Please see 'dmraid' documentation for the details.

I guess I'll take their advice and run chkdsk, what do you think?

Thanks,

lnajt

---

### Post by moore.bryan on 2008-10-19
> **lnajt said:**
> No, gparted cannot see it either.

The only thing I can think of is that when I was setting up Ubuntu on my laptop I used the harddrive somewhat carelessly during the transfer of wireless drivers, etc. I may have force mounted it or forgotten to unmount before unplugging it at least once.
good news/bad news... good news: i don't think accidentally/improperly unmounting could have led to your problem. bad news: i have no idea what could have.
> **lnajt said:**
> Update:

I just plugged the external harddrive in and I got a 'Cannot mount volume' error:

(I copied it by hand, so there may be type-o's)

ntfs_attr_pread: ntfs_preed failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error NTFS is either inconsistent or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into windows TWICE. The usage of the /f parameter is very Important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/directory (e.g. dev/mapper/nvidia_eahaabcc1). Please see 'dmraid' documentation for the details.

I guess I'll take their advice and run chkdsk, what do you think?

Thanks,

lnajt
chkdsk can't hurt, but as a side-note, why is your external formatted ntfs?

---

### Post by lnajt on 2008-10-22
I don't know why it is formatted NTFS - I presume I bought it that way.

In addition, it turns out that the USB cable was flawed - after switching it my Harddrive works perfectly (with the exception of the flawed sectors).

I just ran chkdsk off of a Windows XP home machine and now the corrupted folders are simply missing. 

Is there someway to recover the data now?

Nevermind ... good old find | grep (they were in a hidden folder)

---

### Post by moore.bryan on 2008-10-23
> **lnajt said:**
> I don't know why it is formatted NTFS - I presume I bought it that way.
fair enough.
> 
In addition, it turns out that the USB cable was flawed - after switching it my Harddrive works perfectly (with the exception of the flawed sectors).

excellent! ockham had it right!
> 
I just ran chkdsk off of a Windows XP home machine and now the corrupted folders are simply missing. 

Is there someway to recover the data now?

Nevermind ... good old find | grep (they were in a hidden folder)
congrats...

---

