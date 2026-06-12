---
title: "A problem with my CD/DVD writer"
date: 2021-09-15
forum: Hardware
---

### Post by pascal111 on 2021-09-15
I installed Ubuntu yesterday, it's "Ubuntu 20.04.3 LTS", connected to internet and Ubuntu showed a message for updates and I updated softwares. The problem is that I'm learning making audio music CD's, and although there's no troubles happened in my Ubuntu installation and furthermore I installed K3b, Brasero and Xfburn trying to test my DVD writer on Linux, but I failed writing DVD or CD discs by all of the three applications I mentioned and had an error message that writing isn't supported. I used my laptop writer before when I was using Windows to burn some CD's and I made it successfully.

I checked my DVD writer with this command:

```

pascal@pascal-Lenovo-ideapad-330-15AST:~$ cat /proc/sys/dev/cdrom/info
CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:        sr0
drive speed:        24
drive # of slots:    1
Can close tray:        1
Can open tray:        1
Can lock tray:        1
Can change speed:    1
Can select disk:    0
Can read multisession:    1
Can read MCN:        1
Reports media changed:    1
Can play audio:        1
Can write CD-R:        1
Can write CD-RW:    1
Can read DVD:        1
Can write DVD-R:    1
Can write DVD-RAM:    1
Can read MRW:        1
Can write MRW:        1
Can write RAM:        1


```

I'm not sure of the meaning of the result of the command but I'm still a beginner.

My computer infos. with "inxi" command is like this:

```

pascal@pascal-Lenovo-ideapad-330-15AST:~$ inxi -Fxzd 
System:
  Kernel: 5.11.0-34-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 81D6 v: Lenovo ideapad 330-15AST 
  serial: <filter> 
  Mobo: LENOVO model: LNVNB161216 v: No DPK serial: <filter> UEFI: LENOVO 
  v: 8UCN06WW date: 04/10/2018 
Battery:
  ID-1: BAT0 charge: 16.4 Wh condition: 19.8/30.6 Wh (65%) 
  model: CPT-COS L16C2PB2 status: Charging 
CPU:
  Topology: Dual Core model: AMD E2-9000 RADEON R2 4 COMPUTE CORES 2C+2G 
  bits: 64 type: MCP arch: Excavator L2 cache: 1024 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 7200 
  Speed: 1392 MHz min/max: 1200/1800 MHz Core speeds (MHz): 1: 1224 2: 1241 
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] vendor: Lenovo 
  driver: amdgpu v: kernel bus ID: 00:01.0 
  Display: x11 server: X.Org 1.20.11 driver: amdgpu 
  resolution: 1366x768~60Hz 
  OpenGL: renderer: AMD STONEY (DRM 3.40.0 5.11.0-34-generic LLVM 12.0.0) 
  v: 4.5 Mesa 21.0.3 direct render: Yes 
Audio:
  Device-1: AMD vendor: Lenovo driver: snd_hda_intel v: kernel 
  bus ID: 00:01.1 
  Device-2: AMD Family 15h Audio vendor: Lenovo driver: snd_hda_intel 
  v: kernel bus ID: 00:09.2 
  Sound Server: ALSA v: k5.11.0-34-generic 
Network:
  Device-1: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter 
  vendor: Lenovo driver: rtw_8821ce v: N/A port: 2000 bus ID: 01:00.0 
  IF: wlp1s0 state: down mac: <filter> 
  Device-2: Realtek RTL810xE PCI Express Fast Ethernet vendor: Lenovo 
  driver: r8169 v: kernel port: 1000 bus ID: 02:00.0 
  IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 931.51 GiB used: 12.24 GiB (1.3%) 
  ID-1: /dev/sda vendor: Western Digital model: WD10SPZX-24Z10T0 
  size: 931.51 GiB temp: 42 C 
  Optical-1: /dev/sr0 vendor: HL-DT-ST model: DVDRAM GUE0N rev: T.02 
  dev-links: cdrom,cdrw,dvd,dvdrw 
  Features: speed: 24 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram state: running 
Partition:
  ID-1: / size: 915.40 GiB used: 12.23 GiB (1.3%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 47.8 C mobo: N/A gpu: amdgpu temp: 47 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 215 Uptime: 21m Memory: 3.65 GiB used: 1.83 GiB (50.1%) 
  Init: systemd runlevel: 5 Compilers: gcc: N/A Shell: bash v: 5.0.17 
  inxi: 3.0.38 


```

---

### Post by scdbackup on 2021-09-16
(Sorry, this post had malformed code blocks probably because the site does not like my old workstation browser.
I repeated it below with a younger one.)

---

### Post by scdbackup on 2021-09-16
Hi,

can you show such a refusal message literally ?
(Only then it is possible to search it in the program's code.)

The writer should indeed be able to burn audio CDs. So the message might
come due to the medium type or status.

What do you get from this program run ?
```

xorriso -outdev /dev/sr0 -list_profiles out -toc

```
It is supposed to put out a list of supported medium types and formatting
states. Like
```

Drive type   : vendor 'HL-DT-ST' product 'BDDVDRW GGC-H20L' revision '1.03'
Profile      : 0x0040 (BD-ROM)
Profile      : 0x0050 (HD-DVD-ROM)
Profile      : 0x0012 (DVD-RAM)
Profile      : 0x0011 (DVD-R sequential recording)
Profile      : 0x0015 (DVD-R/DL sequential recording)
Profile      : 0x0016 (DVD-R/DL layer jump recording)
Profile      : 0x0014 (DVD-RW sequential recording)
Profile      : 0x0013 (DVD-RW restricted overwrite)
Profile      : 0x001A (DVD+RW)
Profile      : 0x001B (DVD+R)
Profile      : 0x002B (DVD+R/DL)
Profile      : 0x0010 (DVD-ROM)
Profile      : 0x0009 (CD-R)
Profile      : 0x000A (CD-RW)
Profile      : 0x0008 (CD-ROM)
Profile      : 0x0002 (Removable disk)

```
Further it should report about the loaded medium and its state. Like
```

Media current: CD-R
Media product: 97m34s23f/79m59s73f , Mitsubishi Chemical Corporation
Media status : is blank
Media blocks : 0 readable , 359846 writable , 359846 overall
Media summary: 0 sessions, 0 data blocks, 0 data,  703m free

```
A reason for a burn program to refuse on an audio job would be that
"Media current:" does not say "CD-R" or "CD-RW", or that "Media status :"
says "is written , is closed".

(xorriso does not write audio CDs. cdrskin would do. But the GUI programs
will normally do too.)

Have a nice day :)

Thomas

---

### Post by Autodave on 2021-09-16
Can you play a DVD in the player now?  Are we sure that the drive didn't fail?

---

### Post by pascal111 on 2021-09-16
> **scdbackup said:**
> Hi,

can you show such a refusal message literally ?
(Only then it is possible to search it in the program's code.)

The writer should indeed be able to burn audio CDs. So the message might
come due to the medium type or status.

What do you get from this program run ?
```

xorriso -outdev /dev/sr0 -list_profiles out -toc

```



I didn't make yet audio CD's, I'm still testing the writing ability on Linux of my DVD writer.

```

pascal@pascal-Lenovo-ideapad-330-15AST:~$  xorriso -outdev /dev/sr0 -list_profiles out -toc

Command 'xorriso' not found, but can be installed with:

sudo apt install xorriso

pascal@pascal-Lenovo-ideapad-330-15AST:~$ sudo apt install xorriso
[sudo] password for pascal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libisoburn1
Suggested packages:
  xorriso-tcltk jigit cdck
The following NEW packages will be installed:
  libisoburn1 xorriso
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 655 kB of archives.
After this operation, 1,385 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://eg.archive.ubuntu.com/ubuntu focal/universe amd64 libisoburn1 amd64 1.5.2-1 [372 kB]
Get:2 http://eg.archive.ubuntu.com/ubuntu focal/universe amd64 xorriso amd64 1.5.2-1 [284 kB]
Fetched 655 kB in 5s (122 kB/s)   
Selecting previously unselected package libisoburn1:amd64.
(Reading database ... 193450 files and directories currently installed.)
Preparing to unpack .../libisoburn1_1.5.2-1_amd64.deb ...
Unpacking libisoburn1:amd64 (1.5.2-1) ...
Selecting previously unselected package xorriso.
Preparing to unpack .../xorriso_1.5.2-1_amd64.deb ...
Unpacking xorriso (1.5.2-1) ...
Setting up libisoburn1:amd64 (1.5.2-1) ...
Setting up xorriso (1.5.2-1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for install-info (6.7.0.dfsg.2-5) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
pascal@pascal-Lenovo-ideapad-330-15AST:~$ xorriso -outdev /dev/sr0 -list_profiles out -toc
xorriso 1.5.2 : RockRidge filesystem manipulator, libburnia project.

xorriso : NOTE : Disc status unsuitable for writing
Drive current: -outdev '/dev/sr0'
Media current: is not recognizable
Media status : is not present
Drive current: -outdev '/dev/sr0'
Drive type   : vendor 'HL-DT-ST' product 'DVDRAM GUE0N' revision 'T.02'
Profile      : 0x0012 (DVD-RAM)
Profile      : 0x002B (DVD+R/DL)
Profile      : 0x001B (DVD+R)
Profile      : 0x001A (DVD+RW)
Profile      : 0x0016 (DVD-R/DL layer jump recording)
Profile      : 0x0015 (DVD-R/DL sequential recording)
Profile      : 0x0014 (DVD-RW sequential recording)
Profile      : 0x0013 (DVD-RW restricted overwrite)
Profile      : 0x0011 (DVD-R sequential recording)
Profile      : 0x0010 (DVD-ROM)
Profile      : 0x000A (CD-RW)
Profile      : 0x0009 (CD-R)
Profile      : 0x0008 (CD-ROM)
Profile      : 0x0002 (Removable disk)
Drive current: -outdev '/dev/sr0'
Drive access : exclusive:unrestricted
Drive type   : vendor 'HL-DT-ST' product 'DVDRAM GUE0N' revision 'T.02'
Drive id     : 'KWCI5290234 '
Media current: is not recognizable
Media status : is not present


```

The message is changed when I clicked like a refresh button that make Xfburn recognize the blank CD:

[[img]https://i.postimg.cc/1nrhXHqL/Screenshot-from-2021-09-16-11-22-41.png[/img]](https://postimg.cc/1nrhXHqL)

---

### Post by pascal111 on 2021-09-16
> **Autodave said:**
> Can you play a DVD in the player now?  Are we sure that the drive didn't fail?

The writer reads well the normal data DVD's and CD's, and it's my first time in learning making audio discs, I don't have audio discs yet to test.

---

### Post by rsteinmetz70112 on 2021-09-16
Have you tried a different blank DVD, preferable a different brand? it looks like the drive is either not detecting or not recognizing the blank DVD.

---

### Post by Holger_Gehrke on 2021-09-16
Have you checked that you are a member of the group 'cdrom' ? If you look at the permissions for the CD drive ('ls -l /dev/sr0') you'll see it's owned by root and members of the group cdrom are allowed to read and write. Use 'id' to check and 'sudo usermod -a -G cdrom your_username' to add youself to the group if you aren't already a member.

Holger

---

### Post by scdbackup on 2021-09-17
Hi,

at least during above xorriso run, the permissions sufficed to communicate
with the burner drive. The drive states to be able to burn CD media, but it
also states that it sees no medium.

This is not a matter of particular burn programs, but rather a problem
between the drive and the inserted medium.

Have a nice day :)

Thomas

---

### Post by scdbackup on 2021-09-17
Hi,

the message "Cannot reserve track of ... bytes" in the Xfburn screenshot
probably stems from libburn. It gets emitted by libburn only if DVD+R,
DVD-R, or unformatted DVD-RW have been recognized by the drive.

None of these media is suitable for the kind of CD audio recording, which
the burn programs offer. DVD and BD media can only be used for data recording.
(There is a data formats for DVD audio. Wikipedia is a bit unclear about it,
but there are indications that it is similar to the Video DVD layout in a
UDF filesystem.)

libburn is supposed to also show an SCSI error message if a RESERVE TRACK
fails. I fail to find hints in the web where to to look for a detailed
error log of Xfburn.

Have a nice day :)

Thomas

---

### Post by Autodave on 2021-09-17
Are you trying to burn .wav files and make a CD playable in other CD players?  (I am a little confused here as to what exactly you are trying to do.)  I don't believe that you can burn a DVD as a "music" disk.

---

### Post by pascal111 on 2021-09-17
> **Autodave said:**
> Are you trying to burn .wav files and make a CD playable in other CD players?  (I am a little confused here as to what exactly you are trying to do.)  I don't believe that you can burn a DVD as a "music" disk.

We are not trying to make audio DVD, we are testing the writer on Ubuntu, it refuses to burn both DVD and CD discs.

---

### Post by pascal111 on 2021-09-17
> **rsteinmetz70112 said:**
> Have you tried a different blank DVD, preferable a different brand? it looks like the drive is either not detecting or not recognizing the blank DVD.

I'll try, but same brands worked under Windows, I tried that before.

---

### Post by pascal111 on 2021-09-17
> **Holger_Gehrke said:**
> Have you checked that you are a member of the group 'cdrom' ? If you look at the permissions for the CD drive ('ls -l /dev/sr0') you'll see it's owned by root and members of the group cdrom are allowed to read and write. Use 'id' to check and 'sudo usermod -a -G cdrom your_username' to add youself to the group if you aren't already a member.

Holger

I checked it:

```

pascal@pascal-Lenovo-ideapad-330-15AST:~$ groups
pascal root adm cdrom sudo dip plugdev lpadmin lxd sambashare

```

---

### Post by pascal111 on 2021-09-17
> **scdbackup said:**
> Hi,

the message "Cannot reserve track of ... bytes" in the Xfburn screenshot
probably stems from libburn. It gets emitted by libburn only if DVD+R,
DVD-R, or unformatted DVD-RW have been recognized by the drive.

None of these media is suitable for the kind of CD audio recording, which
the burn programs offer. DVD and BD media can only be used for data recording.
(There is a data formats for DVD audio. Wikipedia is a bit unclear about it,
but there are indications that it is similar to the Video DVD layout in a
UDF filesystem.)

libburn is supposed to also show an SCSI error message if a RESERVE TRACK
fails. I fail to find hints in the web where to to look for a detailed
error log of Xfburn.

Have a nice day :)

Thomas

I tried this command to see "libburn' if it is installed:

```

pascal@pascal-Lenovo-ideapad-330-15AST:~$ apt list --installed
Listing... Done
.
.
.
libburn4/focal,now 1.5.2-1 amd64 [installed,automatic]
.
.
.

```

---

### Post by scdbackup on 2021-09-17
Hi,

it is not a surprise that libburn is installed, as it is the only
burn backend which Xfburn and xorriso are willing to use. Brasero might
use it too. K3B would do indirectly if using cdrskin as burn backend.

There are some indications in the web that Xfburn shows libburn error
messages if it was started in a terminal window. See:
[https://askubuntu.com/questions/1131646/xfburn-fails-burn-run-failed](https://askubuntu.com/questions/1131646/xfburn-fails-burn-run-failed)

To get a report about the medium state you could run
```

xorriso -outdev /dev/sr0 -toc

```
when the intended medium is inserted. (Obviously it was not inserted or
not recognized with the previous xorriso run.)

If your goal is to compose ISO 9660 fileystems and to burn them on CD or
DVD, then xorriso would be the command line way to do so. (I'd need to
know which disk directories shall be copied and which directory names they
shall get. Then i could propose a burn run with checksums and checkreading.)

Have a nice day :)

Thomas

---

