---
title: "How to install Ultracam webcam on Thinkpad T20?"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by marcus74 on 2007-07-13
I am really new in Linux. I have installed Ubuntu 7.04 on a IBM Thinkpad T20. I managed everything to work. Only the integrated USB webcam IBM Ultracam on the Ultraport bay ([[COLOR="Blue"]see here[/COLOR]]("http://www.thinkwiki.org/wiki/UltraPort_Camera_%26_UltraPort_Camera_II")) is not working.
This webcam is not supported by [[COLOR="Blue"]Easycam[/COLOR]]("https://help.ubuntu.com/community/Webcam"), but on the net I found this driver: [http://www.gelato.unsw.edu.au/lxr/source/drivers/media/video/usbvideo/ultracam.c?a=i386](http://www.gelato.unsw.edu.au/lxr/source/drivers/media/video/usbvideo/ultracam.c?a=i386)
Is this driver made also for Ubuntu 7.04? (By the way, where may I found the kernel version in Ubuntu?).
In any case I really do not know how to install this driver which seems to be made in C language.
Could you some one explain me step by step how to install the driver starting from that web page?
Thanks,
marco

---

### Post by w4ett on 2007-07-13
First off...let's see if ubuntu is recognizing your camera...post the results of:  lsusb (from the terminal)

Second, there is an app in Synaptic which is almost guarenteed  to work with your cam..(at least to check video output) camstreamer.

Let's take it step by step and see where we get.

---

### Post by marcus74 on 2007-07-13
thanks for you reply.

It seems to recognize the webcam:
> 
marcus@hal9000:~$ lsusb
Bus 001 Device 003: ID 0461:0813 Primax Electronics, Ltd IBM UltraPort Camera
Bus 001 Device 001: ID 0000:0000 

About "Camstreamer" I cannot find it (Synaptics is "Add and Remove programs"?). I found and installed Camorama, but doesn't start saying: > "Could not connect to video device (/dev/video0). Please check connection"

Also in utility "GStreamer Properties" recognize the IBM Ultra Camera but if I click on test it, it crashes.

I feel I am near the solution, but... I cannot found the way (I have spent only 10 hours on Linux ever...).

regards,

marco

---

### Post by w4ett on 2007-07-13
> **marcus74 said:**
> thanks for you reply.

It seems to recognize the webcam:


About "Camstreamer" I cannot find it (Synaptics is "Add and Remove programs"?). I found and installed Camorama, but doesn't start saying: 

Also in utility "GStreamer Properties" recognize the IBM Ultra Camera but if I click on test it, it crashes.

I feel I am near the solution, but... I cannot found the way (I have spent only 10 hours on Linux ever...).

regards,

marco

System>Administration>Synaptic Package Manager.....Search for Camstream....you'll see it there....install it and the documentation file.

then from the terminal type:  camstream    It should work.

---

### Post by marcus74 on 2007-07-13
thanks for your patience...
here the results. camstream seems to recognize the cam but cannot visualize any image (just black) I had to kill the application because it hangs.

> marcus@hal9000:~$ camstream
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Failed to open configuration file for reading.

CCamWindow::CCamWindow()
CWebCamViewer::CWebCamViewer(0x80d1140, 0x0)
CVideoDevice::Init()
Using mmap(), VMBuf.size = 1843200
Trying to find video options for IBM Ultra Camera:/dev/video0
Creating new video options
<!DOCTYPE Configuration>
<config>
 <defaults/>
 <videodevices>
  <videoconfiguration name="IBM Ultra Camera" >
   <basename>snapshot</basename>
   <textfont>system</textfont>
   <textcolor>#ffff00</textcolor>
   <timeinimage>false</timeinimage>
   <fileformat>PNG</fileformat>
   <savetodisk>true</savetodisk>
   <ftptoserver>false</ftptoserver>
   <saveoption>1</saveoption>
   <maxsequence>1000</maxsequence>
   <sequence>0</sequence>
   <ftpserver></ftpserver>
   <ftppath></ftppath>
   <ftpuser></ftpuser>
   <ftppass></ftppass>
   <ftppassive>false</ftppassive>
   <ftpunique>true</ftpunique>
  </videoconfiguration>
 </videodevices>
</config>

CSnapshotSettingsDlg::CSnapshotSettingsDlg(...)
CVideoSettingsDlg::SizeChanged(640x480)
CVideoSettingsDlg::FramerateChanged(10)
CCamPanel::SetSize(640x480)
CCamPanel::SetImageSize(640x480)
CCamPanel::SetVisibleSize(640x480)
CCamPanel::SetSize(640x480)
CCamPanel::SetImageSize(640x480)
CCamPanel::SetVisibleSize(640x480)
RecalcTotalViewSize: resize viewport(640x480)
EnableRGB: +
CVideoDevice::SetPalette picked palette 4 [rgb24]
CVideoDevice::CreateImagesRGB()
 allocating space for RGB
CVideoDevice::StartCapture() go!
Killed


---

### Post by w4ett on 2007-07-13
It looks like it is working...but might need a tweak...Do you have a window opened titled: CAMSTREAMS?

if so click on file and open the viewer.....do you get another smaller window with any screen at all? (black or otherwise?)....

---

### Post by marcus74 on 2007-07-14
> It looks like it is working...but might need a tweak...Do you have a window opened titled: CAMSTREAMS?

Yes I have this windows.

> if so click on file and open the viewer.....do you get another smaller window with any screen at all? (black or otherwise?)....

Yes, I select "IBM Ultra Camera", a windows appears titled that, with some icons (like colors and settings) but it is black (no image) and hangs. I had to close the window with the "x" (force quit)

The same happens with the application Ekiga, if I select the webcam the application stops to work.

bye,
marco

---

### Post by ErusGuleilmus on 2007-07-14
This comment is completely irrelevant to the question, but what are the specs of the T-20 that you have?

---

### Post by marcus74 on 2007-07-14
These are the specs:
[http://www.thinkwiki.org/wiki/Category:T20](http://www.thinkwiki.org/wiki/Category:T20)
with the 12 gb hd. and 384 mb ram.

---

### Post by w4ett on 2007-07-14
I found this kernel patch to allow use of your camera....I think it's still in alpha testing, but it's definately worth a try:

[http://www.gutwin.org/cam/source/](http://www.gutwin.org/cam/source/)

---

