---
title: "Can't change to 1024x768 resolution after installing nVidia driver"
date: 2009-12-21
forum: Hardware
---

### Post by rectec794613 on 2009-12-21
I recently installed a proprietary driver from Hardware Drivers and restarted. Now my resolution is at 640x480 and I can't change it back to 1024x768. My GPU is an nVidia GeForce 8400GS. What do I do now? Is there any way to uninstall them? Where do I get working drivers? I have a driver from the official site and whenever I run it, it tells me to exit X server. When I exit I can't remember the code to run the .run file.

Currently the driver is uninstalled. I uninstalled the driver from Synaptic and now I'm running in low settings.

Edit: Sorry, I fixed it by installing the drivers from Synaptic instead of the Hardware Manager. I'll be sure to post about any problems on here if I ever have any. Cheers!

---

### Post by oddround on 2009-12-21
I assume you are using the nVidia display config tool.
Check in /home/<your user name>/.config for a file called monitors.xml .
You may have a pre defined resolution here. You can move it out the way set you resolution then it will appear again.

I also had a problem with a video cable on one installation. It was a cheap one and the display resolution would only show safe mode 800x600 or 640x480. I replaced it with a good one and it was fine after.
I think this is your problem but you know, it can be a bit frustrating to find out.

monitors.xml looks like this..,
------------------------------------
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="default">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1360</width>
          <height>768</height>
          <rate>50</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
      </output>
  </configuration>
</monitors>
-----------------------eof---------------
Good luck and be careful.
:KS

---

