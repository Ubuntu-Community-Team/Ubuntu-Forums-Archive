---
title: "Computer hangs and display breaks into horizontal lines"
date: 2015-12-08
forum: Hardware
---

### Post by ChrisOfBristol on 2015-12-08
I've just installed Ubuntu MATE 15:10 on an HP DC5100 which has this 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)


During installation the screen frequently broke up into horizontal lines and it still does it occasionally. The sequence is a slight pause, a black screen then the lines. {edit}Sometimes I get logged out too. Repainting the screen by using alt-tab or something similar, clears it./{edit}


I'm not sure if this related or is a second problem: YouTube HTML5 videos play in both Firefox and Chrome. BBC Flash videos play fine in Firefox but in Chrome just show a slow sequence of stills.


I looked in syslog and found this:


HPC kernel: [ 3484.984040] [drm] stuck on render ring
Dec  7 18:35:24 HPC kernel: [ 3484.985811] [drm] GPU HANG: ecode 3:0:0x7e71ffc0, in Xorg [885], reason: Ring hung, action: reset


Which directed me to sys/class/drm0/error which contains the following:


GPU HANG: ecode 3:0:0x16dfffc1, in Xorg [885], reason: Ring hung, action: reset
Time: 1449512410 s 33897 us
Kernel: 4.2.0-19-generic
Active process (on ring render): Xorg [885]
Reset count: 0
Suspend count: 0
PCI ID: 0x2582
EIR: 0x00000000
IER: 0x00000053
PGTBL_ER: 0x00000000
FORCEWAKE: 0x00000000
DERRMR: 0x00000000
CCID: 0x00000000
Missed interrupts: 0x00000000
  fence[0] = 01000341
  fence[1] = 0b000021
  fence[2] = 0b800331
  fence[3] = 06000341
  fence[4] = 00400011
  fence[5] = 03a00041
  fence[6] = 04800341
  fence[7] = 02800331
  INSTDONE_0: 0x03ffffc1
  INSTDONE_1: 0x00000000
  INSTDONE_2: 0x00000000
  INSTDONE_3: 0x00000000
render command stream:
  START: 0x00500000
  HEAD:  0x0721bd70
  TAIL:  0x0001bdd8
  CTL:   0x0001f001
  HWS:   0x00000000
  ACTHD: 0x00000000 019000c8
  IPEIR: 0x00000000
  IPEHR: 0x15200000
  INSTDONE: 0x03ffffc1
  INSTPM: 0x00000800
  FADDR: 0x00000000 01900880
  seqno: 0x0002d4b8
  waiting: yes
  ring->head: 0x0001ffd0
  ring->tail: 0x0001bdd8
  hangcheck: hung [40]
vm[0]
  Active [9]:
    01900000    16384 7e 00 [ 2d4b9 00 00 00 00 ] 00 dirty uncached
    0b000000    32768 02 00 [ 2d4b9 00 00 00 00 ] 2d4b9 X dirty render uncached (fence: 1)
    0e700000     4096 7e 00 [ 2d4ba 00 00 00 00 ] 00 dirty uncached
    09000000     4096 7e 00 [ 2d4bb 00 00 00 00 ] 00 dirty uncached
    01000000  8388608 02 00 [ 2d4bb 00 00 00 00 ] 2d4bb P X dirty render uncached (name: 2) (fence: 0)
    04800000  7471104 02 00 [ 2d4bb 00 00 00 00 ] 2d4bb X dirty render uncached (fence: 6)
    03b01000    12288 37 00 [ 2d4bb 00 00 00 00 ] 00 dirty uncached
    08c00000  4194304 36 00 [ 2d4bb 00 00 00 00 ] 00 Y dirty uncached
    0a96f000   262144 37 00 [ 2d4bb 00 00 00 00 ] 00 dirty uncached
  Pinned [3]:
    00500000   131072 40 40 [ 00 00 00 00 00 ] 00 P dirty uncached
    00520000  5242880 41 00 [ 00 00 00 00 00 ] 00 P uncached
    01000000  8388608 02 00 [ 2d4bb 00 00 00 00 ] 2d4bb P X dirty render uncached (name: 2) (fence: 0)
render ring (submitted by Xorg [885]) --- gtt_offset = 0x01900000


{Followed by a load of hex numbers and some more details.&#65279;}

---

### Post by ch43 on 2015-12-08
I know this is a longshot but try installing the Intel Graphics Installer for Linux. There's a .deb file for wily (15.10) that you can install with dpkg. The current version is 1.2.1 and it is available on Intel's o1 website.

[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

On another note; did you ever encounter such graphics artifacts before with that machine? If you had to install a "new" card, do you have an AGP port available? It's a Vista-era PC, not saying its bad hardware but just something to consider. :)

---

### Post by ChrisOfBristol on 2015-12-09
> **ch43 said:**
> I know this is a longshot but try installing the Intel Graphics Installer for Linux. There's a .deb file for wily (15.10) that you can install with dpkg. The current version is 1.2.1 and it is available on Intel's o1 website.No difference unfortunately.
> On another note; did you ever encounter such graphics artifacts before with that machine?I've only just got it.
> If you had to install a "new" card [COLOR=#000000]do you have an AGP port available? It's a Vista-era PC, not saying its bad hardware but just something to consider. [/COLOR]I thought AGP slots were dated? The PC has an 18 pin PCI Express slot, would it be possible to get a video card to fit that, and would it solve the problem do you think?

---

### Post by ChrisOfBristol on 2016-01-10
All sorted - nothing to do with Ubuntu of course! I have installed a PCI Express x16  graphics card. It couldn't find a x1 (18 pin) one so I have sawn off the end of the socket to make it fit. The idea came from a great YouTube video about sawing off the unusable pins from the card. Clever technology means that it is able to work with however many channels it can see - and I don't need the extra speed given by the other channels.

---

