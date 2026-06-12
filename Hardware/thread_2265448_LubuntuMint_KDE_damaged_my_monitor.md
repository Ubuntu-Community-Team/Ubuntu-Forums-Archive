---
title: "Lubuntu/Mint KDE damaged my monitor"
date: 2015-02-15
forum: Hardware
---

### Post by q123q on 2015-02-15
Hi All,

I've been using Win XP for years, and I have no problems with my monitor(got it as new) ASUS VB198.
I used Lubuntu 14.04 LTS, and Mint 17.1 KDE from a live USB Stick for 1-2 hours.
After 1-2 hours, I smelled a stange smell coming from the top of my monitor. After the screen started irritating my eyes, on Lubuntu,and on Mint KDE too.
I went back my old Win XP, and the sceen colors has changed. Side areas on Youtube become a litte pink tinge. Facebook had the same.
After few days it changed back to it's original colors, but since the monitor burns my eyes.No flashing, of anything I can see, just my eyes are burning, and tired after few minutes of use my monitor.I was using this monitor on Win XP, and had no problems for years, till I used Lubuntu and Mint for 1-2 hours.
Looks its damaged my monitor.

What can I do? Apart from buying a new monitor.

Monitor: ASUS VB198
Motherboard: Gigabyte GA-G41M-ES2L 
Video card: ATI Radeon HD 4350

Thank you

---

### Post by TheFu on 2015-02-15
What connect is being used?  DVI, HDMI or something else? A digital connection isn't likely to harm anything. 
Initially, I'd chock this up to coincidence.

The last time a monitor was harmed by a properly working computer was the mid-1990s when all monitors added protection to prevent bogus inputs from harming them. In the early 1990s, it was possible for the X/Windows settings to send out-of-range values to a monitor through user error. If you've manually modified the xorg.conf file, I suppose that might still be possible or if the monitor isn't reporting the proper capabilities to the OS, it could happen ... maybe.

So - first questions ... 
* video connector type?
* what resolution and color depth is being used in XP vs Linux?

---

### Post by tgalati4 on 2015-02-15
I upgraded a client's computer from Windows Vista to Windows7 and shortly thereafter their monitor crapped out.  Of course, the computer and monitor were both 7 years old.  It happens.

How old was the monitor?

---

### Post by q123q on 2015-02-16
Hi TheFu,

the connection is VGA. I did not edit the xorg.conf, I was on a live session, from an USB stick. Ubuntu has,and had in the old version compatibility problems.I had a friend, he was an Ubuntu fan/guru(?) in 2006, but he couldn't manage to install Ubuntu on my Clevo laptop.The install process stopped. This is why I suspect Ubuntu, as a source of my damage. 
I got the monitor in January 2013, no problem since, but when I used Ubuntu distos it's got failed.
In Win XP I use it on the native resolution: 1280x1024 
60Hz
32 bit

On Linux, I didn't adjust anyhthing, becouse it was a live session, I kept the setting after boot up.It's looked 1280x1024

Thank you

---

### Post by q123q on 2015-02-16
Hi tgalati4,

got it in January 2013.

Thank you

---

### Post by q123q on 2015-02-16
I suspect an other thing: I built my desktop pc myself. Ubuntu might be using the motherboard chipset to define the vga driver. I could be that, this motherboard never been build with this ATI vga, and Ubuntu sets up a wrong configuration for it.

---

### Post by TheFu on 2015-02-16
Run the live-boot, open a terminal and run this program.
**xrandr**
Please copy/paste all the output back here. I suspect we'll see 1280x1024x32 ...
If possible, can you swap the VGA connection for any digital connection?  DVI/HDMI are good.

---

### Post by q123q on 2015-02-16
mint@mint:~ > xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA-0 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1280x720       75.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DIN disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)

---

### Post by q123q on 2015-02-16
I have no DVI or HDMI
I bought this monitor, becouse it has VGA connection only.

---

### Post by TheFu on 2015-02-16
I'm out of ideas. Those settings confirm it isn't being pushed beyond specs. Time for a new monitor?

I've been there - had a beautiful 24inch 1200p monitor die after only 5 yrs of use. Looked online and found that model had a common issue that was easily fixed with a new set of capacitors.  Opened it up and didn't see any blown caps - my issue was different. Decided time was short and ordered a replacement. Never looked back.

The specs on that monitor say 3 yr warranty here. Does that help you?

I think it is purely coincidence.

---

### Post by q123q on 2015-02-16
Thank you yo much for your help. I went down to my garage, and I was looking for the 3 years warranty card. I found a DVI cable, and now I got it in my mind, why I bought this monitor with VGA connection.Becouse I have only VGA output on the motherboard. The onboard VGA card failed few years ago,and I bought an ATI videocard. This card has DVI output,but I kept using the old VGA cable, and now, I connected my monitor using the DVI instead of the old VGA.
Will see how it's goes. After a few hours I must see,and feel the difference.I already can feel some improvement, hope my eyes will settle.

Thank you for pointing out the 3 years warranty.If still hurst my eyes I will ask for a refound, or swap. But I like this monitor, I want to keep it. Its not  a wide sceen one, becouse I don't like 16:9/16:10 ratio.

Seems a bit better at the moment.


Thank you for your help, great skills.

---

### Post by tgalati4 on 2015-02-16
Your display will look different using a 60 Hz refresh versus a 75 Hz refresh.  Most LCD displays use 60 Hz.  But try both and see which looks better.

---

### Post by q123q on 2015-02-18
Hi tgalati14,

I've used 75 Hz on Win XP, but that was a bit too much, colors were strange, like fixel errors in it.I've got back to 60 Hz.
Was it on 75 Hz on Linux? Becouse I saw 60 Hz there. "1280x1024      60.0*+   75.0" So, the last number is in use?

---

### Post by TheFu on 2015-02-18
**lxrandr** provides simpler access to the monitor settings on LXDE.

---

### Post by tgalati4 on 2015-02-18
Yes, I believe the 60* is the default value as reported from the monitor, so try 60Hz.  Your graphics card can provide up to 75Hz at that resolution, so with a different monitor (like a Sony Trinitron CRT), 75 Hz generally looks better.

---

