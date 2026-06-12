---
title: "HOWTO - Samsung Syncmaster 2443BW + fglrx"
date: 2009-10-25
forum: Hardware
---

### Post by realn on 2009-10-25
Hi,

Configuration:
- Kubuntu HH
- ATI HD3200 + fglrx
- Samsung SyncMaster 2443BW

Problem: 
 After an aticonfig --initial --input=/etc/X11/xorg.conf I got the fglrx driver installed. However , the screen resolution was awful : 1024x768
 Unacceptable, since the screen has a max of 1920x1200@60Hz.

Resolution:
 1) used command "gtf 1920 1200 60" to calculate the modeline:
  # 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
  Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync

 2) added the previous line into the xorg.conf in the monitor section:

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
        Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
EndSection

Still, the image was not crisp, I tried to adjust the monitor, coarseness, etc., still not acceptable

3) Removed (commented out) the Modeline line and added two following lines instead ( I even don't remember where I got them from)

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
#        Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
	HorizSync	30-85
	VertRefresh	50-160
EndSection

Result: crystal clear image. You might need an auto adjust at the end of step 2 and 3.
Note: I forgot to mention that I'm using VGA input on the screen.
 Anyway, I hope it helps someone.

---

### Post by realn on 2010-07-20
Marked as solved.

---

