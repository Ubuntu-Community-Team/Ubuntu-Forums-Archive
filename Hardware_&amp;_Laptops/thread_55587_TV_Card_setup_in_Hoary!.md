---
title: "TV Card setup in Hoary!"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by c-m on 2005-08-09
I've recently installed ubuntu one of the main reasons for doing this was to use mythtv, however i am at a complete loss on how to setup my tv card to work with ubuntu.

My card is a pci Hauppage WinTV Go, can someone please direct me on how to set up this card up correctly in ubuntu?

Thanks.

---

### Post by varunus on 2005-08-09
Can you post the output of lspci and lsmod in a terminal?  There are apparently two models of WinTV Go's, one which requires more tweaking.

---

### Post by c-m on 2005-08-09
[QUOTE=varunus]Can you post the output of lspci and lsmod in a terminal?  There are apparently two models of WinTV Go's, one which requires more tweaking.[/QUOTE]
 output from lspci: (i figured this is the bit you were looking for?)

> 
0000:01:09.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
0000:01:09.1 Multimedia controller: Conexant: Unknown device 8811 (rev 05)
 

output from lsmod:
> 
carl@ubuntu:~$ sudo lsmod
Module                  Size  Used by
proc_intf               4100  0
cpufreq_powersave       1920  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
freq_table              4100  0
video                  16260  0
battery                10244  0
container               4608  0
button                  6800  0
pcc_acpi               11264  0
sony_acpi               6280  0
ac                      4996  0
ipv6                  229504  18
af_packet              20744  2
ohci1394               31876  0
r8169                  17928  0
tuner                  20388  0
cx8800                 29196  0
cx88xx                 46868  1 cx8800
i2c_algo_bit            9224  1 cx88xx
video_buf              20484  2 cx8800,cx88xx
v4l1_compat            13572  1 cx8800
v4l2_common             5888  1 cx8800
btcx_risc               4744  2 cx8800,cx88xx
videodev                9728  2 cx8800,cx88xx
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
usbhid                 29376  0
ehci_hcd               29444  0
ohci_hcd               19848  0
usbcore               107384  4 usbhid,ehci_hcd,ohci_hcd
i2c_nforce2             6400  0
i2c_core               21264  4 tuner,cx88xx,i2c_algo_bit,i2c_nforce2
nvidia_agp              7452  1
agpgart                31784  1 nvidia_agp
analog                 10784  0
gameport                4608  1 analog
pcspkr                  3816  0
rtc                    12216  0
nls_cp437               5888  1
ntfs                   97136  1
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
sr_mod                 16036  0
evdev                   9088  0
sbp2                   22408  0
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
reiserfs              225616  3
ext3                  120968  0
jbd                    54168  1 ext3
ide_generic             1664  0
ide_disk               18176  6
amd74xx                13340  1
ide_core              118988  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26164  784
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  71
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  1
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
carl@ubuntu:~$


Hope that helps.

---

### Post by c-m on 2005-08-10
i have found this ([http://linux.bytesex.org/v4l2/cx88.html](http://linux.bytesex.org/v4l2/cx88.html)) is that any use to me?   Ideally i need somesort of guide as to how to set it up.

---

### Post by varunus on 2005-08-10
Well, according to your lsmod output, your card was autodetected.  The drivers (various v4l2 ones, cx8800, cx88xx, etc) are already loaded.  So it seems you're lucky, you had out of the box support.  What program are you having problems configuring the card in?  Any program that supports Video4Linux 2 should work now...

---

### Post by c-m on 2005-08-11
[QUOTE=varunus]Well, according to your lsmod output, your card was autodetected.  The drivers (various v4l2 ones, cx8800, cx88xx, etc) are already loaded.  So it seems you're lucky, you had out of the box support.  What program are you having problems configuring the card in?  Any program that supports Video4Linux 2 should work now...[/QUOTE]
 well i'm trying to setup Mythtv, which is all installed, i'm just having prpblems seting up the card in it.

Do you know of any easy to configure tv software i can test the card in?

---

### Post by varunus on 2005-08-11
Well, I can point you to the following mythtv guide at Anandtech:
[http://www.anandtech.com/linux/showdoc.aspx?i=2190](http://www.anandtech.com/linux/showdoc.aspx?i=2190)
They use a WINTV PVR250 in this howto, and a WINTV GO in their follow up.  But they talk about how they made sure it was working using xawtv, I think...They also talk about configuring mythtv.  In reality, you can use any configure mythtv guide now, your card seems to have been detected.  Just follow the steps to get mythtv to see your card.  Its been a while since I've read it, maybe it will have some information for you.

Can you post the the output of "ls /dev/v*" in a terminal?  Make sure you have a /dev/videoX device(s).  If you do, your card is working.  Try a simpler tv watching application like xawtv first (check synaptic, I believe its there).

---

### Post by c-m on 2005-08-11
[QUOTE=varunus]Well, I can point you to the following mythtv guide at Anandtech:
[http://www.anandtech.com/linux/showdoc.aspx?i=2190](http://www.anandtech.com/linux/showdoc.aspx?i=2190)
They use a WINTV PVR250 in this howto, and a WINTV GO in their follow up.  But they talk about how they made sure it was working using xawtv, I think...They also talk about configuring mythtv.  In reality, you can use any configure mythtv guide now, your card seems to have been detected.  Just follow the steps to get mythtv to see your card.  Its been a while since I've read it, maybe it will have some information for you.

Can you post the the output of "ls /dev/v*" in a terminal?  Make sure you have a /dev/videoX device(s).  If you do, your card is working.  Try a simpler tv watching application like xawtv first (check synaptic, I believe its there).[/QUOTE]
 heres the output:

> 
root@ubuntu:/home/carl # ls /dev/v*
/dev/vbi0  /dev/vcs2  /dev/vcs5  /dev/vcsa   /dev/vcsa3  /dev/vcsa6
/dev/vcs   /dev/vcs3  /dev/vcs6  /dev/vcsa1  /dev/vcsa4  /dev/vcsa7
/dev/vcs1  /dev/vcs4  /dev/vcs7  /dev/vcsa2  /dev/vcsa5  /dev/video0

/dev/video1394:
0
root@ubuntu:/home/carl #



---

### Post by c-m on 2005-08-11
i've managed to get XAWTV setup. Only found a couple of channels so far, but that not important.

what is more important is i don't have any sound. My card uses a pass through cable that connects to the line in on my sound card. But the only sound i get in XAWTV is a load of static, as if the channel isn't really tuned in.

---

### Post by varunus on 2005-08-11
Well, it means the card is working at least.  I think you should start googling for sound static or something; it seems your card is set up fine, at least, so Ubuntu is doing its job.   :) 

Sorry I can't be more help to you.

---

### Post by se7en2wo on 2005-08-26
how come I can not see xawtv in synaptic package manager? How can I install it if I can not see it there?

Thanks.

---

### Post by s_p_a_r_k_y on 2005-08-26
do you have the IVTV drivers configured and setup?

---

### Post by se7en2wo on 2005-08-26
[QUOTE=se7en2wo]how come I can not see xawtv in synaptic package manager? How can I install it if I can not see it there?

Thanks.[/QUOTE]

Im not sure what IVTV means but I think my Pinnacle TV tuner was auto-detected.

+ + + + +

0000:02:0c.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:02:0c.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

+ + + + +

se7en2wo@se7en2wo:~$ dmesg | grep bttv*
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
bttv0: Bt878 (rev 17) at 0000:02:0c.0, irq: 20, latency: 32, mmio: 0xef000000
bttv0: detected: Pinnacle PCTV [bswap] [card=39], PCI subsystem ID is bd11:1200
bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00ff0fff [init]
bttv0: i2c: checking for MSP34xx @ 0x80... not found
bttv0: miro: id=3 tuner=2 radio=no stereo=no
bttv0: using tuner=2
bttv0: i2c: checking for MSP34xx @ 0x80... not found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
bttv0: i2c: checking for TDA9887 @ 0x86... not found
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: PLL: 28636363 => 35468950 .. ok

---

### Post by s_p_a_r_k_y on 2005-08-26
IVTV are the drivers for Hauppauge based winPVR cards. [http://ivtv.sourceforge.net](http://ivtv.sourceforge.net) for more info.

---

### Post by madjo on 2005-08-27
I too seem to have a problem getting my tv card running.
Ubuntu does seem to detect it somehow, but not fully.
output of lspci:
```
0000:00:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```

output of dmesg:
```
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
bttv0: Bt878 (rev 17) at 000:00:0d.0, irq: 17, latency: 32, mmio: 8xcdcfe000
bttv0: using: *** UNKNOWN/GENERIC *** [card=0, autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00449fff [init]
bttv: readee error
bttv0: using tuner=-1
bttv0: i2c: checking for MSP34xx @ 0x80... not found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... <6>usb 2-1.1: new full speed USB device using ohci_hcd and address 3
bttv0: i2c: checking for TDA9887 @ 0x86... not found
bttv0: registered device video0
bttv0: registered device vbi0
```

And checking the Documentation/Video4Linux/CARDLIST.bttv I gather that my card (a Lifetec 9415) is actually card number 54

So now is my question, how do I change the setting of the card-type and of the tunertype?

This is all out of the box, I did not tinker with the kernel, and I dread the day that I have to... :)

oh btw, lsmod gave me this output (I snipped it, it was far longer than this):
```
Module                  Size  Used by
snd_bt87x              12612  0
bttv                  142928  0
af_packet              20744  2
video_buf              20484  1 bttv
firmware_class          9728  1 bttv
i2c_algo_bit            9224  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4744  1 bttv
i2c_core               21264  2 bttv,i2c_algo_bit
videodev                9728  1 bttv
snd_pcm                84872  3 snd_bt87x,snd_cmipci,snd_pcm_oss
snd_page_alloc          9604  2 snd_bt87x,snd_pcm
snd                    50276  11 snd_bt87x,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
```

I hope someone can point me in the right direction.

oh and btw, I tried to use the search on this forum, but all it gave me, was a message about something being wrong with the database of the forum...

---

### Post by madjo on 2005-08-28
*bump* apparently due to the database problems, my reply wasn't fully acknowledged by the system (I didn't show up as the person of the last reply)

---

### Post by stepper on 2005-08-28
[QUOTE=madjo]
And checking the Documentation/Video4Linux/CARDLIST.bttv I gather that my card (a Lifetec 9415) is actually card number 54

So now is my question, how do I change the setting of the card-type and of the tunertype?

This is all out of the box, I did not tinker with the kernel, and I dread the day that I have to... :)
[/QUOTE] 
I did this instructions to help someone with another card, so u will change your card number to 54 and your type accordingly!
[http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2](http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2)

---

### Post by madjo on 2005-08-28
[QUOTE=stepper]I did this instructions to help someone with another card, so u will change your card number to 54 and your type accordingly!
[http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2](http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2)[/QUOTE]
 thank you I will try this.

---

### Post by madjo on 2005-08-31
[QUOTE=stepper]I did this instructions to help someone with another card, so u will change your card number to 54 and your type accordingly!
[http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2](http://www.ubuntuforums.org/showpost.php?p=162498&postcount=2)[/QUOTE]
 it works flawless here... thank you so much :)

---

