---
title: "&quot;buffer i/o error on device&quot;"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by rhythmiccycle on 2009-05-10
I was having some problems with my computer. 
I removed all the partitions and installed windows.
I then installed ubuntu 9.04 from within windows.

when ubuntu is loading.
this shows up

Buffer I/O error of device sda1 Logical block (then some numbers)

and a bunch of other words too. they pass threw my screen, in cycles with the numbers changing, but the same I/O error message. it goes on for about 10 minutes, then ubuntu loads.

it seems to be working well, I'm using it now. 
but there is no sound(i checked to volume).
and  when I try to open my second hard drive (that works in windows)
it says

unable to mount device.

are all these problems related or are they 3 separate problems?
what should I do to get my sound and second hard drive to work?

---

### Post by orange-wedge on 2009-05-10
well the sound is most likely a separate issue from your hard drive problems.  can you open up a terminal and run the following:
[HTML]dmesg > dmesg.txt[/HTML]
That should create a file called dmesg.txt... please reply back with that file as an attachement.

---

### Post by rhythmiccycle on 2009-05-11
I did it but the file was 122.3 KB

So I attached the first and last 19.4 KB

or is there a way for me to attach a 122.3 kb file?

---

### Post by orange-wedge on 2009-05-11
yeah not sure why they won't let you post a larger file... sort of new to the ubuntu forums.  you could try zipping the file next time:
[HTML]gzip dmesg.txt[/HTML]

yeah i'm seeing all the hard drive errors, not too firm on a root cause...  and it seems to be looping on the same error.  this definitely what is causing the extended boot time:
[HTML]
[  519.038185] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[  519.038218] sd 0:0:0:0: [sda] Write Protect is off
[  519.038224] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  519.038277] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  522.218534] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  522.218540] ata1.00: irq_stat 0x40000008
[  522.218548] ata1.00: cmd 60/08:00:bf:00:00/00:00:00:00:00/40 tag 0 ncq 4096 in
[  522.218549]          res 51/40:08:bf:00:00/00:00:00:00:00/00 Emask 0x409 (media error) <F>
[  522.218553] ata1.00: status: { DRDY ERR }
[  522.218556] ata1.00: error: { UNC }
[  522.221015] ata1.00: configured for UDMA/133
[  522.221036] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  522.221043] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  522.221052] Descriptor sense data with sense descriptors (in hex):
[  522.221056]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  522.221075]         00 00 00 bf 
[  522.221083] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  522.221093] end_request: I/O error, dev sda, sector 191
[  522.221100] Buffer I/O error on device sda1, logical block 128
[  522.221106] Buffer I/O error on device sda1, logical block 129
[  522.221109] Buffer I/O error on device sda1, logical block 130
[  522.221113] Buffer I/O error on device sda1, logical block 131
[  522.221116] Buffer I/O error on device sda1, logical block 132
[  522.221119] Buffer I/O error on device sda1, logical block 133
[  522.221123] Buffer I/O error on device sda1, logical block 134
[  522.221126] Buffer I/O error on device sda1, logical block 135
[  522.221144] ata1: EH complete
[/HTML]

for the audio problem, here's the output when its being loaded:
[HTML][  212.950615] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  212.950690] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  212.981677] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[  212.982131] hda_codec: Cannot set up configuration from BIOS.  Using 3-stack mode...
[/HTML]
if you do have an ALC880, i did a quick google search and it seems to be an older audio chip so ubuntu shouldnt have any trouble.  i've had some issues with the pulseaudio server in ubuntu with these HDA Intel chips though so you could try killing it:

[HTML]killall pulseaudio[/HTML]
 
and test the results. you may check this out also:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

