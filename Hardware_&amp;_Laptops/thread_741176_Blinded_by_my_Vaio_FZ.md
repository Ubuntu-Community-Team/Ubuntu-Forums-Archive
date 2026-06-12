---
title: "Blinded by my Vaio FZ"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by starlily on 2008-03-31
I have a brand new Sony Vaio FZ-340E. I installed a Hardy beta (Ubuntu Studio) and everything so far absolutely worked out of the box; wireless network, 3d accel, card reader, sound buttons, even my wireless logitech mouse with scroll wheel. I havent tried the video out or bluetooth yet. 

The only thing that doesnt work is brightness control for the LCD, and believe me, its really really bright. No Fkeys, no soft control.   
I have the Nvidia card, so Intel card fixes are out. 

smartdimmer doesnt work, it fails with "init_nvclock() failed!". Lots of posts from people with the same problem, no fixes. 

I commented out sonypi so it wouldnt load, and sony-laptop does load. I have confirmed this with dmesg (the version is 0.5). Still no luck, the /sys/class/backlight/sony path never appears.
Update: Ive tried every combination of sonypi / sony_laptop / sony_acpi, to no effect. 

The best hope I have so far is this: 
[http://ubuntuforums.org/showthread.php?t=702879](http://ubuntuforums.org/showthread.php?t=702879)

Update: I ran acpi_ listen: and heres what I saw:
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b

The first two are fnkey+f5, the second fnkey+f6. I have no idea what to do with those values. 

I also stopped in bios long enough to get the version number: R2110J7

Any help appreciated. Im more than willing to try stuff if you are someone like k84 or IntuitiveNipple and need data. 

Thanks, 
Lily

---

