---
title: "Making Ubuntu 9.04, IBM ThinkPad T23 and a Logitech QuickCam(r) Communicate MP &quot;work&quot;"
date: 2009-10-17
forum: Hardware
---

### Post by BETATEST on 2009-10-17
This applies to the **Logitech QuickCam (r) Communicate MP (V-UCR45)** *and* **Logitech QuickCam (r) for Notebooks (V-UBS47)** web cameras.  I know this has been rehashed over and over (plus it's in the Webcam Ubuntu Help Thread), but someone searching the forums here may find this faster and useful.

Both of the webcams I use on my T23 are refurbished models from eBay and/or Overstock . com.  They were very inexpensive.  (Cheaper than Dirt Cheap.  Scrooge would be proud of me.)  But being refurbs ... they came with no pretty Logitech box, user manual, or driver CDs.  Just a plain plastic bag with the webcam model numbers stamped on it and the serial numbers blacked out on the devices.  Which was fine - the CDs contain only Windows drivers (which always seem to be outdated and you have download current ones from Logitech anyway).

Out of the box on Ubuntu 9.04, the LQC for Notebooks works only for Cheese Webcam Booth in 320x240.  (Higher Resolutions only produce squiggily video lines - much like what you used to see on scrambled pay for view adult video channels ...)  It doesn't work at all on Skype, Ekiga, or Camorama Webcam Viewer.  This is pretty much the same story with the LQC Communicate MP - except for Camorama all you get is a black video screen.  :mad:

No, your camera isn't the problem.  And neither is Ubuntu (in and of itself).  :)

The problem is default video system that was "upgraded to Video for Linux V4L2" in Ubuntu Intrepid and carried over into Jaunty (9.04).  The Logitech QuickCams just don't work with the video system V4L2 upgrade.  You need to install the older V4L video system in order for the webcams to work.  This is how to do it (thanks to everyone here on the forums who provided the information).

Step 1: Close any applications that could use a VIDEO device like a webcam.  Instant Messenegers, Web Browsers, Skype, etc.

Step 2: While still connected to the Internet ... open up a Terminal and enter 
             **sudo apt-get install ld.so.preload-manager**

Step 3: After that command completes, enter the following
             **sudo ld.so.preload-manager /usr/lib/libv4l/v4l1compat.so**

Step 4: Once everything has been downloaded and installed in Ubuntu, keep the Terminal open. We have to stop using V4L2 and regress back to video system V4L.  Enter the following in the Terminal
            ** gstreamer-properties**

Step 5:  At the **Mulimedia Systems Selector** dialog, select the **Video** tab.  In the ***Default Input*** section, for*** Plugin*** select the "**Video for Linux (v4l)**" option from the dropdown box.  Then click the CLOSE button.

This should give you a dev/video0  and a dev/audio1.  Now ... you can run Camorama, Skype, etc. with your Logitech QuickCam (r) Communicate MP (V-UCR45) or Logitech QuickCam (r) for Notebooks (V-UBS47) web camera.  Cheese Webcam Booth will still require you to run the webcams at 320x240 resolution.  

Unfortunately, users of the Logitech QuickCam (r) for Notebooks (V-UBS47) web camera will get an ugly green line at the bottom of their video output, but that's the drawback using the V-UBS47.  And the V-UBS47 also has a dark and grainy video quality.  The Logitech QuickCam (r) Communicate MP (V-UCR45) doesn't have this problem with it's RightLight auto correction. (If you have a QuickCam for Notebooks - I suggest going to eBay and picking up a cheap QuickCam Communicate MP refurb webcam for a couple bucks).

This worked for me on Ubuntu 9.04 and I and my T23 are happily video conferencing.  

As always, your mileage may vary.  :P  Good luck!

---

### Post by alabamatoy on 2010-01-31
I followed your instructions, and the video works (Thanks!), but no audio!  Any thoughts on that?  I have a Thinkpad R52 running Ubuntu 9.04 and a Logitech V-UCR45

---

