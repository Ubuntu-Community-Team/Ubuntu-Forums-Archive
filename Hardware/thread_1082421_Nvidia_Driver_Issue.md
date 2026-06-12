---
title: "Nvidia Driver Issue"
date: 2009-02-27
forum: Hardware
---

### Post by DesktopDefender on 2009-02-27
Hi Folks

I am new to linux and ubuntu, but I have a question about Nvidia drivers for a 8600GT

First I am trying to get this working using Sun VirtualBox on a windows machine, is this possible?

Anyway the highest resolution that I can get is 800X600 although my monitor can have 1440X990, is it possible that I might be able to get my screen resolution that high

If so how could I update the drivers

I did an update - no joy

Downloaded the linux files from the nvidia site, stopped my x window and tried to install the .run from the command line and that didn't work

Any ideas I would greatly appreciate

Thanks
DD

---

### Post by brokenLockpick on 2009-02-27
Is this a mainstream brand of monitor? I had a pair of Rosewill monitors that I could not get to be properly recognized by my 7800GT after days of frustration I connected them via VGA rather than DVI cable and the proper max resolution was immediately available. So far as I could tell, the signal (EDID I believe it's called) wasn't being sent properly over the DVI cable in a way that the nvidia drivers could interpret.

Edit: perhaps I didn't read your post carefully enough, from what limited virtual machine experience I've had the resolution is set for the emulated monitor in the virtual machine software generally

---

### Post by howefield on 2009-02-27
If I understand you right, you are trying to run Ubuntu as a guest in Virtualbox with windows as the host, and want to use the nvidia drivers in your Ubuntu guest ?

This cannot be done as the guest system will use drivers supplied by Virtualbox, if you haven't already done it, you should install guest additions, which will give you greater resolutions amongst other benefits.

---

### Post by DesktopDefender on 2009-03-02
Hi Folks,

Thanks for the replys, 
yes I am trying to get Ubuntu to be a guest OS using Sun Virtual Box on a windows(Vista) machine,

I tried to install the guest additions, by using the menu Device-Install Guest Additions in guest OS window

That didn't seem to do anything so I made a disc of the iso that I found in C:\Program Files\Sun\xVM VirtualBox, ran the disc and it installed to C:\Program Files\Sun\xVM VirtualBox Guest Additions the following files

15/05/2008  14:20            25,214 iexplore.ico
01/09/2008  11:59            26,582 netamd.inf
15/05/2008  14:20             9,136 pcntpci5.cat
15/05/2008  14:20            36,352 PCNTPCI5.sys
02/03/2009  20:38                51 Sun xVM VirtualBox Guest Additions.url
02/03/2009  21:54                 0 text.txt
17/12/2008  09:54            76,832 uninst.exe
17/12/2008  09:54            84,496 VBCoInst.dll
17/12/2008  09:54           662,032 VBoxControl.exe
17/12/2008  09:54            65,552 VBoxDisp.dll
17/12/2008  09:53           104,976 VBoxDrvInst.exe
17/12/2008  09:52           670,224 VBoxGINA.dll
17/12/2008  09:54             8,990 VBoxGuest.cat
17/12/2008  09:54             2,621 VBoxGuest.inf
17/12/2008  09:54            38,928 VBoxGuest.sys
17/12/2008  09:54             7,545 VBoxMouse.cat
17/12/2008  09:54             2,090 VBoxMouse.inf
17/12/2008  09:53            39,696 VBoxMouse.sys
17/12/2008  09:54         1,051,152 VBoxTray.exe
17/12/2008  09:54             8,082 VBoxVideo.cat
17/12/2008  09:54             2,816 VBoxVideo.inf
17/12/2008  09:54            58,192 VBoxVideo.sys
17/12/2008  09:54           625,103 VBoxWHQLFake.exe

I am still unable to update my screen resolution beyond 800x600,
Am I doing something wrong, If I partition my drive and install Ubuntu, will I be able to increase my screen resolution, 
The screen itself can support 1440x900

Thanks very much for your help and assistance
DD

---

### Post by hotweiss on 2009-03-03
See if this post doesn't help you:

[http://ubuntuforums.org/showpost.php?p=6495696&postcount=21](http://ubuntuforums.org/showpost.php?p=6495696&postcount=21)

Basically you have to uninstall your driver and reinstall it again. :)

---

