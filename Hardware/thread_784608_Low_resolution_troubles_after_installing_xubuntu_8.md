---
title: "Low resolution troubles after installing xubuntu 8.04"
date: 2008-05-06
forum: Hardware
---

### Post by vlad.genie on 2008-05-06
I've installed Xubuntu 8.04 on my legacy desktop. Everything goes good, except low resolution (800x600) was set from first start and I can't find way to change this :(

Applications > ... > Display gives me only:
- Default (800x600)
- 640x480

My graphics card (Riva TNT) supports higher resolutions (up to 1280, but I'm interested in 1024). My monitor (MAG Innovision 786) supports them as well.

I've tried to do different steps to solve this out:

1. Running **sudo dpkg-reconfigure xserver-xorg**. I saw text-only configuration tool, where I told what keyboard I'm using. After that I saw GUI, where I choose my graphics card and monitor. Also I choose resolution (1024x768).

Anyway - after this wizard everything rolled back to hated 800x600.

2. Editing xorg.conf with text editor, adding different hacks to different parts of it - without results.

3. Installing NVidia drivers. I downloaded latest from NVidia site. Run xubuntu in 'recovery mode', than turned to 'root command line' (or something). After this I tried to launch installation with needed command, but drivers installator said:
- I have something improperly launched (like level 1 when it should be level 3), I said 'continue'
- They couldn't find something for my kernel, but try to compile it themselves
- Some kind of error, that I couldn't continue with installation

Right after this I seriously doubt if installing Ubuntu was good idea. My hardware is so old, that OS not supporting it 'from the box' is looking strange. To continue with mass adoption, Ubuntu should definitely rule out problems with graphics cards and WiFi.

Can somebody tell me, what should I do to make my desktop under Ubuntu understand, that I want to use 1024? I really stuck and need you help.

Thank you! :)

---

### Post by djs_uk on 2008-05-06
Have you tried using Ubuntu's ability to install proprietary drivers?  I recently did a clean install of Ubuntu 8.04 on my Lenovo T61.  When it first booted, the graphics were bad, DVDs played really badly, and the resolution was much lower than the screens native 1440x900.  But then clicking on Start | System | Administration | Hardware Drivers allowed me to install the proprietary Nvidia drivers with one click.  All problems were resolved.

Darren

---

### Post by vlad.genie on 2008-05-07
Darren,

I did steps "Start > System > Hardware drivers". Now I see "nvidia_legacy" line - it is exactly drivers I need.

They are "enabled", but "not in use". And I can't see a way to make them use. I tried to disable/enable/reboot, but this won't help.

Please tell me, how did you turned them on. Thank you!

---

### Post by vlad.genie on 2008-05-07
I've successfully installed NVidia "binary closed source" drivers. I used "Add programs" dialog to do so. When I chose "NVidia legacy driver". Right now it is "installed" and "in use".

BUT: resolution hasn't changed :( It is still low.

---

