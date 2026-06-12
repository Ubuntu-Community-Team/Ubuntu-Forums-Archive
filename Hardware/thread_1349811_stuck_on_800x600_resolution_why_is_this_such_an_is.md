---
title: "stuck on 800x600 resolution why is this such an issue?"
date: 2009-12-08
forum: Hardware
---

### Post by lhodgins on 2009-12-08
Hi there everyone, can anyone *genuinely[I]help?  I love ubuntu, but cannot use due to intel 815 graphic issues.  i only get 600x800 resolution.  i install other non ubuntu distro's and i get my full 1024x768 resolution.  Looking at all posts this seems to be a massive issue with ubuntu, some things we can live with but poor resolution is something that is difficult for most.  why is it that for example this is not a problem on Mandriva for example, but an issue with all ubuntu flavours.  if this was solved this would be the perfect OS, I have search tried hundreds of solutions spent a day looking through forums but nothing that [I]really*works. Thank you one an all!:?

---

### Post by gewitty on 2009-12-08
Can't give you a definitive answer, but having had similar problems with my NVIDIA graphics and display I found that the two key elements were having the right graphics driver installed (which may already be there in Ubuntu. Someone else might confirm this) and making sure that your display screen is properly recognised.

I bought a new Edge10 screen a while back and it was stuck at a very low resolution (640x480). I eventually discovered that the EDID information was not being passed from the display to the graphics driver and had to modify the Xorg.conf file to force the graphics to use a stored version of the EDID file which I got from the manufacturer.

If you haven't checked it already, take a look at the display information in System/Admin and see if it names your screen correctly, or just shows it as unrecognised. If it's unrecognised, that's probably your problem.

Unfortunately, I have no idea of what you need to do to the Xorg.conf file when using an Intel graphics chipset. There's a bit more info available at [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760), which might be of use.

Good luck!

---

### Post by lidex on 2009-12-08
Please post terminal output of this command:
```
sudo lshw -C display
```
You can find a terminal in Accessories menu.

---

### Post by lidex on 2009-12-08
Info here:
[http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html]("http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html")
[http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/]("http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/")
[http://intellinuxgraphics.org/]("http://intellinuxgraphics.org/")

---

### Post by lhodgins on 2009-12-09
*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82815 Chipset Graphics Controller (CGC)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 11
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-fbffffff(prefetchable) memory:f4000000-f407fff

as requested thank you all for your time the display unclaimed bit at the top seems to me the layman like an issue?

Once again i appreciate your help

---

### Post by lidex on 2009-12-11
Read this carefully and implement: [http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html]("http://www.webupd8.org/2009/06/new-ubuntu-intel-graphics-drivers.html") Then reboot and run this command: ```
lshw -C display
```

---

### Post by mikewhatever on 2009-12-11
> **lhodgins said:**
> Hi there everyone, can anyone *genuinely[I]help?  I love ubuntu, but cannot use due to intel 815 graphic issues.  i only get 600x800 resolution.  i install other non ubuntu distro's and i get my full 1024x768 resolution.  Looking at all posts this seems to be a massive issue with ubuntu, some things we can live with but poor resolution is something that is difficult for most.  why is it that for example this is not a problem on Mandriva for example, but an issue with all ubuntu flavours.  if this was solved this would be the perfect OS, I have search tried hundreds of solutions spent a day looking through forums but nothing that [I]really*works. Thank you one an all!:?

Are you on Hardy Heron, as the info in your profile suggests? If so, can you check if 915resolution package is installed and post the output of the following:

xrandr -q

cvt 1024 768

I don't know the answers to the highly philosophical questions about 'a massive issue' and the relation to Mandriva. Sorry about that.

---

### Post by lhodgins on 2009-12-11
Hey guy's it's great to see loads of genuinely decent folk pulling together to help out.  i am truely grateful.  I have fixed my issue by following this:

[http://ubuntuforums.org/showthread.php?t=998642&highlight=815](http://ubuntuforums.org/showthread.php?t=998642&highlight=815)

i created the xorg file. restarted the computer kicked off a bit, wouldn't load so i tried to fix it by using xterm on startup, to delete what i did, couldn't do it so booted in safe mode, changed the res in the disply properties (which now had my res as an option) restarted in normal mode, and since then all OK!!! don't ask me how this happened! but it went from not booting to working perfectly fine.  thanks one and all

---

### Post by mikewhatever on 2009-12-11
Interesting solution, thanks for updating.

---

