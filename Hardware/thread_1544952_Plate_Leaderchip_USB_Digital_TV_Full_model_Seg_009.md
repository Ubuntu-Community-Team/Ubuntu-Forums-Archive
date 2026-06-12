---
title: "Plate Leaderchip USB Digital TV Full model Seg 0090"
date: 2010-08-03
forum: Hardware
---

### Post by emmerick on 2010-08-03
Hi all,
My name is Emmerick and am new in linux world, until now the moment got several things just by reading tutorials and panning on the Net, even managed to run a 3d minimo ta more going on in the woods for my board SIS 671 of my notebook.
More trouble could I try to install the receiver for digital TV Full Mon in Ubuntu. Have ran everything even thought up a tutorial, but I will follow the tutorial cool, more Guando arrive at the Scan on my terminal appears that I have access denied.
```
bash: channels.conf: Permissão negada
```
I've tried everything and not getting to, I will leave here the specifications of my system, lsusb and address of the tutorial that I'm following to see if you can help me.
let go then:
[HTML]emmerick@emmerick-laptop:/$ uname -r
2.6.32-24-generic[/HTML]
[HTML]emmerick@emmerick-laptop:/$ lsusb
Bus 003 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 10b8:1fa0 DiBcom-------------------------------------------------------------- -------------- This is the Digital TV card
Bus 001 Device 006: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/HTML]
This here is recptor:
[IMG]http://www.leadership.com.br/imgs/grd/0090_g.jpg[/IMG]
[HTML]Product Name: DIGITAL TV RECEIVER FULL SEG Code: 0090Família: LeadershipDescrição: 
Fully compatible with the new standard Brazilian Digital TV. Compatible with both signs and 1Seg Fullseg that lets users watch their favorite shows in high definition. Watch Digital TV programming directly on your notebook or PC. Have full mobility watching Digital TV anywhere with your notebook. Lets you record and schedule the recording of TV programming directly on your HD. Function "Instant Replay" which allows pause live programming. Accompanying application that allows automatic tuning of channels. Menus and Settings portguês fully. Ability to view the program name displayed, synopsis and program schedules. It also has adjustable brightness, contrast, color saturation and allows you to view the program in full screen. 


Key Features: 
- Fully compatible with the new standard Brazilian Digital TV 
- Compatible with both signs and 1Seg Fullseg that lets users watch their favorite shows in high definition 
- Watch Digital TV programming directly on your PC or Notebook 
- Have full mobility watching Digital TV anywhere with your laptop 
- Allows you to record and schedule recording of TV programming directly on your HD 
- Function "Instant Replay" which allows pause live programming 
- Monitoring application that allows automatic tuning of channels 
- Menus and Settings entirely in Portuguese 
- Ability to view the program name displayed ¹, ¹ and synopsis of the programming grid ¹ 
- Has also adjust brightness, contrast, color saturation and allows you to view the program in full screen 

Technical Information: 
- PC Connection: USB 2.0 
- Signal Transmission Compatible: Full Sun / 1 Mon 
- AVC: H.264 
- Video Decoder: MPEG &#82084; Part.10 
- Audio Decoder: MPEG &#82084; HE-AAC @ L2 Stereo 
- Scan channel / recording schedule 
- Major recording formats: AVI and MPEG 
- Edit / Cut / Burning videos recorded by the receiver in TotalMedia ² 

Playback Features: 
- Resolution of playback: 
FullSeg HD or FullHD ¹ 
1s: Maximum Resolution of 360 x 240 px 
- Video Control: Brightness / Contrast / Color / Saturation Control.[/HTML]
Now to the tutorial:
The same is located at: [http://www.guax.net/2009/12/review-receptor-isdb-t-dibcom-stk8096gp-tv-digital-do-brasil/](http://www.guax.net/2009/12/review-receptor-isdb-t-dibcom-stk8096gp-tv-digital-do-brasil/) I'll try to reproduce it here, credits are all the author of the page above.
[HTML]That does not help much but it gives us the make and model of the chip. With it's easy to give a google about how it will work on Linux. The good news is that the manufacturer is nice and cooperated with the making of the driver. We have a stand still for so early in the ISDB-T http://www.linuxtv.org/. A matter of downloading, a make, make install and everything ready. To do this just grab the trunk (since it is experimental we live dangerously).[/HTML]
```
$ hg clone http://www.linuxtv.org/hg/v4l-dvb
$ cd v4l-dvb
$ make
$ su
# make rmmod
# make install
```
[HTML]You can substitute su with sudo if you prefer. After installing the drivers still need the firmware of the device. Just download here http://www.guax.net/pub/windows/mygica-s870-driver/dvb-usb-dib0700-1.20.fw and put it in / lib / firmware / everything will be fine. The response from dmesg after replugar the device should now be something like:[/HTML]
[HTML]dib0700: loaded with support for 14 different device-types
dvb-usb: found a 'DiBcom STK8096GP reference design' in cold state, will try to load
a firmware
firmware: requesting dvb-usb-dib0700-1.20.fw
dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
dib0700: firmware started successfully.
dvb-usb: found a 'DiBcom STK8096GP reference design' in warm state.
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
DVB: registering new adapter (DiBcom STK8096GP reference design)
DVB: registering adapter 0 frontend 0 (DiBcom 8000 ISDB-T)...
DiB0090: successfully identified
input: IR-receiver inside an USB DVB receiver as /devices/...
dvb-usb: schedule remote query interval to 50 msecs.
dvb-usb: DiBcom STK8096GP reference design successfully initialized and connected.
usbcore: registered new interface driver dvb_usb_dib0700[/HTML]
[HTML]Is not it beautiful?

Thus we have the device working but still missing the piece that made me lose a few hours. Scan the channels to see Bill Murray on the small screen of your PC (it fits now that weight loss). To do this we will use the tools that driver up there before already installed along with the modules. The application will scan it but it needs information to do their job, she needs a list of frequencies and power ranges to scan for approval. This list I got the first blog dougsland (which does not seem real name posted on the website). Knowing what I was looking for (frequency table) I could find in the excellent wiki linuxtv.org in http://www.linuxtv.org/wiki/index.php/ISDB-T_Frequency_Table

Copy and paste the contents into a ch.conf then run the scan command to generate the list of available channels:[/HTML]
```
$ scan ch.conf > channels.conf
```
[HTML]This will generate a lot of errors like:[/HTML]
```
>>> tune to: 503142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM_
AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE
```
[HTML]But do not worry, they are normal. If you have received in the middle of that hill you will see an error:[/HTML]
```
Network Name 'RBS TV FLOPS'
0x0000 0xdc60: pmt_pid 0x0101 (null) -- RBS TV HD (???)
0x0000 0xdc78: pmt_pid 0x1fc8 (null) -- RBS TV 1seg (???)
```
[HTML]And then your file will channels.conf information channels for you to see them. If you're in Florianopolis Santa Catarina Brazil around the year 2009 you will only have two channels, a 1 sec and another full FES are, unfortunately:[/HTML]
```
RBS TV HD:587142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM
_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:273:274:
56416
RBS TV 1seg:587142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_3_4:FEC_AUTO:QAM
_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_NONE:529:530:
56440
```
[HTML]After all, the Band has yet to dawn on Saturday to cheer the kids. Thus we get the last step: watch TV. But first, a quick explanation about the area before all the digital TV (did not think I was going to release right now?). 

The whole world uses of these DVB-S, DVB-T, DVB-S, DVB-C and ATSC, Japan has created and uses the ISDB-T, Brazil has adopted it and uses it to broadcast, even uses the same range frequencies, if the tables are not the same they are very similar. Digital broadcasting uses 13 segments, a pattern that left them reserved for low-quality broadcasting to mobile devices with small screens or low capacity. Yes, this is just the 1s that you will see a lot. The rest is broadcast in 12 segments (full-seg) and these transmissions are standard and hd. The codec used is AAC audio and video and H264. 

The entire front is resolved by the driver, beautiful and functional, a charm art. But ... the question of the codec yet. Although the MPlayer have put support for now is not good until the writing of this text. The only viable alternative for now is that VLC has support for h264 and AAC. Besides understanding with DVB. 

To operate you simply click on View> Playlist, click on more, add the channels.conf that you created, make two clicks and done just that simple.[/HTML]
[IMG]http://www.guax.net/wp-content/uploads/2009/12/vlc-300x97.png[/IMG]
[HTML]But let's get down to business, and the HD?? Well, you see. The H264 provides high compression with little loss of quality, but this has a cost, a kidney. I mean, a processor, you need a good machine to decode the video in HD 1080p. So much so that in Linux I could not play properly due to the implementation of h264, audio is perfect with no problem, video is catching, even in powerful windows (because of my proc dai). To be honest, in VLC I could not see nor 1seg rights on behalf of decoding h264 video is framed repeated (failed interpolation or something out there). You may have more luck in a newer version of VLC or better (do not let padawan)[/HTML]
[IMG]http://www.guax.net/wp-content/uploads/2009/12/rbshd-300x175.png[/IMG]

The problem of permission denied I'm not taking over now I try an error in the SCAN
```
root@emmerick-laptop:~# scan ch.conf > channels.conf
scanning ch.conf
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
```

I tried everything, I do not know what to do.
Thanks to all
PS: Sorry for my english

---

