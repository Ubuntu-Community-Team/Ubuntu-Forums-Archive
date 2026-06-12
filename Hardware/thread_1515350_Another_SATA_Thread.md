---
title: "Another SATA Thread"
date: 2010-06-22
forum: Hardware
---

### Post by whoopa on 2010-06-22
Hi Forum!

Ok, so I've got a little problem. I 'assembled' a new computer yesterday and first thoughts were to install lucid on it. I have it on both my old desktop & laptop (installed from usb).
The new machine wouldn't let me boot from usb (mobo didn't want me to/let me) SO I made a cd and booted/installed from that.

Everything's great, ran good and after nvidia drivers the GPU came alive!
So I'm testing some of the basics out and I get the one and only (so far) problem with 10.04 .
I'm running both a HDD && a DVD RW on SATA (via mobo).

The HDD is great.
The DVD RW mounts Media, including CD's and DVD's
BUT when I play a CD (in VLC or Rhythmbox), I get an consistent pause every 2 or so seconds in playback. I tried playing a DVD and an got I/O error (in Totem).

(Note: I installed the OS with the DVD drive, so it works)

So I was thinking DMA, but apparently this doesn't/shouldn't apply to SATA.
hdparm doesn't allow the changing of this value.

Currently both SATA devices are on the 'master' channel (3 & 2 respectively).
BIOS doesn't allow heaps of changes:
Gigabyte MA78LMT-S2 (revision 1.3, BIOS F 8                  {possible upgrade to F9}
Enable onboard SATA controller <YES>
Options for SATA [native IDE, RAID, AHCI] <Native IDE>

For those still reading, I am using a SAMSUNG SH-S233C, labeled under TSST (brand).
This is running firmware SB02                   {upgrade unknown}

I have already researched this thoroughly.
Most problems with other SATA devices are for HDD's, are BIOS-related (incorrectly set-up) or that the Optical drive does not even mount a disc.

One solution was to use libata boot command line arguments (not sure if I've tried this correctly, not used to GRUB2).
Another was to edit the modules (/etc/modules), and add the lines;

pata_atiixp
blacklist ata_generic

OR

amd74xx

AND then running update-initramfs -u

Another was to edit the fstab (/etc/fstab).

Ohh, and I've also played around heaps with codecs and etc (hoping) they may be strangely interconnected.

In conclusion, The drive kinda works. But it's not at a functional level of operation.
Any left-field thoughts, or if a voice of experience could speak, it would be greatly appreciated!

Thanks.

---

### Post by whoopa on 2010-06-22
AND here's some excess information for the curious:

ls -l /media

```
total 8
drwxr-xr-x 2 root root 4096 2010-06-22 20:36 cdrom0
lrwxrwxrwx 1 root root    7 2010-06-22 02:32 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-06-22 02:32 floppy0
```
ls -l /dev/cd* /dev/dvd* /dev/scd*

```
lrwxrwxrwx 1 root root 3 2010-06-22 20:40 /dev/cdrom3 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-22 20:40 /dev/cdrw3 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-22 20:40 /dev/dvd3 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-22 20:40 /dev/dvdrw3 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-22 20:40 /dev/scd0 -> sr0

```dmesg | grep -i dvd

```
[    1.790928] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB02, max UDMA/100
[    1.811693] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB02 PQ: 0 ANSI: 5
[    1.812484] sr0: scsi3-mmc drive: 8x/40x writer dvd-ram cd/rw xa/form2 cdda tray

```sudo lshw -C disk -short

```
H/W path         Device       Class       Description
=====================================================
/0/100/11/0      /dev/cdrom3  disk        CDDVDW SH-S223C
/0/100/11/1      /dev/sda     disk        250GB ST3250318AS
```
wodim -checkdrive

```
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDDVDW SH-S223C '
Revision       : 'SB02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

```sudo hdparm -Ii /dev/sr0

```
/dev/sr0:

 Model=TSSTcorp, FwRev=SB02, SerialNo=Q
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  *mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no
 Drive conforms to: ATA/ATAPI-4 T13 1153D revision 17:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode


ATAPI CD-ROM, with removable media
    Model Number:       TSSTcorp CDDVDW SH-S223C                
    Serial Number:      Q   w         U     
    Firmware Revision:  SB02    
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Likely used CD-ROM ATAPI-1
Configuration:
    DRQ response: 50us.
    Packet size: 12 bytes
    cache/buffer size  = unknown
Capabilities:
    LBA, IORDY(can be disabled)
    DMA: *mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 (?)
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    PACKET command feature set
       *    DEVICE_RESET command
       *    NOP cmd
            Removable Media Status Notification feature set
       *    Gen1 signaling speed (1.5Gb/s)
       *    Phy event counters
       *    Software settings preservation
```lshal | egrep cdrom  scsi.type = 'cdrom'  (string)

 ```
 info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdrdl = true  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 7056  (0x1b90)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 8467  (0x2113)  (int)
  storage.cdrom.write_speeds = {'8467', '7056', '5645', '4234', '2822', '1411'} (string list)
  storage.drive_type = 'cdrom'  (string)
```

---

### Post by whoopa on 2010-06-22
My mistake, this only concerns CD playback (I/O).

I've tried two DVD's since posting, and they have worked splendidly!
(Using both Totem & VLC).

I took the liberty of downloading K3b.
I was able to extract (or rip) a song off the cd I was originally testing.
EDIT: This took 2 minutes and 20 seconds for a **2** minute song (@ Ogg-Vorbis Quality setting 6 (~192)). **This is about 1x speed. Not good.**

<during ripping the progress bar jumped by 15-20%, instead of smoothly incrementing sequentially>

Although it did take a fair amount of time, the ripped music file then played flawlessly.

EDIT: Also tried a second CD, same problem with playback

I have a feeling this can now be narrowed down to how the "CD" portion of the drive is handled, since the "DVD" portion works and I've tried multiple programs to read CD's.

Still really keen to hear back from anyone...

---

### Post by whoopa on 2010-06-22
Well, I've updated my BIOS (version F9).
And I've updated Ubuntu (No new packages in Update Manager).

I've also discovered that mounting a disc (CD) and using Ubuntu's PopUp Helper to choose an application, using VLC with 300ms (default) cache works alright.
The first track plays fine, but skipping takes a while (300ms+ obviously).

BUT, as soon as this is closed, and say Rhythmbox opened, it seems choppy still. The Built-in app. handler must read ahead and cache a fair bit or something. Returning to VLC I cannot reproduce the same results as the initial mount, with the time-stamp thing in the corner always changing to "Buffer: " and some associated percentage.

**Please Note: **I am running the 64 bit version of Ubuntu.
I don't think i've mentioned that yet.

Also - another comparison to make between my HDD && DVD.
In Disk Utility, for the HDD I can see the serial number and world-wide name.
In Disk Utility, for the DVD I cannot see either of these two values.

Anyone's thoughts? I'm more than happy to test/provide some info.

---

### Post by whoopa on 2010-06-23
Just tried swapping SATA cables.
No difference whatsoever.

I may have to install another OS (which I don't want to do) to really see if it's a hardware issue.

I'm quite confident it's a software based issue though.

Is there a way to update Optical drive DRIVERS?

EDIT: Also - is it AT ALL possible that running **32 bit** would be better?
I only have 4GB of RAM and will probably never exceed that in this machine.
Although I was thinking that the more people who run 64 the better it gets, I really need this functionality...

---

### Post by whoopa on 2010-06-23
So here's another of my own updates (since no-one else has responded).

I've copied data from a burnt cd (2.4 - 4.0 MB/sec) which I consider good.
I've burnt a cd (the 32bit Ubuntu 10.04) which passed self-disk check and installed on another partition wonderfully.
I've even run the 32bit version, but the problem still remains.

**NOW** this is either a hardware issue which is only limited to reading CD's slowly.

**OR** since dvd's, cd reading & writing (or burning) work, I'm thinking the problem can now be pinpointed to Audio CD's in general, and the application's/codec/modules that handle them.

I'm focused on the latter.

So far I'm using VLC & Rhythmbox.
I know there is a multimedia guide on these forums. I will try that thoroughly within the next 3 or so hours. Otherwise could SOMEONE please let me know if they have encountered a similar problem (Hell, test your CD playback and just let me know if you share my problem).

Again, willing to try abc right through to xyz.
If I cannot get this to work, I may have to settle for windows (machine isn't for me).

---

### Post by dino99 on 2010-06-23
you might select ahci into bios

and maybe its time to look at errors:
- .xsession-errors (unhide it: ctrl+h)
- system admin logviewer

you might find usefull errors to go ahead

---

### Post by whoopa on 2010-06-23
HELLO!

so, I had tried AHCI mode before, but not since BIOS update.
Sadly, no difference.

Couldn't get to .xsession-errors via the System Log Viewer.
Did a quick search with hidden files checked.

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Window manager warning: Failed to read saved session file /home/avcomputer/.config/metacity/sessions/10b250ec82f9452c62127728503619024300000015200043.ms: Failed to open file '/home/avcomputer/.config/metacity/sessions/10b250ec82f9452c62127728503619024300000015200043.ms': No such file or directory

(polkit-gnome-authentication-agent-1:1579): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1579): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-panel:1580): GConf-WARNING **: Directory `/apps/panel/toplevels/bottom_panel_screen1/screen' was not being monitored by GConfClient 0x2462e40

(gnome-panel:1580): GConf-WARNING **: Directory `/apps/panel/toplevels/top_panel_screen1/screen' was not being monitored by GConfClient 0x2462e40
Initializing nautilus-gdu extension
Unable to find a synaptics device.
** (rhythmbox:1681): DEBUG: Loading the real store page
** (rhythmbox:1681): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token
** (rhythmbox:1681): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=496&partner=983
Sense key: 0x70 0x00 0x03 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x11 0x00 0x00 0x00 0x00 0x00 0x00 
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x3000003 (messages -); these messages lack timestamps and therefore suck.
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x3000003 (messages -); these messages lack timestamps and therefore suck.
```More explicitly, this is the error I believe I'm getting (displayed from System Log Viewer -> messages):

```
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.774624] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.774636] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.774646] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.774659] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.774684] __ratelimit: 9 callbacks suppressed
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.775750] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.775758] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.775766] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.775776] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.777650] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.777661] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.777669] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.777680] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00

...Repeating until...

Jun 23 19:25:07 avcomputer-desktop kernel: [   94.993685] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.993696] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.993704] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Jun 23 19:25:07 avcomputer-desktop kernel: [   94.993714] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Jun 23 19:25:24 avcomputer-desktop pulseaudio[1578]: ratelimit.c: 8 events suppressed
```That very last line is when I stopped the track playing ( I played the song for 17 seconds )

Judging by that last line, problem could be with pulseaudio (so it effects more than one application).

I have a firm grasp of ubuntu and terminal, in terms of navigating and installing / basic commands. Debugging other peoples programs, not so much.

EDIT: Had a little play with sg_requests (seeing Sense Key pop up everywhere)

```
sg_requests -vts /dev/sr0
    Request Sense cmd: 03 00 00 00 fc 00 
Decode parameter data as sense data:
 Fixed format, current;  Sense key: No Sense
 Additional sense: No additional sense information
time to perform commands was 0.001308 secs; 764.53 operations/sec
```

---

### Post by whoopa on 2010-06-23
Ok, so the problem is with PulseAudio!

In essence, the problem was never with SATA at all. If I had trouble mounting a disc or problems otherwise then maybe this would be an issue.

AFTER I had tested and came to the conclusion that it was only Audio CD's playing that caused the problem, I was able to come to a viable solution.

**Credit:** Credit is given where credit is due. I found this website which prompted me to try the change (in VLC) from Default Audio Output to ALSA Audio Output.
[http://forums.virtualbox.org/viewtopic.php?f=3&t=18308](http://forums.virtualbox.org/viewtopic.php?f=3&t=18308)

Thanks again to dino99 for at least saying hi, although I also respect the other viewers who may not have posted if they truly had nothing constructive to add.

P.S. What can I do to change ALSA to the default across the OS (if something like that's possible)? I can change VLC, but cannot Rhythmbox and possibly other programs.

---

