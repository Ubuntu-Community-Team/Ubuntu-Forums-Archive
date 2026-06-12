---
title: "enabling shmconfig"
date: 2010-08-22
forum: Hardware
---

### Post by kespindler on 2010-08-22
Hi,

I am trying to enable shmconfig so that I can use gsynaptics and related programs. So far I've done the following:

Created /etc/hal/fdi/policy/shmconfig.fdi with contents:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>
```

I restarted, and looked to check if shmconfig was on:
```
less /var/log/Xorg.0.log | grep -i shmconfig
```
No result. Then I went to xinput list.
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse             	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```

So I get why shmconfig.fdi didn't work. It wasn't activated by any devices. My question is, how can I tell which device is my touchpad, and why doesn't it have a name resembling touchpad/synaptics, etc?

This is on 10.04 ubuntu on a 1015pe, which I think had an elantech touchpad (I'm not positive on that, and I forget where I learned that). Otherwise, the touchpad works great. Sensitivity, multitouch, etc, so the driver or what have you is working well.

Thank you for your help!!

---

