---
title: "Performance issues in streaming MPEG-2 Transport Stream from a DVB device to HDD"
date: 2013-01-21
forum: Hardware
---

### Post by teke on 2013-01-21
I'm using dvbstream to record MPEG-2 transport streams from DVB-C to hard disk.
Every 13...14 seconds there is found incontinuity in the recorded audio and video. Possibly this is caused by missing Transport Stream packets.

If I try to stream to a ram drive or if I view a DVB service with VLC, the output is not choppy. Thus I believe the driver for the DVB device (Technotrend C3650-CI through USB2) is OK.

I have been playing around with nice and renice values without any notable change in performance. 
I benchmarked the hard disk, file copy gives approximately 16MB/s speed, while the DVB transport stream bitrate is approx. 7MB/s at maximum. Thus the hard disk should be fast enough. 
I have tried both internal ext4 and external ntfs USB2 hard drive without a change in performance.
Strangely enough, if I do stream the full multiplex to disk with VLC, it works better; there are flaws in the video approximately every 25s. 

The distribution is out-of-box Lubuntu 12.10. 
This problem was not present with Ubuntu 10.04LTS, but I do not see downgrading as an option.
Hardware is an elderly Thinkpad R52 / Pentium M 1.87MHz, with 1GB of RAM.

Any ideas how to resolve this?

---

