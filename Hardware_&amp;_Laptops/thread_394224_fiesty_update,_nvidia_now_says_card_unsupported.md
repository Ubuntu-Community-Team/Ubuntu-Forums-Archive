---
title: "fiesty update, nvidia now says card unsupported"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by Verbunk on 2007-03-26
Hi Guys,

    Maybe this question has been beat to death, here goes anyhoo. 

   I have a Dell Latitude C840 that has received a video card upgrade to a Quadro4 700 GO. 

  Yesterday everything was hunky-dorey, no problems (except a residual rt61 driver problem, but that's another story). Today after an update and reboot into new kernel the Xorg log is telling me the nvidia driver refuses to load b/c my driver is 'unsupported'. I saw that it was also upgraded during today's fiesty update but I'm not sure if it was truly updating versions or simply reinstalling b/c of the kernel update. 
     I know that under windows one needs to DL drivers with modified inf files (simply add the name of your card in the list of supported cards) to get it to work, is there something similiar to force this? As of today, Nvidia's website doesn't mention this card as being unsupported so I think they just don't want to support Dell's laptop card.

I have confirmed that the driver does load with a $> sudo modprobe nvidia , just when you startx it bails and complains that it's unsupported.

   If there is no known way to force the driver, how do I try different (past) driver versions?


 Any help is very appreciated!

 -J

## Relevant Xorg.log clip ##

(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(WW) NVIDIA(0): The NVIDIA Quadro4 700 GoGL GPU installed in this system is
(WW) NVIDIA(0):     supported through the NVIDIA 1.0-96xx Legacy drivers.
(WW) NVIDIA(0):     Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for
(WW) NVIDIA(0):     more information.  The 1.0-9755 NVIDIA driver will ignore
(WW) NVIDIA(0):     this GPU.  Continuing probe...
(EE) No devices detected.


## Relevant Xorg clip ##

Section "Device"
    Identifier     "nVidia Corporation NV28GLM [Quadro4 700 GoGL]"
    Driver         "nvidia"
    Option         "NvAGP"                 "1"
    Option         "UseEDID"               "True"
    Option         "AddARGBGLXVisuals"     "True"
    Option         "DamageEvents"          "True"
    Option         "RenderAccel"           "True"
    Option         "TripleBuffer"          "True"
    Option         "UseEvents"             "True"
    Option         "Coolbits"              "1"
    Option         "NoLogo"                "True"
    Option         "Mobile"                "1"
    Option         "UBB"                   "True"
    Option         "Overlay"               "True"
    Option         "RandRRotation"         "True"

    Option         "HWCursor"              "True"
    Option         "CursorShadow"          "True"
    Option         "CursorShadowAlpha"     "64"
    Option         "CursorShadowXOffset"   "4"
    Option         "CursorShadowYOffset"   "4"

    Option         "TVStandard"            "NTSC"
    Option         "TVOutFormat"           "SVIDEO"
    Option         "TVOverScan"            "0.0"
EndSection

---

### Post by Verbunk on 2007-03-26
ok, I see there is some discussion about this here

[http://www.ubuntuforums.org/showthread.php?t=393748&highlight=9755+9631](http://www.ubuntuforums.org/showthread.php?t=393748&highlight=9755+9631)

If anyone has the command line way to downgrade it would still be helpful!


         -J

---

