---
title: "Webcam not working - for home surveillance"
date: 2008-12-05
forum: Hardware
---

### Post by madhatter563 on 2008-12-05
Hey guys,

I'm trying to get a Phillips webcam model SPC110NC working for  surveillance.  It doesn't seem to work in 'motion' but seems to work in the 'cheese webcam booth' application.  Any ideas on how to get it working in motion or better software for recording motion on the webcam?  Thanks for any help!

Motion output:
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.9 Started
[0] ffmpeg LIBAVCODEC_BUILD 3355136 LIBAVFORMAT_BUILD 3409664
[0] Motion running in setup mode.
[0] Thread 1 is from /etc/motion/motion.conf
[0] Thread 1 is device: /dev/video0 input 8
[1] Thread 1 started
[1] cap.driver: "spca561"
[1] cap.card: "Generic Digital camera"
[1] cap.bus_info: "0000:00:1d.0"
[1] cap.capabilities=0x05000001
[1] - VIDEO_CAPTURE
[1] - READWRITE
[1] - STREAMING
[0] Waiting for threads to finish, pid: 9697
[1] Supported palettes:
[1] 0: GBRG (GBRG)
[1] Unable to find a compatible palette format.
[1] Using VIDEO_PALETTE_YUV420P palette
[1] Using V4L1
[1] Started stream webcam server in port 8081
[1] sync error in proc 9697: Invalid argument
[1] Raw changes: 62822 - changes after 'EedDl':     0 - labels:  11 - noise level: 130
[1] mcapture error in proc 9697: Invalid argument
[1] Video device fatal error - terminating camera thread
[1] Thread exiting
[1] Somebody stole the video device, lets hope we got his picture: Invalid argument
[1] Closing webcam listen socket
[1] Closing active webcam sockets: Invalid argument
[0] Threads finished
[0] Motion terminating


[http://www.p4c.philips.com/files/s/spc110nc_27/spc110nc_27_dfu_aen.pdf](http://www.p4c.philips.com/files/s/spc110nc_27/spc110nc_27_dfu_aen.pdf)

---

### Post by madhatter563 on 2008-12-09
bump

---

### Post by swimmerbody on 2008-12-24
same problem.  Got webcam working with cheese.  then wont work with motion.  light stays on all the time.  defi:confused:nitely a differene between intrepid and hardy

---

