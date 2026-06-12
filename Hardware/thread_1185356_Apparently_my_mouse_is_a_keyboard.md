---
title: "Apparently my mouse is a keyboard"
date: 2009-06-12
forum: Hardware
---

### Post by Dirktooth on 2009-06-12
Hi everyone, I was wondering if you could help me with a very strange problem. 
I have a Dell XPS M1530 laptop that dual boots Ubuntu 9.04 and Windows XP. It's got a touchpad built in, but I prefer to use my Microsoft Sidewinder USB mouse. The mouse works fine for the most part, and I can set the resolution on it in HAL, but when I try to turn off the mouse acceleration it only seems to work for the touchpad. Here's the code I added to preferences.fdi:

<device>
<match key="info.capabilities" contains="input.mouse">
<merge key="input.x11_driver" type="string">evdev</merge>
<!--<merge key="input.x11_options.Device" type="string">/dev/inpu/mice</merge> -->
<merge key="input.x11_options.Sensitivity" type="string">0.0</merge>
<merge key="input.x11_options.Resolution" type="string">1200</merge>
<merge key="input.x11_options.SampleRate" type="string">800</merge>
<merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
</match>
</device>

When I un-comment the fourth line, my USB mouse appears to be completely gone. However, my touchpad takes on the desired sensitivity settings. 
Once I re-commented that line, I checked xinput and found something very bizarre:

"Microsoft Sidewinder? Mouse"   id=4    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
        Num_buttons is 32
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1

That's exactly what it says in there. Not only is my mouse somehow a keyboard, but it has 248 keys. When I uncomment that one pesky line in preferences.fdi, this device isn't even listed anymore. I've got a feeling that this is the reason I can't get rid of the acceleration on the Sidewinder mouse even though it seems to work with the touchpad. 

I have no idea whether this is a laptop-specific thing or if all Sidewinders are listed as keyboards, but any help would be greatly appreciated. Thanks in advance!

---

### Post by jimv on 2009-06-12
How many words per minute can you click?

---

