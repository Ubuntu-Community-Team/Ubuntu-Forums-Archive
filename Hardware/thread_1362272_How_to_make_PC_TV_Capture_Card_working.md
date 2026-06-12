---
title: "How to make PC TV Capture Card working"
date: 2009-12-22
forum: Hardware
---

### Post by deviprasad_k on 2009-12-22
Hi there,

I have installed UBUNTU a couple of days back and it is really rocking.:guitar:
Till now i had been using windows XP and UBUNTU is simply cool.
It had recognized almost all the hardware installed - like USB PC Webcam, Microphone, Wireless Card, but doesn't seem to recognize the PC TV Capture Card :(.

I am using the Intex PC TV Capture Card w/o FM.
lspci lists the following:

01:03.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
    Subsystem: Philips Semiconductors Device 0000
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (3750ns min, 9500ns max)
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at f8010000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

I have tvtime installed and when I try running tvtime it gives the following output:
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/deviprasad/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

Can someone let me know how to get the card up and running :P

Thanks in advance,
Deviprasad K

---

### Post by unmole on 2009-12-22
Try this

```
sudo update-pciids
```

That will update your pci.ids, and then do this

```
dmesg | grep saa7133
```

You will see a couple of lines of out put indicating that the driver is loaded. Now you need to install tvtime

```
sudo apt-get install tvtime
```

This links for further settings
[http://www.cyberciti.biz/tips/debian-ubuntu-linux-configure-pinnacle-pctv-tuner.html](http://www.cyberciti.biz/tips/debian-ubuntu-linux-configure-pinnacle-pctv-tuner.html)
[http://blog.prashanthellina.com/2008/03/23/watching-television-on-linux-setting-up-a-tv-tuner-card/](http://blog.prashanthellina.com/2008/03/23/watching-television-on-linux-setting-up-a-tv-tuner-card/)

---

### Post by deviprasad_k on 2009-12-23
I gave

sudo update-pciids and it gave the following output:

Downloaded daily snapshot dated     2009-11-23 03:15:02
------
then i gave

dmesg | grep saa7133 and it gave the following output:

[   11.248761] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002
------
then i gave
sudo apt-get install tvtime (i had installed tvtime already) and it gave the following output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
tvtime is already the newest version.
The following packages were automatically installed and are no longer required:
  libibtk0 netpbm libavifile-0.7c2 libnetpbm10 libqt3-mt libjpeg-progs libgatos0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 159 not upgraded.

-------

but when i try running 

tvtime & it gives the following output

[1] 2741
deviprasad@Ubuntu-Home-Computer:~$ Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/deviprasad/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.


[1]+  Exit 1                  tvtime

----
how to troubleshoot ? kindly help

---

### Post by unmole on 2009-12-23
Which graphic card are you using ? Can you get desktop effects to work (Hit alt+ctrl+right/left . Do you see arrow marks or two rectangles labled Desk1,2)

---

### Post by deviprasad_k on 2009-12-23
There is no seperate graphics card. I am using the on board display adapter.
I am able to get the desktop effects work and able to switch between Desks. 
 
I am using a **"Intex PC TV Capture Card w/o FM"** and this is not working with tvtime.
 
I am a novice to Ubuntu (or even linux for that matter).
Can you suggest some troubleshooting tips to get this up and running please?

---

### Post by deviprasad_k on 2009-12-25
Is there anyone who would be able to help me with the installation of the PC TV Capture Card.
 
Otherwise, I have to go back to Windows :lolflag:

---

### Post by deviprasad_k on 2010-01-06
Switching back to Windows...
 
Windows seems to be simpler and more user friendly in terms of installation and recognition of the hardware.....
 
):P

---

