---
title: "T61 6457-4XU Sleep / Resume Fix"
date: 2008-06-23
forum: Hardware
---

### Post by blackmax on 2008-06-23
I wanted to share a configuration change I discovered that would allow sleep and resume to function correctly under Ubuntu 8.04 on the Lenovo T61 Type: 6457-4XU using the proprietary Nvidia (EnvyNG) video drivers.  This model T61 uses the Nvidia Quadro NVS 140M video card.

You need to go to the '/usr/share/hal/fdi/information/10freedesktop' folder and edit the file '20-video-quirk-pm-lenovo.fdi'

First make a copy of this file and name it something like '20-video-quirk-pm-lenovo.fdi.bak' so you can restore quickly if needed.

In this file you want to go down to the section that contains the prefix for the '6457' model of T61.  It looks like this by default:

```

 <!-- T61 (8895), intel card 32bit works with S3_MODE, but 64bit needs VBE_MODE 
           T61p (6460), does not work with the NVidia driver-->
      <match key="system.hardware.product" prefix_outof="6457;6460;6465">
        <merge key="power_management.quirk.s3_bios" type="bool">true</merge>
        <merge key="power_management.quirk.vbemode_restore" type="bool">true</merge>
      </match>

```

Edit it to look like this:

```

 <!-- T61 (8895), intel card 32bit works with S3_MODE, but 64bit needs VBE_MODE 
           T61p (6460), does not work with the NVidia driver-->
      <match key="system.hardware.product" prefix_outof="6465">
        <merge key="power_management.quirk.s3_bios" type="bool">true</merge>
        <merge key="power_management.quirk.vbemode_restore" type="bool">true</merge>
      </match>
      <match key="system.hardware.product" prefix_outof="6457;6460">
        <merge key="power_management.quirk.s3_mode" type="bool">true</merge>
        <merge key="power_management.quirk.s3_bios" type="bool">false</merge>
        <merge key="power_management.quirk.vbemode_restore" type="bool">true</merge>
        <merge key="power_management.quirk.save_pci" type="bool">true</merge>
      </match>

```

I've read that this configuration should also work for the T61 type 6460, so I've included this prefix along with the 6457 in this updated configuration.

Now I can successfully sleep and resume.  Sometimes I get a white screen on resume (which is something I'm still trying to debug), but if you blindly type in your password you will be brought back to your desktop successfully.

Hope this is helpful to someone.

---

