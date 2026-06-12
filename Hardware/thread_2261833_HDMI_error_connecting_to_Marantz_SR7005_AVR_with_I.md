---
title: "HDMI error connecting to Marantz SR7005 AVR with Intel HD graphics"
date: 2015-01-21
forum: Hardware
---

### Post by LeeC22 on 2015-01-21
I have just built my system as a Steam streaming client. It is based on Ubuntu 14.04 with the added libva packages to enable the hardware decoding on the Intel HD GPU. The motherboard is the MSI J1800I.

Everything was fine when I was connecting to a monitor via VGA, everything is fine when I connect direct to my TV with HDMI, but when I connect to my AVR, I get a black screen until I switch to a different input, then back to my computer. When I switch back, there is an error dialog on the screen, as shown in the attachment.

When I run the xrandr command, I get:

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767 
VGA1 disconnected (normal left inverted right x axis y axis) 
HDMI1 disconnected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm 
DP1 disconnected (normal left inverted right x axis y axis) 
HDMI2 disconnected (normal left inverted right x axis y axis) 
DP2 disconnected (normal left inverted right x axis y axis) 
VIRTUAL1 disconnected (normal left inverted right x axis y axis) 
  1920x1080 (0xad)  148.5MHz 
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz 
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz

This is pretty much my first serious Linux setup and the first time I have had this kind of problem. I used to connect my windows based server to this AVR but that detected with no problems. I'm not quite sure where I should be focussing my attention to solve the problem, so would appreciate any pointers.

Edit: I have just noticed, when it boots up, I also get the following lines... or something similar, they're not on screen long.

Error: No Video Mode found
Error: Booting in blind mode

---

### Post by LeeC22 on 2015-01-22
So after hours of searching, searching and more searching, I am getting nowhere. So I took the radical (yet seemingly mandatory with Linux) option of reinstalling everything again. But to try and minimise all problem sources, I connected to my AVR to do the full install. However, it appears that I can't even do that. The minute I select any option in the install option screen, I get the "No suitable video mode found" and "Booting in blind mode" errors... so I can't even see to install the OS. I can't run any of the Boot-Repair options, because I can't see anything on screen. I have no idea how to fix the problem, when I can't see any output.

I presume I have either asked a too-frequently asked question, or one that nobody knows how to solve, or perhaps doesn't want to solve. Unfortunately, I am at the mercy of the community, so what do I need to do, to get the help of this community? I must be doing something wrong, to get 130+ views and no response...

Does this help? $sudo apt-get install community-help

---

### Post by LeeC22 on 2015-01-23
I have spent several more hours trying to work out what the problem is myself... not an easy task for an inexperienced Linux user.

So I found some info on Grub, and some commands that could identify video information. So I booted up my Ubuntu 14.04 USB, hit 'c' at the install option screen to go into Grub. Typed "videoinfo" and got the result shown in the second attachment.

I presume that if the system is not getting any video mode information at the absolute basic level, then my other problems are to be expected. In windows, the system would just kick in a set of generic display options, but things are not quite so simple in Linux (to us noobs anyway). I certainly can't understand how an OS can believe a connection is "disconnected" yet still manage to display an image on it... it doesn't make any sense. If you look at the first attachment, you can see what I mean, it thinks there is no monitor. So as a result, I'm not sure what my next course of action should be.

Up to now, I have installed Ubuntu 14.04, then SteamOS, then OpenElec, then Ubuntu 14.04 again, followed by SteamOS (again) Kubuntu 12.04, Ubuntu 12.04 and finally Ubuntu 14.04 again. I just wonder if getting the screen to display is such a major issue, what lies in store if/when the system is up and running. All I know is that reinstalling OS after OS after OS, and having the same problem in every single one, is debilitating to say the least.

Am I asking about a problem that would be better suited to another forum, i.e. not ubuntuforums.org?

---

### Post by LeeC22 on 2015-01-25
3 days, 160 views, no replies... an unfortunate replication of my previous attempts to gain any kind of support with Linux related matters. I know it's a real inconvenience when new users have problems, but unfortunately, archaic, user-unfriendly operating systems are going to create problems for people. As someone who spent over 20 years in a position to help, support and advise people, I find it quite sad when people aren't prepared to chip in. To be honest, I place some of the blame in the hands of the Ubuntu creators, especially after a page I read to day regarding their X/Monitor detection tools. I quote a section from it...

> There are two general reasons the tools fail. 

One reason is if the user's hardware setup falls outside the tools' design parameters. For example, they may be used on a hardware platform the given tool has not been ported to. Or the user has multiple video cards, or has hot-swapped an external monitor or projector onto their laptop. 

The second reason is that the user's hardware is bad. This is unfortunately common. Older monitors may not support DDC. Some monitors are buggy and give bad data. Adapters or KVMs may corrupt the data from the monitor before it reaches the card. The card may corrupt things or fail to pass things along properly. Or the card or monitor may simply lie and give incorrect values.

It's like "Our tools don't work properly, but it's still your fault when they don't.". Speaking as an experienced software developer, you __**must** take ownership for the failings of your own software.  Later they say:

> For addressing the symptom of mis-detection, a GUI config tool displayconfig-gtk is to be used.

...but they removed that tool. I struggle to comprehend how you can admit your tools have problems, have a tool that can help fix those problems, and then remove it, offering nothing to replace it apart from manual configuration file editing. :mad:

As much as Linux is the ideal platform for the machine I have built, I really can't afford to wade through page after page of archaic suggestion using methods we left behind in the 90's. I refer of course, to convoluted command line solutions, to complex configuration problems. I shouldn't have to load up tools that read EDID information, just so that I can manually edit a .conf file. This is made even more difficult, when those tools return EDID information full of zeroes. I borrowed a laptop with Windows 8 installed, loaded up Monitor Asset Manager, and immediately got a complete EDID report from the exact same device the Linux tools got nothing from. When good hardware returns bad results, then the software used has to be the fault. As much as the Ubuntu creators might want to deny it, Ubuntu has a problem. Display auto-detection either has to work 100% of the time, or they have to provide an adequate UI tools, to let users fix the OS faults. If they can't get that simple, fundamental aspect right, then they are on the back foot from the start.

Anyway, I have edited the title of the thread (I hope), I will also ask the mods to lock this thread and to delete my account. I apologise if my question has forced anyone to read about something they don't care about. I would **sudo apt-get remove community-help**. but it would seem that my attempted installation failed anyway, so there's nothing to remove. Perhaps an update of the help package is required... ;)

P.s. I have also removed my subscription from the thread, as I suspect the only responses this will get now are the usual "If it's too much effort, use Windows...". I don't have time to get involved in that level of discussion, I use what works, that's an ingrained philosophy built on 30 years of using/creating professional grade tools... that __**do** work.

---

### Post by howefield on 2015-01-25
Thread closed at OP request.

---

### Post by coffeecat on 2015-01-25
Just to add as a point of information for others coming across this, since it is a common cause of misunderstanding...

> **LeeC22 said:**
> 3 days, 160 views, no replies...

Of the 160 views, only 11 were from forum members, none of whom it seemed felt able to comment. The other over 100 views were from spiders (googlebots and the like) and guests to the forum, none of whom can post. The vbulletin software counts all in its view count.

---

