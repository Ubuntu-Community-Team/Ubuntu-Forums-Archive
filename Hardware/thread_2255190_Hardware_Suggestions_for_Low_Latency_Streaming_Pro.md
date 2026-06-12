---
title: "Hardware Suggestions for Low Latency Streaming Product"
date: 2014-12-02
forum: Hardware
---

### Post by Todd_Mendenhall on 2014-12-02
I am looking for suggestions for the production version of a product we have already prototyped. 
Keep in mind that we are trying to make 1000 of these so hardware overkill is not an option. 
On the other hand, it has to work every time so we cannot afford to run hardware right at its limits.

The system description is as follows:

A high resolution security camera produces a RTSP stream at 1920x1080, 25 Hz. The stream is limited
 to 8 Mbps. The hardware takes the RTSP stream that arrives over wired Ethernet and displays the video 
onto a LED television via HDMI at 1920x1080. The hardware must also monitor a joystick/game controller
 to issue HTML commands to the camera. Later on, the hardware may perform basic video processing and 
overlay on the stream.

The key issue I am having is latency in the display of the video. The RTSP video plays flawlessly on my 
Windows PC using both the ONVIF Device Manager and VLC. The latency in VLC is maybe 250 msec, in the 
ONVIF Device manager is it on the order of 100 msec.  I have an older laptop running Ubuntu and the RTSP 
video runs flawlessly on VLC but the best latency I can get is about 1 second.

On the bottom end, I have run the stream on a Raspberry Pi using OMXPlayer (hardware accelerated) and the  
best latency I can get at 1080p is about 2-3 seconds. I have tried using Mplayer on a Odroid UX3 but the 
lack of hardware acceleration is limiting.

There is a dizzying array of new small boards with powerful processors (Firefly RK3288, A80 Optimus Board).
I am worried about support and drivers for the new boards. 

Board size is not a problem, power is not a problem. The solution has to cost less than $200 in 1000 quantity.

Any help would be greatly appreciated.

Thanks to all.

Todd

---

### Post by baapek on 2014-12-03
Did yuo install Ubuntu 14.04 or what

---

