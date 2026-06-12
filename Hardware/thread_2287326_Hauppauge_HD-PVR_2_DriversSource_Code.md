---
title: "Hauppauge HD-PVR 2 Drivers/Source Code"
date: 2015-07-18
forum: Hardware
---

### Post by shspvr on 2015-07-18
Link [http://www.hauppauge.com/site/support/linux.html#tabs-3](http://www.hauppauge.com/site/support/linux.html#tabs-3)

Also the 1st gen Colossus is there as well have but not tested
I have look into and see if it work with Colossus 2

There a small error in readme and there we site but video is dead on
$ sudo copy 99-Hauppauge-PVR2.rules to /etc/udev/rules.d/
$ sudo cp 99-Hauppauge-PVR2.rules to /etc/udev/rules.d/
need be change to
$ sudo cp 99-Hauppauge-PVR2.rules /etc/udev/rules.d/

If have all ready Install this and are not have any luck and it saying 000000.018189 cannot open device 2040:E5??
Del the folder hauppauge_hdpvr2_driver_ver6 folder off your desktop
Unzip a new copy on to the desktop

Run lsusb look for Hauppauge in USB print out for example
Bus 002 Device 002: ID 2040:e514 Hauppauge
HardwareID is 2040:e514 in case we have subID of e514

Now that you know what Hardware subID is the frist thing you want to do edit the file 99-Hauppauge-PVR2.rules
SUBSYSTEM=="usb", ATTR{idProduct}=="e524", ATTRS{idVendor}=="2040", MODE="0660", GROUP="plugdev"
Change e524 to match your subID just example like mine show as e514
SUBSYSTEM=="usb", ATTR{idProduct}=="e514", ATTRS{idVendor}=="2040", MODE="0660", GROUP="plugdev"
Save the file

Next we need to edit in the folder TestApp the file called main.cpp
Fined the line #define kMyProductID 0xE524
Edit your to match you subID just example like mine show as e514
#define kMyProductID 0xE514
Save the file

---

### Post by TheFu on 2015-07-18
Got the code from Hauppauge a few weeks ago. The readme-files are really rough. **They misspelled the company name!**  Well - my 1512 was sent to hauppauge for the 2nd time for an RMA.  It worked fine (under Windows) for about 18 months - then a puff of white smoke and RMA #1.  Got that back and it worked for about a week, then refused to connect -on Windows or Linux. No smoke this time.  Have 5 more months on the warranty.

So - i haven't gotten to test the Linux code yet, but did get it compiled and setup on a chromebook here.

Just got the 2nd RMA back today and was in the middle of a few other tasks today (new R-Pi-v2 Kodi+PlexBMC and migrating a dual boot laptop from 500G disk to 750G disk). Just haven't had time to touch the Hauppauge.  I didn't see any mention of DD/DTS 5.1 audio in the REAME files. Any news about that? There are 50% less costly ($80) single purpose HDMI capture devices with 20Mbps peak 1080 video with stereo AAC audio.  The recorded video (h.264/aac/mkv) is huge and broken at 2G points, but it is gorgeous! Sadly, the audio is just stereo.  A transcode with 19.5 quality settings reduces the file sizes by approx 75%.  The 1512 is 14Mbps peak for 1080 video, but with Windows it can record DTS/DD 5.1 audio too - for me, that is a key differentiator and why $160 is ok.  Just wish they weren't so temperamental. My 1512 has never been moved and sits on a steel rack with no airflow blocked anywhere around it.

Should be able to test the code this week. I'll update here, if anything interesting happens.

---

### Post by shspvr on 2015-07-18
> **TheFu said:**
> Got the code from Hauppauge a few weeks ago. The readme-files are really rough. **They misspelled the company name!**  Well - my 1512 was sent to hauppauge for the 2nd time for an RMA.  It worked fine (under Windows) for about 18 months - then a puff of white smoke and RMA #1.  Got that back and it worked for about a week, then refused to connect -on Windows or Linux. No smoke this time.  Have 5 more months on the warranty.
Yes you should have scean readme way before 
WoW I never heard them doing that before 

> **TheFu said:**
> So - i haven't gotten to test the Linux code yet, but did get it compiled and setup on a chromebook here.

Just got the 2nd RMA back today and was in the middle of a few other tasks today (new R-Pi-v2 Kodi+PlexBMC and migrating a dual boot laptop from 500G disk to 750G disk). Just haven't had time to touch the Hauppauge.  I didn't see any mention of DD/DTS 5.1 audio in the REAME files. Any news about that? There are 50% less costly ($80) single purpose HDMI capture devices with 20Mbps peak 1080 video with stereo AAC audio.  The recorded video (h.264/aac/mkv) is huge and broken at 2G points, but it is gorgeous! Sadly, the audio is just stereo.  A transcode with 19.5 quality settings reduces the file sizes by approx 75%.  The 1512 is 14Mbps peak for 1080 video, but with Windows it can record DTS/DD 5.1 audio too - for me, that is a key differentiator and why $160 is ok.  Just wish they weren't so temperamental. My 1512 has never been moved and sits on a steel rack with no airflow blocked anywhere around it.

Should be able to test the code this week. I'll update here, if anything interesting happens.
I have look at source code but my guest it that may be left out duelicensing or have got to it
You know about flip it up down rigth to allow heat better get out the case holes as that the I had it run under SageTV Server under windows.

I hope lee we see some here that hard core dev that make better

---

### Post by TheFu on 2015-07-20
From [http://www.hauppauge.com/site/support/support_hdpvr2.html](http://www.hauppauge.com/site/support/support_hdpvr2.html) 
> [B]
Can I use the HD PVR 2 with Linux?[/B]
We are starting to test our Linux support for the HD PVR 2. If you would like to try this out, please send a note to us at: [email]support@hauppauge.com[/email]


Also - NextPVR (a windows program) has support for the HD-PVR2 (and Colossus and HD Homerun models) according to this:  [http://www.nextpvr.com/#devices](http://www.nextpvr.com/#devices)

That is good news all around.  Because MSFT is killing off Media Center.

In the USA, Microsoft Media Center just changed all the schedule data from Zap2It to Rovi and lots of people have discovered they don't have any schedule data going forward. ** I'm in that boat too.**  MC has been reasonably trouble free for 4 yrs. The last 2 days, I've been trying to get OTA schedule data - tried everything - including reinstalling 7MC.  The data ends at 7pm tonight. That's the deadline for a new solution.  

In the USA, we have to pay for TV schedule data, sadly. In the long run, looks like buying a new [HDHR4]("https://www.silicondust.com/products/models/hdhr4-2us/") will provide schedule data AND a DLNA server for live TV.  Already use 2 HDHR3 tuners here. Love them! That's probably better than paying [Scheduled Direct]("http://www.schedulesdirect.org/") $25/yr.  Tried MythTV two prior times and failed. My Linux-fu must be too weak. Perhaps 1 more time?

I do not use the 1512 to record TV, so that isn't a helpful answer.

---

### Post by shspvr on 2015-07-21
> **TheFu said:**
> From [http://www.hauppauge.com/site/support/support_hdpvr2.html](http://www.hauppauge.com/site/support/support_hdpvr2.html) 


Also - NextPVR (a windows program) has support for the HD-PVR2 (and Colossus and HD Homerun models) according to this:  [http://www.nextpvr.com/#devices](http://www.nextpvr.com/#devices)

That is good news all around.  Because MSFT is killing off Media Center.

In the USA, Microsoft Media Center just changed all the schedule data from Zap2It to Rovi and lots of people have discovered they don't have any schedule data going forward. ** I'm in that boat too.**  MC has been reasonably trouble free for 4 yrs. The last 2 days, I've been trying to get OTA schedule data - tried everything - including reinstalling 7MC.  The data ends at 7pm tonight. That's the deadline for a new solution.  

In the USA, we have to pay for TV schedule data, sadly. In the long run, looks like buying a new [HDHR4]("https://www.silicondust.com/products/models/hdhr4-2us/") will provide schedule data AND a DLNA server for live TV.  Already use 2 HDHR3 tuners here. Love them! That's probably better than paying [Scheduled Direct]("http://www.schedulesdirect.org/") $25/yr.  Tried MythTV two prior times and failed. My Linux-fu must be too weak. Perhaps 1 more time?

I do not use the 1512 to record TV, so that isn't a helpful answer.
Yup I heard about that EPG problem with MCE
You may want keep eye out for HDHomeRun DVR Software
Some eles look forword to SageTV is goign to make  come back when it get open source as it work under Linux as well

---

