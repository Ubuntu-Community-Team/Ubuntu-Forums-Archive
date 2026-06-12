---
title: "HAL FDI &amp; Legacy Serial Devices (Dynapro)"
date: 2009-01-24
forum: Hardware
---

### Post by KA8WTK on 2009-01-24
Hello,
  I have an industrial flat panel computer with a Dynapro 8 wire resistive touch screen built-in. Ubuntu 8.10 installed without a problem and appears to run fine. I am looking for way to use the touch screen.
  The touch screen is on ttyS2. Using "cat /dev/ttyS2" and touching the screen produces an output in a terminal. The "old" way to use this device was to add lines in the xorg.conf file (as noted in other posts on the forum). However, it appears that 8.10 does not make the same use of xorg.conf that previous versions did. Adding the lines recommended into xorg.conf produces a crashed X-server.
  To further complicate things, running "lshal | less" does not find the touch screen device. Either hal won't probe past the serial port or the hardware is just too old to be able to talk to hal. So, my thought is to write a fdi policy file to tell the computer that the touch screen is there.
  The lines that would be added to the Device section of xorg.conf are:

 Section "InputDevice"
	Identifier      "touchscreen"
	Driver		"dynapro"
	Option		"Type" "Finger"
	Option		"Device" "/dev/ttyS2"
	Option		"BaudRate" "9600"
	Option		"MinX" "1000"
	Option		"MaxX" "0"
	Option		"MinY" "900"
	Option		"MaxY" "0"
	Option		"SendCoreEvents" "True"
EndSection
	
  There are also lines to add to load the dynapro driver and a line to add to ServerLayout.
  My "translation" of this to a fdi policy file is:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.mouse">
	<merge key="input.x11_driver" type="string">dynapro</merge>
	<merge key="input.x11_options.MinX" type="integer">1000</merge>
	<merge key="input.x11_options.MaxX" type="integer">0</merge>
	<merge key="input.x11_options.MinY" type="integer">900</merge>
	<merge key="input.x11_options.MaxY" type="integer">0</merge>
	<merge key="input.x11_options.AlwaysCore" type="string">true</merge>
	#<merge key="input.device.set" type="string">/dev/ttyS2</merge>
	#<merge key="tty.serial.baud_base" type="integer">9600</merge>
    </match>
  </device>
</deviceinfo>     	     	    		

  I am posting this because this does not work. The file is saved in the etc/hal/fdi/policy folder. I have the latest dynapro driver. "input.mouse" is used as this screen is like a mouse pointing device(?).
  So, how far off am I in my thinking? Any help appreciated.

Thanks,
       Bill

P.S. I see when I preview this post that the indentations in the code listings are missing. However, they are there in the code.

---

