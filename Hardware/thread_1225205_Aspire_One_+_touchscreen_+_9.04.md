---
title: "Aspire One + touchscreen + 9.04"
date: 2009-07-28
forum: Hardware
---

### Post by ChrisJC on 2009-07-28
System: Acer Aspire One netbook + 9.04
Issue: Adding touch sensor didn't work very well, X axis reversed, and calibration all to pot.

The touch hardware is an eGalax board with a custom 8.9" sensor.

The calibrate application in Applications -> Calibrate Touchscreen doesn't work with flipped axes.

Solution:
Add the following to /etc/hal/fdi/50-eGalax.fdi
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="eGalax">
      <match key="info.capabilities" contains="input">
        <merge key="input.x11_driver" type="string">evtouch</merge>
        <merge key="input.x11_options.SwapX" type="string">1</merge>
      </match>
    </match>
  </device>
</deviceinfo>

This swaps the X axis by overriding (or supplementing) /usr/share/hal/fdi/policy/20thirdparty/50-eGalax.fdi

Next step is to run the dodgy calibration tool in Administrator -> Calibrate Touchscreen
Do the first part as requested which finds the limits of the sensor. Hit Enter.
This next bit is IMPORTANT:
When the TOP LEFT cross hair goes red, select the TOP RIGHT cross hair
When the TOP MIDDLE cross hair goes red, select the TOP MIDDLE cross hair
 When the TOP RIGHT cross hair goes red, select the TOP LEFT cross hair
etc.
I.e. swap left and right.

Restart X, and it works!

It would be preferable if the calibration routine understood swapped axes, however I hope this helps somebody in the meantime.

Chris.

---

