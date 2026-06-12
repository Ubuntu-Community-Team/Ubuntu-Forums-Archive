---
title: "Same machine, different problems  -  Openchrome on Amilo La1703 (K8M890) Vol II"
date: 2011-08-14
forum: Hardware
---

### Post by jadabra on 2011-08-14
*[Note: See also [[COLOR="DarkRed"]this earlier thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1813096&highlight=1703") by CosSin, who as mentioned has different problems with the same model]*

After a few years in Windows World, I am again poking my nose into Linux land, and unfortunately, as happened before, hit a wall right away. I would consider myself something like an intermediate newbie, who can find and figure out and understand some stuff, but not all that much.
**Any help will be very much appreciated!**

I helped a friend set up her new (Windows) laptop, and ended up getting her old one - a Fujitsu Siemens Amilo La1703 with VIA K8M890CE/K8N890CE (Chrome9) graphics - which is in good working condition except for the half-broken display lighting. I want to use it as backup machine with an external monitor.

Out goes Vista, and in comes ... first Xubuntu, then Ubuntu, last Lubuntu, which I am sitting in front of right now. The following applies to all, afaik.

EDIT: I used the 11.04 Live Versions from CD or USB Key.


**So now to the problem at hand ...**

The openchrome driver is not active. Unlike the user mentioned above, I get a working system, be it from Live CD or HD, but apparently with a generic video driver, i.e. no acceleration.


Some observations:

[LIST]
[*]Oddly, openchrome seems all over the "Xorg.0.log", correctly detecting the maximum resolutions of both the laptop (1280x800) and external monitor (1280x1024), but apparently quietly quitting at some point for a reason unclear to me.

[*]I get a "compromise" resolution of 1024x768 on both displays, which is not terrible but far from optimal.

[*]If I unplug the external monitor during startup, the built-in display will end up running at its native 1280x800, though still without the openchrome driver.

[*]Ubuntu's monitor management app shows only 1 monitor, although 2 are connected, and all configuration options are greyed out (except further  reducing the resolution). Setting the monitors up as clones or extensions and at their different native resolutions worked on Vista btw, so it's not impossible on principle because of some hardware incompatibility or such.

[*]Lubuntu is the first -buntu variant that gives me a mouse pointer on **both** displays, not just on the (most-of-the-time-broken) built-in one.

[*]"sudo lshw -c display" returns (on Lubuntu, but was the same on the others, I think):
```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: K8M890CE/K8N890CE [Chrome 9]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=64 mingnt=2
       resources: memory:c0000000-cfffffff memory:d8000000-d8ffffff
```

[*]"xrandr" returns (on Lubuntu, but was the same on the others, I think):
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 400, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       75.0*    70.0     60.0  
   1024x600       59.0  
   1024x576       60.0  
   1024x512       60.0  
   832x624        75.0  
   800x600        75.0     72.0     60.0     56.0  
   720x576        60.0  
   856x480        60.0  
   848x480        60.0  
   800x480        60.0  
   720x480        60.0  
   640x480        75.0     73.0     67.0     60.0  
   720x400        70.0
```

[*]**Really weird** and possibly unrelated random discovery:
Starting a video in a player (I tried Parole and VLC) and then right-clicking on the video crashes & restarts the X server 100% of the time. I got the same result by trying to (left-)click on a player menu, but I am not sure about the 100% here.[/LIST]

I am going to attach 2 versions of the Xorg.0.log file as zips:
[COLOR="DarkRed"]"Xorg.0.log_ext+int.txt"[/COLOR] is from a startup with external monitor attached, and
[COLOR="DarkRed"]"Xorg.0.log_int.txt"[/COLOR] from a try with the external monitor unplugged.

Many thanks in advance to anyone who looks at this stuff and tries to figure out what is going wrong!
If you need more detailed information, I'd love to supply it. Thanks!

---

### Post by jadabra on 2011-08-16
Some new details

I learned from the **openchrome** website that their driver is **not dual-head-capable**, which I understand means that my intended setup (internal + external monitor) will not work.

That could explain why openchrome does not load in this setup. Do I understand that right?

2 questions remain for me:

1) Why doesn't it load if I don't attach the external display? I even set the display to LCD only in the BIOS (options are LCD, LCD+CRT and CRT) so as to avoid confusion about how many displays there are. I also specifically directed the X server to load openchrome in the xorg.conf, but the display device still turns out "UNCLAIMED" in the "lshw -c display" output (see above).
It would be interesting to see if there is a way to make this work, however as mentioned the internal display does not work reliably, so the other important question is ...

2) Bearing in mind that openchrome is not dual-display-capable, is there a way to make it appear to the driver as though the external monitor is the only one present? I tried the "CRT only" setting in the BIOS, which leaves the internal display completely black, but the Xorg.0.log still appears to show that the internal display is detected and a compromise resolution is chosen that fits both displays. No sign of a succesfully loaded openchrome in this setup also, which would be the first part of the problem.

Any suggestions?

---

### Post by bantuvez on 2011-10-08
Hi,

My family is switching from windows to ubuntu (at least on our laptops.) So a few days ago I installed Ubuntu 11.04 on three laptops. I have a Toshiba notebook which I think is working pretty fine with Natty. The other two notebooks are from Fujitsu-Siemens: an AMILO Li1705 and an AMILO La1703. With these two machines we have exactly the same problem as the first poster:

"Starting a video in a player (I tried Parole and VLC) and then  right-clicking on the video crashes & restarts the X server 100% of  the time. I got the same result by trying to (left-)click on a player  menu, but I am not sure about the 100% here."

The AMILO Li1705 and the La1703 has the same video card (Chrome 9 HC), so I think this is definitely a driver problem. As I mentioned both machines run a fresh install of Ubuntu 11.04. After googling a few hours I couldn't find any solutions for this problem. 

I don't want to run the unity interface on the notebooks nor I want 3D acceleration, cause I think the hardware (Chrome 9 HC) can't handle that. But it's really weird that I can't change the size of the playing video. Hope someone can help here.

---

### Post by bantuvez on 2011-10-10
Okay. I've found a workaround. At least now with VLC it's possible to resize the playing video or right-click on it without the crash of the X server. So I've set VLC as the default media player on the AMILOs until someone can figure this out.  I will post a Xorg.conf and a Xorg.0.log file when I have some time. I hope someone can help to find the real solution for this problem.

---

