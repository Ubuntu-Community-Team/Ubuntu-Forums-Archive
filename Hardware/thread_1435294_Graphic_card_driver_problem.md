---
title: "Graphic card driver problem"
date: 2010-03-21
forum: Hardware
---

### Post by thekillingjoke on 2010-03-21
I have an ASUS g51vx which has a NVIDIA GEFORCE GTX 260M CUDA 1gb graphics card. I have installed ubuntu 9.10 32bit using VMware player running from windows vista 64 bit.

I am quite a newbie when it comes to using linux. I tried to install drivers for my graphics card but none of them seem to be working. I tried to find the appropriate driver from the nvidia site but all of them gave an error like

You do not appear to have an NVIDIA GPU supported by the xxxx     
NVIDIA Linux graphics driver installed in this system. 

lspci did not list any NVIDIA graphic cards on my system. 
Why is it that the hardware is not being detected. The graphic card works because it is being detected on the windows platform I use. Does running it from a virtual box cause this problem?.

Best Regards,

---

### Post by Kruken on 2010-03-21
You need to use the graphics driver from vmware tools (included in your vmware installation). The drivers required are not those of you nvidia gfx card but those of the virtualized hardware by vmware.

---

### Post by a mad pigeon on 2010-03-21
I don't think you can install graphics drivers through VMware. I was emulating Ubuntu through VMware Player 3 for a while and it didn't report any proprietary drivers I could use. Although, VMware tools usually helps me, especially in Windows 98. Can't remember if there were any for Ubuntu...

---

### Post by thekillingjoke on 2010-03-21
Thank you kruken for replying!..

Are the graphic drivers installed by default in VMware player?..(I don't remember an option about graphic drivers while installing)..As I said before, O couldn't find the card among the hardware specified nor could I find its proprietary software under System>Admin>Hardware drivers.
Could you be more elaborate?..
How can I find drivers for the virtualized hardware as you said..
 sudo lshw -businfo gives display as:     SVGA II Adapter
lspci gives VA compatible controller SVGA II Adapter

Also I did try to use envyng to try to install but none of the options provided were compatible!..

Appreciate the help as always,

Best Regards,

---

### Post by thekillingjoke on 2010-03-21
I tried using sysinfo which list VGA compatible controller under the graphic card option!..
It does not detect the GPU connected!..
Do we have any commands other than (lspci or hardinfo) in order to view the hardware connected?..or rather make it detectable?..
appreciate the help anyone!..

Best Regards,

---

