---
title: "Dell Latitude Z 600"
date: 2010-03-14
forum: Hardware
---

### Post by 5hundy on 2010-03-14
The Dell Latitude Z 600 seems to work out of the box with 9.10. I've tested the basic hardware, the ethernet card, and the wireless. I was able to get Heroes of Newerth working by installing xorg-edgers (latest Intel graphics drivers).

Update: I have discovered that the touchpad gets recognized as normal mouse and not as a synaptics touchpad (at least in 9.10). This is unfortunate because it means you can't do things like disable the touchpad while using the keyboard. The end result - if you are not careful with your hands, the pointer will often go crazy while you are using the keyboard. Fingers crossed that this gets resolved in a later release.

Update: I finally figured out how to turn the touchpad off. In Preferences -> Startup Applications, I added a new application that runs:

xinput set-int-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 8 0

I also added application launchers on my taskbar which can to turn it off and on. To turn it back on do:

xinput set-int-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 8 1

---

### Post by vault55 on 2010-05-26
> **5hundy said:**
> The Dell Latitude Z 600 seems to work out of the box with 9.10. I've tested the basic hardware, the ethernet card, and the wireless. I was able to get Heroes of Newerth working by installing xorg-edgers (latest Intel graphics drivers).

Update: I have discovered that the touchpad gets recognized as normal mouse and not as a synaptics touchpad (at least in 9.10). This is unfortunate because it means you can't do things like disable the touchpad while using the keyboard. The end result - if you are not careful with your hands, the pointer will often go crazy while you are using the keyboard. Fingers crossed that this gets resolved in a later release.

Update: I finally figured out how to turn the touchpad off. In Preferences -> Startup Applications, I added a new application that runs:

xinput set-int-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 8 0

I also added application launchers on my taskbar which can to turn it off and on. To turn it back on do:

xinput set-int-prop "ImPS/2 Generic Wheel Mouse" "Device Enabled" 8 1

Has this been corrected in 10.04? I just bought a Z600 and I thought I could live without Ubuntu but I've made it less than 2 days!

---

### Post by 5hundy on 2010-08-18
> **vault55 said:**
> Has this been corrected in 10.04? I just bought a Z600 and I thought I could live without Ubuntu but I've made it less than 2 days!

This isn't fixed in 10.04. There are a lot of reasons to love this laptop, but the touchpad support in linux is not among them. I'd go so far as to say not to get this laptop unless you plan on using it with an external mouse.

---

