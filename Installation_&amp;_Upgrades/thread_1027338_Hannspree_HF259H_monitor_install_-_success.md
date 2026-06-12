---
title: "Hannspree HF259H monitor install - success"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by therneau on 2009-01-01
I purchased a new Hanspree monitor from Best Buy yesterday, $259 special, 24.6" LCD 1920x1080 resolution, and spent some time before I could get it to work at full resolution.  But with help from this forum and others I prevailed.  The final setup:
  Ubuntu 8.04 Hardy Heron
  Radeon 9600 graphics card (old but not ancient), DVI output jack
  GPL ati driver

The three last changes between doesn't work and success were:
  1. Changed from the proprietery flgrx driver to the ati one
  2. Added "virtual 1920 1080" to the display subsection, based on a post that said one may lose resolutions due to memory + overly large defaults
  3. Added the lines below to my xorg.conf, which came from get-edid.  Note that the get-edid program complains that the EDID file it is reading does not look right and is 'likely invalid'.

Which of the 3 was responsible for success I don't know, but thought that the xorg file might be useful to others.  The only glitch wrt to the 19" CRT it replaces is that the screen is blank during bootup, i.e., I see the grub messages, but then nothing more until the login screen. 
  I had no success using any of the point&click tools; had to fix up /etc/X11/xorg.conf and reboot. 
  After turning the brightness down to 60 (default was 100) I am quite pleased with the image quality.  
          Terry T

output of get-edid | parse-edid  (less warning messages)
        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:ff
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "HF259"
        VendorName "HSD"
        ModelName "HF259"
        # Block type: 2:0 3:ff
        # Block type: 2:0 3:fd
        HorizSync 24-75
        VertRefresh 56-70
        # Max dot clock (video bandwidth) 140 MHz
        # Block type: 2:0 3:fc
        # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

        Mode    "1920x1080"     # vfreq 59.934Hz, hfreq 66.587kHz
                DotClock        138.500000
                HTimings        1920 1968 2000 2080
                VTimings        1080 1083 1088 1111
                Flags   "-HSync" "+VSync"
        EndMode
        # Block type: 2:0 3:ff
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc

---

