---
title: "0c45:62c0 Microdia Webcam help on HP Pavilion dv9000"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by bluemarvel on 2007-05-20
Hello:

I am trying to get my Microdia webcam that is built into my HP Pavilion dv9000 notebook working on Feisty. I'd like to be able record video into software so that I can vlog, like I used to do on OS X using Quicktime Pro.

My webcam works very well under Ekiga 2.0.3 but no other software recognizes it.

Does anyone have any suggestions?

Thanks!
J.P.

Camstream reports:
The device experienced an error -19 (No such device).
With this going on in the console:
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 147
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode: 147
Minor opcode: 3
Resource id: 0x0
Failed to open device
CVideoDeviceInput: Warning: no channel info available.
CCamWindow::CCamWindow()
CWebCamViewer::CWebCamViewer(0x80d28e0, 320x240)
CVideoDevice::Init()
Allocating own buffer.
Trying to find video options for USB 2.0 Camera:/dev/video0
searching USB 2.0 Camera
CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
CVideoSettingsDlg::SizeChanged(176x144)
CVideoSettingsDlg::FramerateChanged(10)
CCamPanel::SetSize(176x144)
CCamPanel::SetImageSize(176x144)
CCamPanel::SetVisibleSize(176x144)
CVideoDevice::SetSize(320, 240)
CCamPanel::SetSize(320x240)
CCamPanel::SetImageSize(320x240)
CCamPanel::SetVisibleSize(320x240)
CWebCamViewer:eviceChangedSize(320x240)
RecalcTotalViewSize: resize viewport(320x240)
CCamPanel::SetSize(320x240)
CCamPanel::SetImageSize(320x240)
CCamPanel::SetVisibleSize(320x240)
RecalcTotalViewSize: resize viewport(320x240)
EnableRGB: +
CVideoDevice::SetPalette picked palette 8 [yuyv]
CVideoDevice::CreateImagesRGB()
allocating space for RGB
CVideoDevice::StartCapture() go!
CVideoDevice::LoadImage() Error loading image; errorcode=-19

EnableRGB: -
CVideoDevice::ResetImagesRGB()
freeing memory
CVideoDevice::SetPalette picked palette 0 []
CVideoDevice::StopCapture() halt!
CWebCamViewer::~CWebCamViewer()
CWebCamViewer::StopTimeSnap()
CWebCamViewer::StopFTP()
CCamWindow::~CCamWindow()


lsusb:
Bus 005 Device 003: ID 0c45:62c0 Microdia
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 1130:6606 Tenx Technology, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000


caminfo:
CVideoDeviceInput: Warning: no channel info available.Detected 1 Video4Linux devices.
Device node : /dev/video0
Name of device : "USB 2.0 Camera"
Minimum size : 48x32
Current size : 0x0
Maximum size : 0x0
Video inputs : 1
Input 0
Name : "(null)"
Type : Unknown
Audio : no
Tuners : 0
Audio inputs : 0

---

### Post by greenplastic on 2007-10-25
try this
luvcview -d /dev/video0 -f yuv -s 640x480

---

### Post by lgambett on 2007-11-14
Microdia Webcam WORKS FLAWLESSLY with Skype 2.0 Beta on Kubuntu Gutsy !
Uninstall any other Skype version (sudo aptitude remove skype)
Download the .deb package for Feisty from Skype website
Install it (sudo dpkg -i skype-debian....)
et voilà.

---

### Post by scorp123 on 2007-11-28
> **lgambett said:**
> Microdia Webcam WORKS FLAWLESSLY with Skype 2.0 Beta  It doesn't in my case. All I get is a black picture. More details in this posting here: 
[http://ubuntuforums.org/showthread.php?p=3847488#post3847488](http://ubuntuforums.org/showthread.php?p=3847488#post3847488)

I'm really confused here. No idea what's wrong.

---

### Post by scorp123 on 2008-04-20
Bump.

Still completely green screen in Ekiga, completely black screen in Skype 2.x ... Anyone have any idea why?

---

