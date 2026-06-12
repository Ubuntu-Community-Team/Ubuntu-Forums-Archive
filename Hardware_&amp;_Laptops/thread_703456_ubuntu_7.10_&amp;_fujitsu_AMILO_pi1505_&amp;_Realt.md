---
title: "ubuntu 7.10 &amp; fujitsu AMILO pi1505 &amp; Realtek ALC861"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by black-flag on 2008-02-21
hello,
my microphone don't working under ubuntu 7.10
my conf 
Fujitsu siemens AMILO pi 1505
> 
root@b-f:~# uname -a
Linux b-f 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

> 
superuser@b-f:~$ sudo lspci -vv
....
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10c7
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at f0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0
....


> 
superuser@b-f:~$ tail -2 /proc/asound/oss/sndstat 
Mixers:
0: Realtek ALC861
superuser@b-f:~$

> 
superuser@b-f:~$ dmesg |grep hda
[   15.692000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
superuser@b-f:~$


> 
superuser@b-f:~$ alsamixer 

alsamixer: function snd_mixer_load failed: No such file or directory
superuser@b-f:~$


thank you

---

### Post by Yellow Pasque on 2008-02-21
Try running these scripts to upgrade to the latest version of ALSA. Then, go into alsamixer and make sure everything's unmuted.
[http://ubuntuforums.org/showpost.php?p=4360698&postcount=6](http://ubuntuforums.org/showpost.php?p=4360698&postcount=6)

---

### Post by black-flag on 2008-02-21
hello again
thank you for your answer :)
ok :(
i excuted these scripts (alsa_1.sh and after rebooting alsa_2.sh ) to upgrade to the last version of ALSA

> 
root@b-f:/tmp# alsamixer 

alsamixer: function snd_mixer_load failed: No such file or directory
root@b-f:/tmp# 


> 
root@b-f:/tmp# dmesg |grep hda
[   15.704000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
root@b-f:/tmp# 


and the mic is unmuted.

---

### Post by black-flag on 2008-02-21
so any solution for me :( ???

---

### Post by Yellow Pasque on 2008-02-21
Ah, it's saying unknown model so try the suggestion of this thread: [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
i.e. open up /etc/modprobe.d/alsa-base and add or change this line options snd-hda-intel model=3stack

Other model= you can try 
3stack 3-jack
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack with SPDIF I/O
3stack-660 3-jack (for ALC660)
uniwill-m31 Uniwill M31 laptop
toshiba Toshiba laptop support
asus Asus laptop support
asus-laptop ASUS F2/F3 laptops
auto auto-config reading BIOS (default)

---

### Post by black-flag on 2008-02-21
> 
superuser@b-f:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Motorola Si3054
Codec: Realtek ALC861
superuser@b-f:~$ 


ok i tested all models of ALC861/660 and ALC861VD/660VD one after one with rebooting :( but always my mic don't working   

> 
options snd-hda-intel model=3stack
options snd-hda-intel model=3stack-dig
options snd-hda-intel model=6stack-dig
options snd-hda-intel model=uniwill-m31
options snd-hda-intel model=lenovo
options snd-hda-intel model=dallas
options snd-hda-intel model=hp
options snd-hda-intel model=uniwill-m31
options snd-hda-intel model=asus
options snd-hda-intel model=asus-laptop
options snd-hda-intel model=auto
options snd-hda-intel model=3stack-660


---

### Post by black-flag on 2008-02-21
does mean i can't use my microphone under ubuntu 7.10 :confused:

---

### Post by black-flag on 2008-02-21
i waiting your help !!

---

### Post by black-flag on 2008-02-22
please i need your help, say to me any things >  "back to windows; don't use ubuntu,  or wait for solution "so don't let me in between please

---

