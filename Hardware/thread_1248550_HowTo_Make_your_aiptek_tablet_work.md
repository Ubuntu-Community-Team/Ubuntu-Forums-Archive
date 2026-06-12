---
title: "HowTo: Make your aiptek tablet work"
date: 2009-08-24
forum: Hardware
---

### Post by AtomZeppelin on 2009-08-24
Hi!

I don't know if this is the right forum, but since many users seem to have trouble with their tablet, I'll just dumpt this howto here.
I'm using an Aiptek USB Tablet (6000U) for 4 weeks now without any problems on Kubuntu 9.04.
Here is what I have done:
[B]
Steps that you have do once:[/B]

Install the xserver-xorg-input-aiptek package

xorg.conf: No modifications, if you have any extra entries for your tablet there, delete them first and restart X.

/etc/hal/fdi/policy/10-aiptek.fdi: Create this file if it doesn't exist. The content should be:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.zMin" type="string">0</merge>
      <merge key="input.x11_options.zMax" type="string">511</merge>
    </match>
  </device>
</deviceinfo>
```**Steps that you have to do everytime after you have plugged your tablet in:**

In the shell go to /sys/bus/usb/drivers/aiptek/<special directory>
where <special directory> is something like "6-1:1.0"

Execute the following line at least(!) 3 times:
```
sudo echo absolute > ./coordinate_mode &&  sudo echo anything > ./execute
```Done, your tablet should work with pressure sensivity :)

The trick here is to execute the cmdline manytimes, there seems to be some bug in X/kernel driver.
If anything goes wrong have a look at the diagnostic file in the same directory.

Cheers,
AtomZeppelin

---

