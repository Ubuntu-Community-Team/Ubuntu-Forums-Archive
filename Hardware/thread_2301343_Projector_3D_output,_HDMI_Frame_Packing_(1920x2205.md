---
title: "Projector 3D output, HDMI Frame Packing (1920x2205)"
date: 2015-11-01
forum: Hardware
---

### Post by kyle59 on 2015-11-01
Good evening

I'm attempting to get a 3D output to a home projector
The Projector is an Optima 1070X Active 3D Projector using a HDMI 1.4a connection. The Graphics card is a Raedon HD 7970 using the open source drivers. 

Here is what I've done and managed so far to force the 3D resolution as shown here. [http://hdguru.com/3d-hdtv-and-hdmi-explained/1336/](http://hdguru.com/3d-hdtv-and-hdmi-explained/1336/)
Using the following commands I've setup the correct resolution (I believe)
```

$ cvt 1920 2205 24
# 1920x2205 23.99 Hz (CVT) hsync: 53.70 kHz; pclk: 135.75 MHz
Modeline "1920x2205_24.00"  135.75  1920 2024 2224 2528  2205 2208 2218 2238 -hsync +vsync
$ xrandr --newmode "1920x2205_24.00"  135.75  1920 2024 2224 2528  2205 2208 2218 2238 -hsync +vsync
$ xrandr --addmode HDMI-0 "1920x2205_24.00"
$ xrandr --output HDMI-0 --mode "1920x2205_24.00"

```

When doing this, the projector HUD Information shows that it's functioning at 2205x1920 @ 24Hz. The native resolution for this device is 1080x1920. At 2205x1920@24 the projector display just freezes and it increases the internal Fan. Seemingly not positive for the projector.
This projector has been tested through windows using a horrible program called PowerDVD on this computer (dual boot) and this is able to change the projector to 3D and function OK. So on a hardware level, things are suitable it seems. 
To do some extra testing, I have a LG TV that supports 3D frame packing through HDMI. So I connected this to the computer and set the output to 2205x1920_24. The TV will change to 3D automatically and works very well.

I get the feeling that some devices will change to 3D Frame packing mode by just the resolution only, while maybe the projector is wanting a 'special packet' to indicate a 3D signal.
Wondering if anyone has any experience in this or any idea's of how I can get this projector in 3D mode through Linux. 
The projector can only manually be placed in 3D mode when a 1080p display is been sent (SBS / OU) but this half's the resolution to each eye, which is why I wish to try and use Frame Packing. 

Thank you for any feedback
Regards ~

---

### Post by lordearl on 2015-11-29
Hey, I am now working on the same project. I got a frame-packing capable projector a few days ago. Could not get it running yet.

Have you tried the "bino" player? It is in the Ubuntu repos. It has an option to output 3D frame packing signals.

---

### Post by kyle59 on 2015-12-02
Good evening. 
I was not able to get this working with frame packing on the projector. 
The Above worked fine with the LG TV with just forcing the resolution. I expect the projector will only change to frame packing when a special packet is sent.
Yes I've been attempting to do this with Bino. My LG TV works fine using the frame packing method. To do this I ripped the Bluray using Make MKV and then converted to a 1080x1920 on the top and bottom with a spacing of 45 pixels. I had issues in locating software that was able to do this and add the blank spacing. So did this using premier on Windows. However it could probably be done using Blender or other software.
Once the video was created, I used the above commands to force the resolution, which allowed the LG TV to go into 3D mode and display in full resolution 3D using Bino.

However the projector doesn't automatically go into 3D mode with the correct resolution only. I was looking at using frame sequencing to do this but I wasn't able to locate a way on Linux of creating the video with frames being sequenced automatically. It again could be done using video editing software but would only be suitable for me if I could get a way of doing it automatically.

---

### Post by frafl on 2016-08-10
I had the same problem. The following hack worked: [http://askubuntu.com/questions/810404/send-stereoscopic-image-via-hdmi-frame-packing/810405#810405](http://askubuntu.com/questions/810404/send-stereoscopic-image-via-hdmi-frame-packing/810405#810405).
Basically I slightly modified the drm kernel module (2places, 3 lines) to send the infoframes if 1920x2205 is selected as resolution. Nevertheless, I'd be interested in "cleaner" solutions.

---

### Post by oldos2er on 2016-08-12
Old thread closed.

---

