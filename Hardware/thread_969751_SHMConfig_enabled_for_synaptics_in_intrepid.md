---
title: "SHMConfig enabled for synaptics in intrepid"
date: 2008-11-03
forum: Hardware
---

### Post by xan.scale on 2008-11-03
[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

according to this guide i have made the file, but dont works because when open gsynaptics i recive this error message:
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

:~$ cat /etc/hal/fdi/policy/shmconfig.fdi
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>

what am I doing wrong?

---

### Post by issih on 2008-11-03
Two thoughts, not particularly hopeful either will help but worth trying..

First off in my fdi file used to get my macbook touchpad working the <merge> value is true with a lower case t

Secondly I had to reboot (not just log off or restart X, reboot) before things started working.

If its neither of those, I can only presume somehow your <match> is not working properly

Hope that helps

---

### Post by xan.scale on 2008-11-04
changed T with t and restarted, but i got same error...

---

### Post by xan.scale on 2008-11-04
UP
after 6 hour this thread is in page 5...

TOO users? lol

---

### Post by PatrickVogeli on 2008-11-04
I put the line <merge key="input.x11_options.SHMConfig" type="string">True</merge> into the file /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

```

~$ cat /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
	<!-- Arbitrary options can be passed to the driver using 
	     the input.x11_options property since xorg-server-1.5. -->
	<!-- EXAMPLE:
	<merge key="input.x11_options.LeftEdge" type="string">120</merge>
	-->
	<merge key="input.x11_options.SHMConfig" type="string">True</merge>
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1280</merge>
        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">0</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">40</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
        <merge key="input.x11_options.FingerLow" type="string">16</merge>
        <merge key="input.x11_options.FingerHigh" type="string">80</merge>
        <merge key="input.x11_options.FingerPress" type="string">256</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
        <merge key="input.x11_options.MinSpeed" type="string">0.8</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">1.2</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">25</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">223</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">200</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

---

### Post by xan.scale on 2008-11-04
i have tryed to put this line in that file, but noting results...

---

### Post by Katerine on 2008-11-04
Try something:

In Terminal, type "synclient TouchPadOff=1"

If you're told, "Can't access shared memory area. SHMConfig disabled?", then I just got through the same problem (on my EEE 1000H running Ubuntu 8.04 hardy) yesterday. In my case, I located the following thread, which got it working:

[http://ubuntuforums.org/archive/index.php/t-942400.html](http://ubuntuforums.org/archive/index.php/t-942400.html)

HTH with your issue. :)

(BTW, just in case the synclient command works, it will probably turn off your touchpad. You get it working again with "synclient TouchPadOff=0")

---

