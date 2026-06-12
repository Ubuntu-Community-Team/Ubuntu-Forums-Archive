---
title: "Override monitors EDID settings"
date: 2014-11-10
forum: Hardware
---

### Post by cj-peter on 2014-11-10
Made the switch to Linux last night so I am new. On windows I would have a program to override my primary monitors (CRT) settings to reach a higher refresh rate. My setup should be: Primary DVI-0: 1024 x 768 @140. Secondary DVI-1 1920 x 1080 @120. These are the settings I ran on my old windows configuration and I would like to learn how to do so on Linux. I am running Linux Mint 17, but seeing as its based on ubuntu (should be the same thing deep down?) this would be the best place to ask.

Here are some of my specs:
[http://pastie.org/9708896](http://pastie.org/9708896)

Here is what I have tried, to no avail:
[http://pastie.org/9708902](http://pastie.org/9708902)

Clearly simply selecting those paramaters isn't enough, I need to force them with some sort of magical command.

---

### Post by grahammechanical on 2014-11-10
I am a little confused by your description of your monitors as CRT. Cathode Ray Tube monitors were analogue devices. They did not have a EDID. That comes with digital monitors. I am wondering if you are using a DVI to VGA adapter to connect to CRT monitors. VGA cannot give the full range of resolutions even when connected to digital monitors.

Did you notice that your GLX Render is listed as Gallium 0.4. That tells me that you are using an open source video driver. There is a setting utility for open source video drivers. It is in System Settings and it is called Display Screen. 

If we install a proprietary video driver then as part of the installation of the driver we get a settings manager utility for that driver. You will find that in the Dash. Of course, I am talking about Ubuntu. I do not support Linux Mint. But the forum does have a section called Other OS Support and Projects with a sub section called Mint. That is a better place to have this post.

Regards.

---

