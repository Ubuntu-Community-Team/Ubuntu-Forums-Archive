---
title: "No video"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by glaucon on 2005-08-18
So im having a huge problem getting any video to work on my laptop, its custom built and im not sure what graphics card im using nothing seems to be labeled in my device manager, so as far as i can tell its an intel card. I have tried about every media player in the universe, downloaded the codecs, tried the nvidia drivers, even tried it on kubuntu just to see if by some chance it would work, but no matter what i do the video field goes blue and then i crash, and crash hard- not even a cursor to be seen. 

It does this no matter what format im trying, original dvds, dvd files, burned dvds, avi, mpg, even visuals in totem. 

Help me please im at my whits end!  ](*,) 

thanks- Glaucon

---

### Post by heimo on 2005-08-19
I would try to install vlc and run it from terminal
 ```
vlc -vv video_file.mpeg
``` 

Watch for errors on terminal.

---

### Post by glaucon on 2005-08-19
I went ahead and ran an mpg and I cant make ANY sense out of what it gave me, forgive my newbieness.

it gave me this :

leluiahkiani@Hiro-Jani:~$ vlc -vv test.mpg
VLC media player 0.8.1 Janus
[00000001] main vlc debug: opening config file /home/leluiahkiani/.vlc/vlcrc
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/leluiahkiani/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 184 modules
[00000001] main vlc debug: opening config file /home/leluiahkiani/.vlc/vlcrc
[00000000] main root debug: VLC media player - version 0.8.1 Janus - (c) 1996-2004 VideoLAN
[00000000] main root debug: libvlc was configured with ./configure --mandir=/share/man --infodir=/share/info --enable-release --prefix=/usr --disable-gnome --disable-gtk --disable-familiar --disable-fb --enable-ggi --enable-sdl --enable-esd --disable-qt --enable-mad --enable-arts --enable-alsa --enable-lirc --enable-a52 --enable-aa --enable-dvbpsi --enable-xosd --enable-mozilla --disable-kde --enable-mp4 --enable-dvb --enable-dv --disable-satellite --enable-ogg --enable-vorbis --enable-wxwindows --disable-slp --enable-flac --disable-skins --disable-basic-skins --enable-skins2 --enable-freetype --enable-mkv --enable-v4l --enable-pvr --disable-speex --enable-caca --enable-livedotcom --enable-libmpeg2 --enable-dts --enable-fribidi --enable-cdio --enable-mod --enable-theora --enable-modplug --enable-dvdnav --enable-gnutls --enable-ffmpeg --with-ffmpeg-tree=extras/ffmpeg --enable-faad --with-faad-tree=extras/faad2 --enable-x264 --with-x264-tree=extras/x264 --enable-glide --enable-svgalib --enable-dvd --without-dvdcss --no-create --no-recursion
[00000001] main vlc debug: translation test: code is "C"
[00000001] main vlc debug: opening config file /home/leluiahkiani/.vlc/vlcrc
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/leluiahkiani/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 184 modules
[00000001] main vlc debug: opening config file /home/leluiahkiani/.vlc/vlcrc
[00000001] main vlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU
[00000001] main vlc debug: looking for memcpy module
[00000001] main vlc debug: probing 3 candidates
[00000010] main module debug: using memcpy module "memcpymmxext"
[00000232] main playlist debug: creating group Normal with id 1 at position 0
[00000232] main playlist debug: waiting for thread completion
[00000232] main playlist debug: thread -1213514832 (playlist) created at priority 0 (src/playlist/playlist.c:107)
[00000233] main interface debug: looking for interface module
[00000233] main interface debug: probing 1 candidate
[00000127] main module debug: using interface module "hotkeys"
[00000233] main interface debug: interface initialized
[00000233] main interface debug: thread -1221928016 (interface) created at priority 0 (src/interface/interface.c:209)
[00000232] main playlist debug: adding playlist item `test.mpg' ( test.mpg )
[00000235] main interface debug: looking for interface module
[00000235] main interface debug: probing 4 candidates
[00000039] main module debug: using interface module "wxwindows"
[00000235] main interface debug: interface initialized
[00000235] main interface debug: thread -1245357136 (manager) created at priority 0 (src/interface/interface.c:194)
[00000235] wxwindows interface debug: accelerator table loaded
[00000232] main playlist debug: creating new input thread
[00000238] main input debug: waiting for thread completion
[00000238] main input debug: `test.mpg' gives access `' demux `' path `test.mpg'[00000238] main input debug: demux2_New: access='' demux='' path='test.mpg'
[00000239] main demuxer debug: looking for access_demux module
[00000239] main demuxer debug: probing 2 candidates
[00000238] main input debug: thread -1254741072 (input) created at priority 0 (src/input/input.c:228)
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Can't stat test.mpg
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000239] dvdnav demuxer warning: cannot open dvdnav
[00000238] main input debug: access2_New: access='' path='test.mpg'
[00000242] main access debug: looking for access2 module
[00000242] main access debug: probing 4 candidates
[00000242] vcd access warning: could not open test.mpg
[00000242] access_file access warning: cannot stat() file `test.mpg' (No such file or directory)
[00000242] cdda access warning: could not open test.mpg
[00000238] main input debug: access2_New: access='' path='test.mpg'
[00000248] main access debug: looking for access2 module
[00000248] main access debug: probing 4 candidates
[00000248] vcd access warning: could not open test.mpg
[00000248] access_file access warning: cannot stat() file `test.mpg' (No such file or directory)
[00000248] cdda access warning: could not open test.mpg
[00000238] main input error: no suitable access module for `test.mpg'
[00000238] main input debug: thread -1254741072 joined (src/input/input.c:290)

---

### Post by heimo on 2005-08-19
You probably didn't have test.mpg in that directory. Try with some video file that has crashed your system earlier. Most of the time 90% of debug info is useless, but I'm hoping to get at least some clue about what's wrong on your system. Probably something to do with graphics card driver. Don't know.

---

### Post by glaucon on 2005-08-19
unfortunately, when it actualy runs the video, the system crashes before i can even look at what is in terminal :(

---

### Post by heimo on 2005-08-19
[QUOTE=glaucon]unfortunately, when it actualy runs the video, the system crashes before i can even look at what is in terminal :([/QUOTE]

Redirect output to file:
vlc -vv video_file.mpg > ~/vlc.log 2>&1

After the crash, reboot and read file vlc.log in your home directory.

---

### Post by glaucon on 2005-08-19
Thats a nifty little trick! Here is what was in the log, but again im completely clueless:

VLC media player 0.8.1 Janus
[00000001] main vlc debug: opening config file /home/leluiahkiani/.vlc/vlcrc
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/leluiahkiani/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 184 modules
[00000001] main vlc debug: opening config file /home/leluiahkiani/.vlc/vlcrc
[00000000] main root debug: VLC media player - version 0.8.1 Janus - (c) 1996-2004 VideoLAN
[00000000] main root debug: libvlc was configured with ./configure --mandir=/share/man --infodir=/share/info --enable-release --prefix=/usr --disable-gnome --disable-gtk --disable-familiar --disable-fb --enable-ggi --enable-sdl --enable-esd --disable-qt --enable-mad --enable-arts --enable-alsa --enable-lirc --enable-a52 --enable-aa --enable-dvbpsi --enable-xosd --enable-mozilla --disable-kde --enable-mp4 --enable-dvb --enable-dv --disable-satellite --enable-ogg --enable-vorbis --enable-wxwindows --disable-slp --enable-flac --disable-skins --disable-basic-skins --enable-skins2 --enable-freetype --enable-mkv --enable-v4l --enable-pvr --disable-speex --enable-caca --enable-livedotcom --enable-libmpeg2 --enable-dts --enable-fribidi --enable-cdio --enable-mod --enable-theora --enable-modplug --enable-dvdnav --enable-gnutls --enable-ffmpeg --with-ffmpeg-tree=extras/ffmpeg --enable-faad --with-faad-tree=extras/faad2 --enable-x264 --with-x264-tree=extras/x264 --enable-glide --enable-svgalib --enable-dvd --without-dvdcss --no-create --no-recursion
[00000001] main vlc debug: translation test: code is "C"
[00000001] main vlc debug: opening config file /home/leluiahkiani/.vlc/vlcrc
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/leluiahkiani/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 184 modules
[00000001] main vlc debug: opening config file /home/leluiahkiani/.vlc/vlcrc
[00000001] main vlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main vlc debug: looking for memcpy module
[00000001] main vlc debug: probing 3 candidates
[00000010] main module debug: using memcpy module "memcpymmxext"
[00000232] main playlist debug: creating group Normal with id 1 at position 0
[00000232] main playlist debug: waiting for thread completion
[00000232] main playlist debug: thread -1213514832 (playlist) created at priority 0 (src/playlist/playlist.c:107)
[00000233] main interface debug: looking for interface module
[00000233] main interface debug: probing 1 candidate
[00000127] main module debug: using interface module "hotkeys"
[00000233] main interface debug: interface initialized
[00000233] main interface debug: thread -1221928016 (interface) created at priority 0 (src/interface/interface.c:209)
[00000232] main playlist debug: adding playlist item `test.mpg' ( test.mpg )
[00000235] main interface debug: looking for interface module
[00000235] main interface debug: probing 4 candidates
[00000039] main module debug: using interface module "wxwindows"
[00000235] main interface debug: interface initialized
[00000235] main interface debug: thread -1245357136 (manager) created at priority 0 (src/interface/interface.c:194)
[00000235] wxwindows interface debug: accelerator table loaded
[00000232] main playlist debug: creating new input thread
[00000238] main input debug: waiting for thread completion
[00000238] main input debug: `test.mpg' gives access `' demux `' path `test.mpg'
[00000238] main input debug: demux2_New: access='' demux='' path='test.mpg'
[00000239] main demuxer debug: looking for access_demux module
[00000239] main demuxer debug: probing 2 candidates
[00000238] main input debug: thread -1254741072 (input) created at priority 0 (src/input/input.c:228)
[00000238] main input debug: access2_New: access='' path='test.mpg'
[00000242] main access debug: looking for access2 module
[00000242] main access debug: probing 4 candidates
[00000242] vcd access debug: trying .cue file: test.cue
[00000242] vcd access warning: could not open test.mpg
[00000242] access_file access debug: opening file `test.mpg'
[00000025] main module debug: using access2 module "access_file"
[00000247] main private debug: pre buffering
[00000247] main private debug: received first data for our buffer
[00000247] main private debug: prebuffering done 851942 bytes in 0s - 7007 kbytes/s
[00000238] main input debug: demux2_New: access='' demux='' path='test.mpg'
[00000248] main demuxer debug: looking for demux2 module
[00000248] main demuxer debug: probing 34 candidates
[00000248] mp4 demuxer warning: MP4 plugin discarded (not a valid file)
[00000248] avi demuxer warning: avi module discarded (invalid header)
[00000248] asf demuxer warning: ASF plugin discarded (not a valid file)
[00000248] flac demuxer warning: flac module discarded (no startcode)
[00000248] mpgv demuxer warning: ES module discarded (system startcode)
[00000248] main demuxer debug: looking for id3 module
[00000248] main demuxer debug: probing 2 candidates
[00000248] id3tag demuxer debug: checking for ID3 tag
[00000168] main module debug: using id3 module "id3tag"
[00000168] main module debug: unlocking module "id3tag"
[00000248] aac demuxer warning: AAC module discarded
[00000248] sap demuxer warning: SDP (UDP) module discarded
[00000248] livedotcom demuxer warning: SDP module discarded
[00000248] ogg demuxer warning: ogg module discarded (invalid header)
[00000248] mkv demuxer warning: matroska module discarded (invalid header 0x000001ba)
[00000248] real demuxer warning: Real module discarded
[00000248] pva demuxer warning: PVA module discarded
[00000248] nsv demuxer warning: NSV module discarded
[00000248] aiff demuxer warning: AIFF module discarded
[00000248] playlist demuxer warning: old import module discarded: invalid file
[00000248] playlist demuxer warning: pls import module discarded
[00000248] au demuxer warning: AU module discarded
[00000248] ts demuxer warning: TS module discarded
[00000248] mod demuxer warning: MOD module discarded (extention 'mpg' unknown)
[00000139] main module debug: using demux2 module "ps"
[00000238] main input debug: `test.mpg' sucessfully opened
[00000238] main input debug: control type=1
[00000238] main input debug: Selecting program id=0
[00000281] main decoder debug: looking for decoder module
[00000281] main decoder debug: probing 20 candidates
[00000099] main module debug: using decoder module "mpeg_audio"
[00000281] main decoder debug: thread -1278620752 (decoder) created at priority 0 (src/input/decoder.c:157)
[00000285] main decoder debug: looking for decoder module
[00000285] main decoder debug: probing 20 candidates
[00000118] main module debug: using decoder module "libmpeg2"
[00000285] main decoder debug: thread -1288238160 (decoder) created at priority 0 (src/input/decoder.c:157)
[00000285] libmpeg2 decoder debug: 352x288, aspect 563200, 25.000 fps
[00000285] main decoder debug: no usable vout present, spawning one
[00000286] main video output debug: looking for video output module
[00000286] main video output debug: probing 6 candidates
[00000281] mpeg_audio decoder: MPGA channels:2 samplerate:44100 bitrate:192
[00000281] main decoder debug: no aout present, spawning one
[00000288] main audio output debug: looking for audio output module
[00000288] main audio output debug: probing 2 candidates
[00000288] oss audio output error: cannot open audio device (/dev/dsp)
[00000286] xvideo video output debug: adaptor 0, port 52, format 0x32315659 (YV12) planar
[00000176] main module debug: using audio output module "dummy"
[00000288] main audio output debug: output 'mpga' 44100 Hz Stereo frame=1152 samples/1262 bytes
[00000288] main audio output debug: mixer 'mpga' 44100 Hz Stereo frame=1152 samples/1262 bytes
[00000288] main audio output debug: filter(s) 'fl32'->'mpga' 44100 Hz->44100 Hz Stereo->Stereo
[00000298] main private debug: looking for audio filter module
[00000298] main private debug: probing 23 candidates
[00000287] main private debug: Registering subpicture channel, ID: 2
[00000287] main private debug: Registering subpicture channel, ID: 3
[00000287] main private debug: Registering subpicture channel, ID: 4
[00000287] main private debug: Registering subpicture channel, ID: 5
[00000286] xvideo video output debug: Window manager supports NetWM
[00000286] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000286] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000286] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000211] main module debug: using video output module "xvideo"
[00000286] main video output debug: waiting for thread completion
[00000286] main video output debug: got 8 direct buffer(s)
[00000286] main video output debug: picture in 352x288, chroma 0x30323449 (I420), aspect ratio 176:135
[00000286] main video output debug: picture out 352x288, chroma 0x30323449 (I420), aspect ratio 176:135
[00000286] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000286] main video output debug: thread -1298138192 (video output) created at priority 0 (src/video_output/video_output.c:443)
[00000299] main private warning: dts != current_pts (-207877)
[00000299] main private warning: backward_pts != current_pts (-40000)
[00000288] main audio output error: couldn't find a filter for the conversion
[00000288] main audio output error: couldn't set an output pipeline
[00000176] main module debug: unlocking module "dummy"
[00000299] main private debug: stream periodicity changed from B[1] to B[2]
.: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

---

### Post by mo_x on 2005-08-19
You might want to find out what kind of videocard you have. Enter the following command in a terminal and post the output:```
lspci
```

---

### Post by glaucon on 2005-08-19
leluiahkiani@Hiro-Jani:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:01:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:01:04.0 CardBus bridge: ENE Technology Inc CB710 Cardbus Controller
0000:01:04.1 FLASH memory: ENE Technology Inc: Unknown device 0530
0000:01:04.2 0805: ENE Technology Inc: Unknown device 0550
leluiahkiani@Hiro-Jani:~$

---

### Post by mo_x on 2005-08-19
You have an intel graphics card. You probably need the i810 driver. Do a search on this forum for i810, that will give you more information, also other people are having problems with this.

---

