---
title: "Hauppauge WinTV-HVR2255 -composite input to record vcr tapes   - or 2250"
date: 2022-08-22
forum: Hardware
---

### Post by darter on 2022-08-22
I am using Ubuntu 20.04.4 LTS and use Kaffeine to use both tuners on this card to record off-the-air.  I recently have physically installed the A/V 'header' portion of the card that is connected with a cable and now allows me to push in composite RCA plugs to attempt to record from a VCR or camcorder that has composite output.  I'm pretty much stuck here as I don't really know what to select to choose this analog portion of the hardware that I think my camcorder is physically plugged into. When I use VLC I am choosing Media>Open Capture Device and then choosing' Video Camera'. Now here is the part that I am clueless about: in VLC I can choose Video device name and I may choose either (1) dev/video0   or  (2) dev/video1 . There is also a choice for 'Video standard' now set at Undefined.

I am not sure if I am trying to setup another device and maybe it would be named dev/video2 (???) and that 'device' would access the analog portion of the card?  Or maybe something else?

So I am wondering what step I should do next. My real understanding of this is limited but I can try different solutions.

Thanks.



In VLC when I hit Play I see a message: VLC is unable to open the MRL 'v4l2://'. Check the log for details.


=== vlc log ===
If this will help here is the log:
v4l2 error: cannot open device '/dev/video1': Operation not permitted
v4l2 error: cannot open device '/dev/video1': Operation not permitted
v4l2 error: cannot open device '/dev/video1': Operation not permitted

=== also  from a terminal here is some info==
 dmesg | grep 7164
[    0.464650] pci 0000:02:00.0: [1131:7164] type 00 class 0x048000
[    0.971641] Key type ._fscrypt registered
[    0.971643] Key type .fscrypt registered
[    0.971644] Key type fscrypt-provisioning registered
[   26.362827] CORE saa7164[0]: subsystem: 0070:f111, board: Hauppauge WinTV-HVR2255 [card=12,autodetected]
[   26.362839] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 53, latency: 0, mmio: 0xfe000000
[   26.581585] saa7164_downloadfirmware() no first image
[   26.581730] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   26.883383] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   26.883394] saa7164_downloadfirmware() firmware loaded.
[   26.883407] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   26.883414] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   26.883417] saa7164_downloadfirmware() BSLSize = 0x0
[   26.883420] saa7164_downloadfirmware() Reserved = 0x0
[   26.883422] saa7164_downloadfirmware() Version = 0x1661c00
[   34.017636] saa7164_downloadimage() Image downloaded, booting...
[   34.125685] saa7164_downloadimage() Image booted successfully.
[   36.433641] saa7164_downloadimage() Image downloaded, booting...
[   38.057597] saa7164_downloadimage() Image booted successfully.
[   38.110354] tveeprom: audio processor is SAA7164 (idx 43)
[   38.110357] tveeprom: decoder processor is SAA7164 (idx 40)
[   38.110363] saa7164[0]: Hauppauge eeprom: model=151061
[   40.171599] dvbdev: DVB: registering new adapter (saa7164)
[   40.171607] saa7164 0000:02:00.0: DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   40.212273] dvbdev: DVB: registering new adapter (saa7164)
[   40.212280] saa7164 0000:02:00.0: DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3306A VSB/QAM Frontend)...
[   40.249204] saa7164[0]: registered device video0 [mpeg]
[   40.475647] saa7164[0]: registered device video1 [mpeg]
[   40.687238] saa7164[0]: registered device vbi0 [vbi]
[   40.687482] saa7164[0]: registered device vbi1 [vbi]
[   40.689580] saa7164 driver loaded

---

