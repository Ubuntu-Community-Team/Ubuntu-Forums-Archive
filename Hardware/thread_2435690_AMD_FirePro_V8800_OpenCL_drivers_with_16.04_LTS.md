---
title: "AMD FirePro V8800 OpenCL drivers with 16.04 LTS"
date: 2020-01-24
forum: Hardware
---

### Post by jtrial on 2020-01-24
I have an HP Z620 workstation which I use as a virtualization platform. Since this system is always powered on I decided I would contribute to the Distributed Net project. I have been using the Distributed Net CPU client for a while but recently decided I would try using an old FirePro V8800 I had laying around. I installed the card and everything is working perfectly as far as its originally intended purpose (i.e. being a virtualization platform).

However I am unable to use the OpenCL version of the client ([LEFT][COLOR=#000000][FONT=helvetica][AMD64/OpenCL], v2.9112.521[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]) [/FONT][/FONT][/COLOR][/LEFT]because OpenCL is not installed / configured. Off I went to AMDs web site where I located drivers for this GPU. Upon reading the instructions I learned support for these drivers ended with 14.04 LTS. Further research revealed AMD is has AMDGPU-Pro drivers available. Apparently these are vendor specific drivers for the open source AMDGPU drivers which ship with Linux.

I downloaded the AMDGPU-Pro drivers (version [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]17.40-492261) and followed the installation procedures. Upon restarting my system I received a dialog stating there was a problem with the resolution and I was presented with a number of options. One of which was to use the default configuration. I selected that option and the system then switch back to text mode with a message showing the disk was OK (I believe this was the last message displayed before the graphical display started) and then it just hangs there. I am able to SSH into the system so the OS is up and operational except for the GUI.

I reviewed the /var/log/Xorg log file and it appears the X-server is crashing (there is a core file written to the root directory). I thought maybe I don't have the correct drivers but all the research I've done returns me to the original, unsupported drivers (which ended in 14.04) or this version of the AMDGPU-Pro drivers. I don't actually need the AMD drivers, I'd just like to get OpenCL support working so I can use the GPU for Distributed Net.

Any suggestions? I'm not overly familiar with configuring the GUI so I don't know what I would need to provide (logs, versions, etc) to assist the forum. If you need something let me know and I'll provide it.

The system in question is a Z620 with dual 2.98GHz 8 core CPUs, 192GB RAM, 256GB Z-Turbo drive boot drive and 2TB spinner for storage. OS installation is pretty much stock with the addition of Virtual Box added to apt. The system did have a Quadro K600 GPU prior to installing the FirePro V8800.
[/FONT]

---

