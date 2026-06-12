---
title: "NVIDIA Quadro NVS 110M on Dell Latitude D820"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by ph0b05 on 2007-04-19
Hi,

I installed Feisty earlier today on my new D820 laptop and I'm the most impressed I have ever been with a Linux Distro. It pretty much got everything out of the box. I have an ATI x1800XT on a desktop machine and resorted to never getting that to work. So when I purchased my laptop I wanted one with an nVidia card so I could get something like Beryl running.

Once again I'm without my eye candy desktop features and 3D acceleration. I noticed that Feisty has this "Restricted Driver Manager" applet. In mine I have my Wireless Card and Nvidia card listed. The wireless card is enabled and "in use" by default, but the graphics card is not enabled. So when I try and enable it I am presented with the "Enable the driver?" dialog and I click "Enable Driver". The computer thinks for about 1 - 2 seconds and hands me back to the list, where the graphics card is still not enabled.

I am still running Mesa GLX Indirect mode (which is giving me my widescreen 1680 x 1050 resolution, but nothing more).

I would really appreciate any help you can give me, as I feel I am months now trying to get this stuff working with my ATI card on my desktop, and now that I have another nvidia machine (with a card that "IS" supported, allegedly), I am frustrated that still nothing works.

A big pat on the back to any of you that can help me get this working.

---

### Post by ph0b05 on 2007-04-21
**I got it working!!**

Just as a follow up. I did the following

sudo apt-get install nvidia-glx-new

changed the driver line in my xorg.conf file from "nv" from "nvidia"

When I rebooted and logged in, the Restricted Driver Manager popped up to tell me that it had loaded a restricted driver. When I opened the dialog I could see that my card was now "enabled"

When I did a "glxinfo | grep rendering" I could see that direct rendering was enabled.

I then simply "apt-get install beryl emerald-themes".

When I got that far I noticed that I had 3D desktop effects using beryl, but the title bars on all windows disappeared and 3D cube rotation didn't work either.

To fix that I changed the default colour depth from 16 to 24 (bit).

Once rebooted everything works perfectly ;) 

Hope this is of help.

---

### Post by falstaff on 2007-04-23
I've got the same Laptop, and all works fine (beryl, desktop effects...)

I've basicly applied the xorg.conf from [http://www.ailis.de/~k/docs/delld820/]("http://www.ailis.de/~k/docs/delld820/"). But you don't have to install the nvidia driver by hand, just aptitude install nvidia-glx-new... 

If it still doesn't works, post your xorg.conf (located in /etc/X11/xorg.conf)...

I had another two bugs with beryl <=> nvidia <=> Latitude D820: Black windows after i opened a few windows, and black screen after i switchet to a virtual terminal and back to x... I will post the solutions later, i don't know the options by heart...

good luck.. cya 
falstaff

---

### Post by kingfisher on 2007-04-23
> **falstaff said:**
> 
I had another two bugs with beryl <=> nvidia <=> Latitude D820: Black windows after i opened a few windows, and black screen after i switchet to a virtual terminal and back to x... I will post the solutions later, i don't know the options by heart...


I've a D620, video card is pretty much the same, it has just half of the video RAM. I'm experiencing the black window but too, so I would be very interested in how you solved this problem.

Thanks,

  Christian

---

### Post by falstaff on 2007-04-23
Hello,

Here are the solutions:
Black window bug: Its because beryl tries to save the window content in video ram. When the card is running out of ram, the window is black. The solution:
- Right click on the Beryl manager tray icon
- => Advanced beryl options
- => Rendering Path
- Copy

The other bug is a problem with the nvidia drivers. It cant sync after the switch from virtual terminal and back. Three settings in the Beryl settings manager solves the problem:
- Under "General Options" => "General Options" 
- Disable "Detect Refresh Rate"
- Disable "Sync to VBlank"
- Set "Refresh Rate" to 60-100 fps...

Bye
falstaff

---

### Post by zeddock on 2007-04-25
> **falstaff said:**
> Hello,

Here are the solutions:
Black window bug: Its because beryl tries to save the window content in video ram. When the card is running out of ram, the window is black. The solution:
- Right click on the Beryl manager tray icon
- => Advanced beryl options
- => Rendering Path
- Copy

The other bug is a problem with the nvidia drivers. It cant sync after the switch from virtual terminal and back. Three settings in the Beryl settings manager solves the problem:
- Under "General Options" => "General Options" 
- Disable "Detect Refresh Rate"
- Disable "Sync to VBlank"
- Set "Refresh Rate" to 60-100 fps...

Bye
falstaff

I am running on a Dell Latitude D800, with nVidia GeForce Go 4200 Ti AGP8
When I turn on Desktop Effects in Feisty (release) I get black windows when too many are open.  Do you think this is the same thing as you are experiencing?

If so, what would be the fixes for me?  In a standard install I do not see the Beryl Settings at all.  I can get into nvidia-config. But I am a newb to ubuntu and linux so please be kind and full of GUI! <wink>

Thanx,

Zeddock
PS. Is there a bug in launchpad for this? I could not find any.

---

### Post by Basz on 2007-04-26
Believe it or not, but this thread solved all my problems i had with resuming from standby :) Thanks a lot.

---

### Post by aneas on 2007-05-16
> **falstaff said:**
> Hello,

Here are the solutions:
Black window bug: Its because beryl tries to save the window content in video ram. When the card is running out of ram, the window is black. The solution:
- Right click on the Beryl manager tray icon
- => Advanced beryl options
- => Rendering Path
- Copy

The other bug is a problem with the nvidia drivers. It cant sync after the switch from virtual terminal and back. Three settings in the Beryl settings manager solves the problem:
- Under "General Options" => "General Options" 
- Disable "Detect Refresh Rate"
- Disable "Sync to VBlank"
- Set "Refresh Rate" to 60-100 fps...

Bye
falstaff

Is this something that could be applied to compiz settings too, does anyone know? Or do I have to install beryl?

---

