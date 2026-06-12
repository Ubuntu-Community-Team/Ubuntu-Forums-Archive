---
title: "Nvidia 8600 to display in 1080p"
date: 2009-05-10
forum: Hardware
---

### Post by TheKeyMaker on 2009-05-10
Just to start off I am new to working with X and setting it up...

That being said, I have recently percussed a 32” 1920x1080 1080p LCD TV

I have it connected to my computer via a DVI to HDMI Cable

In my computer I have a Nvidia 8600 GTS 

I also have the 180.44 Nvidia driver installed and am running Ubuntu 9.04


So here is my problem...

When I boot into ubuntu it displays on the TV in 1080i

I would like to have it look better by getting it to 1080**p**

I have read some forms that have said that you can force it to display in 1080p

If this is possible or if there is any way to make my viewing experience better please let me know


 Thank you in advance for any help!!!

---

### Post by Blackkitten on 2009-05-22
I have the same problem!
Did you managed to find a solution?

---

### Post by TheKeyMaker on 2009-05-27
No I'm still trying to find out myself. If anyone has any information please post it!!!

---

### Post by garretwp on 2009-06-01
I was having the same problems with my Mitsubishi 52in DLP. I have my HTPC connected to my stereo receiver via hdmi to get hdmi audio and video. The computer would only output to 1080i on the tv. If I had the computer connected directly to the TV, it would output to 1080p. I followed a post here on the forums: [http://ubuntuforums.org/showthread.php?t=1003099&page=2](http://ubuntuforums.org/showthread.php?t=1003099&page=2)

I followed the part to kill the xserver and load up X to output the display data to a log file. I than parsed the log file to get the proper resolution settings to put in my xorg.conf file. If you follow the instructions posted above, you may very well be able to get the tv to output to 1080p. This solved my problem.

I hope this helps,

- Garrett

---

### Post by TheKeyMaker on 2009-06-09
Here was my problem...

In the nvidia setting gui
There is a section in one of the last tabs called flat panel scaling..
In the box there is something that says Force full GPU scaling.
I had that checked, but once I unchecked it set my display to 1080 60p
:p :p :p

Hope this helps someone!!!

---

