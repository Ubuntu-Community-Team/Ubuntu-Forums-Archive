---
title: "Laptop Screen Resolutions"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by Sasayaki on 2005-04-11
I'm running a fresh install of Hoary on a Compaq Armada v300.

I'm trying to get this laptop to display 1024x768 resolution- I could get it do it in the dim, dark days of Windows just by setting the resolution to that.

However, in Ubuntu, I only have access to the 800x600 resolutions- anyone know how I can get access to 1024x768? I tried editing my XOrg conf, but something *wierd* happened whereby I could scroll my mouse off the 'screen' and it was... very strange.

Any ideas?

---

### Post by ChrisTheGeek on 2005-04-11
Have you installed the appropriate NVidia/ATI graphics drivers?  This fixed the problem for me on Warty.  You can find instructions for NVidia at:

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by Sasayaki on 2005-04-11
I don't know what video card the Armada v300 has... is it ATI/Nvidia?

---

### Post by ChrisTheGeek on 2005-04-12
Your system should tell you :) Have a look at the System Info program available from the menus.

---

### Post by lucus on 2005-05-01
i have the same problem with my toshiba tecra

---

### Post by Hieronymus on 2005-05-02
If your laptop has a Nvidia card try the following:

install nvidia-glx

do

```

gtf 1024 768 60

```

meaning " gtf res res hz"
this will give you an output looking like this:

```

  # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

```

now copy this output to your /etc/X11/xorg.conf under the section monitor like this:

```

Section "Monitor"
		Identifier	  "Generic Monitor"
		Option		  "DPMS"
		HorizSync	   30-67
		VertRefresh	 30-60
		Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

```

to get the correct horizsync and vert refresh do

```

gtf 1024 768 60 -v

```

now 
put the mode "1024x768_60.00" under the section "SCREEN" subsection "DISPLAY" and everything sould work fine.

grz Hieronymus

---

