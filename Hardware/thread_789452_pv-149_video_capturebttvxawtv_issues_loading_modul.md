---
title: "pv-149 video capture/bttv/xawtv issues loading modules"
date: 2008-05-10
forum: Hardware
---

### Post by Xteven on 2008-05-10
Hello,

I just purchased the following **PV-149 8-port Video Capture Card** from [http://store.bluecherry.net/8_port_video_capture_card_linux_bt878_p/pv-149_8port.htm](http://store.bluecherry.net/8_port_video_capture_card_linux_bt878_p/pv-149_8port.htm)

This is a BTTV chipset based video capture card: [http://tldp.visiolab.de/HOWTO/html_single/BTTV/#PERMISSIONS](http://tldp.visiolab.de/HOWTO/html_single/BTTV/#PERMISSIONS)

I am trying to use xawtv ([http://linux.bytesex.org/xawtv/](http://linux.bytesex.org/xawtv/)) to communicate with this card to actually see some video! Here is my current problem:

```

account@server:/$ xawtv -hwscan
xdpyinfo:  unable to open display "".
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-16-generic)
Error: Can't open display: 

```

As you can see, when I try to scan for video capture hardware, xawtv comes up dry with some errors. I tried to Google for days but can't dig up anything useful (at least useful to me...)

The newest Linux Kernel is apparently packaged with the appropriate modules to automagically detect and install this card as well as other BTTV based cards.

After installing the card into my server the following is the result:

```

account@server:/$ uname -r
2.6.24-16-generic

account@server:/$ lspci | grep Bt878
02:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

account@server:/$ dmesg | grep bttv
[   43.374322] bttv: driver version 0.9.17 loaded
[   43.374329] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   43.374426] bttv: Bt8xx card found (0).
[   43.374481] bttv0: Bt878 (rev 17) at 0000:02:08.0, irq: 16, latency: 32, mmio: 0xde000000
[   43.380143] bttv0: detected: Provideo PV150A-1 [card=98], PCI subsystem ID is aa00:1460
[   43.380150] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,insmod option]
[   43.380212] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   43.412375] bttv0: tuner absent
[   43.417670] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   43.418296] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   43.418915] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   43.421516] bttv0: registered device video0
[   43.421570] bttv0: registered device vbi0
[   43.421625] bttv: Bt8xx card found (1).
[   43.421677] bttv1: Bt878 (rev 17) at 0000:02:09.0, irq: 20, latency: 32, mmio: 0xde002000
[   43.421701] bttv1: detected: Provideo PV150A-2 [card=98], PCI subsystem ID is aa01:1461
[   43.421705] bttv1: using:  *** UNKNOWN/GENERIC ***  [card=0,insmod option]
[   43.421736] bttv1: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   43.453901] bttv1: tuner absent
[   43.469397] bttv1: i2c: checking for MSP34xx @ 0x80... not found
[   43.470023] bttv1: i2c: checking for TDA9875 @ 0xb0... not found
[   43.471076] bttv1: i2c: checking for TDA7432 @ 0x8a... not found
[   43.473475] bttv1: registered device video1
[   43.473539] bttv1: registered device vbi1
[   43.473595] bttv: Bt8xx card found (2).
[   43.473648] bttv2: Bt878 (rev 17) at 0000:02:0a.0, irq: 18, latency: 32, mmio: 0xde004000
[   43.473674] bttv2: detected: Provideo PV150A-3 [card=98], PCI subsystem ID is aa02:1462
[   43.473678] bttv2: using:  *** UNKNOWN/GENERIC ***  [card=0,insmod option]
[   43.473714] bttv2: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   43.505901] bttv2: tuner absent
[   43.521292] bttv2: i2c: checking for MSP34xx @ 0x80... not found
[   43.521917] bttv2: i2c: checking for TDA9875 @ 0xb0... not found
[   43.522536] bttv2: i2c: checking for TDA7432 @ 0x8a... not found
[   43.523258] bttv2: registered device video2
[   43.523333] bttv2: registered device vbi2
[   43.523387] bttv: Bt8xx card found (3).
[   43.523441] bttv3: Bt878 (rev 17) at 0000:02:0b.0, irq: 17, latency: 32, mmio: 0xde006000
[   43.523919] bttv3: detected: Provideo PV150A-4 [card=98], PCI subsystem ID is aa03:1463
[   43.523925] bttv3: using:  *** UNKNOWN/GENERIC ***  [card=0,insmod option]
[   43.523962] bttv3: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   43.556175] bttv3: tuner absent
[   43.572616] bttv3: i2c: checking for MSP34xx @ 0x80... not found
[   43.573260] bttv3: i2c: checking for TDA9875 @ 0xb0... not found
[   43.573879] bttv3: i2c: checking for TDA7432 @ 0x8a... not found
[   43.574603] bttv3: registered device video3
[   43.574660] bttv3: registered device vbi3

```

If you notice the result of the dmesg | grep bttv, you will see that each port is using: ** UNKNOWN/GENERIC ***. Now I am not exactly sure, but I don't think that's good ;-).

If I do a search for available bttv modules, you can see that it is there.

```

account@server:/$ ls -R /lib/modules/`uname -r`/kernel | grep bttv
bttv.ko

account@server:/$ find /lib/modules -name bttv*
/lib/modules/2.6.24-16-generic/kernel/drivers/media/video/bt8xx/bttv.ko

```

Additionally each of the ports have been mapped to a respective /dev/video

```

account@server:/$ ls -al /dev | grep video*
crw-rw----  1 root   video    10, 175 2008-05-10 12:21 agpgart
crw-rw----  1 root   video   195,   0 2008-05-10 12:21 nvidia0
crw-rw----  1 root   video   195, 255 2008-05-10 12:21 nvidiactl
crw-rw----  1 root   video    81, 224 2008-05-10 12:21 vbi0
crw-rw----  1 root   video    81, 225 2008-05-10 12:21 vbi1
crw-rw----  1 root   video    81, 226 2008-05-10 12:21 vbi2
crw-rw----  1 root   video    81, 227 2008-05-10 12:21 vbi3
crw-rw----  1 root   video    81,   0 2008-05-10 12:21 video0
crw-rw----  1 root   video    81,   1 2008-05-10 12:21 video1
crw-rw----  1 root   video    81,   2 2008-05-10 12:21 video2
crw-rw----  1 root   video    81,   3 2008-05-10 12:21 video3

```

So from what you can see... I think my video capture card PV-149 is loaded correctly however xawtv does not seem to detect it. I am afraid it might have to do with the "using:  *** UNKNOWN/GENERIC ***"

Any ideas?

Thanks.
Steven

---

### Post by Xteven on 2008-05-12
Okay, so I was able to solve the UNKNOWN/GENERIC problem by creating a new file in my /etc/modprobe.d/ directory like so:

```

account@server:/$ sudo echo "options bttv card=98,98,98,98" > /etc/modprobe.d/pv149

```

Then I restarted my computer and viola, it was no long UNKNOWN/GENERIC! However, I am still having this problem with xawtv and have no idea why. Where is this display setting and why is it empty "" !!!

```

account@server:/$ xawtv -hwscan
xdpyinfo:  unable to open display "".
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-16-generic)
Error: Can't open display:

```

---

### Post by groesbeck on 2008-05-15
Hey there.  I have a PV-143NA card that I also bought from bluecherry.  Mine worked great in Redhat9, Feisty and Gutsy.  When I went to Hardy, everything quit working.  I actually have two different capture cards and they both failed.  I eventually went back to Gutsy.

I have never needed to make a modeprobe.d file.  For me, the bttv and bt878 drivers seemed to autodetect my cards but xawtv would just hang in Hardy.  Never found out what was wrong.  

xawtv never gave me an error.  would just hang.  xawtv -hwscan would also hang.

I just noticed you are running 2.6.24-16.  That was the version that wouldn't work for me.

I'd suggest booting a gutsy livecd and seeing what happens.  If it doesn't autodetect your card type, try unloading them with modprobe -r bttv and then reload with modprobe -v bttv card=whatever (I think that syntax is close to being correct) and then running xawtv.

---

### Post by quinella on 2008-07-30
Was also having this kind of error:

# xawtv -hwscan
xdpyinfo:  unable to open display "".
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-19-generic)
Error: Can't open display: 

Then I realized I was login as root. root doesn't have the proper
env variables. 

Other than root, I could:

sysadmin:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-19-generic)
looking for available devices
port 158-189
    type : Xvideo, image scaler
    name : NV05 Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture tuner

---

