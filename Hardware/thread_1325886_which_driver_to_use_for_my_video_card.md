---
title: "which driver to use for my video card ?"
date: 2009-11-13
forum: Hardware
---

### Post by _mikec_ on 2009-11-13
video card:
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

System / Administration / NVIDIA X server settings
error: " [I][B]You do not appear to be using NVIDIA X Driver.
            Please edit your X configuration file, just run nvidia-xconfig
            as root and restart the X Server[/B]. [/I]" 

# nvidia-xconfig
The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-glx-173
 * nvidia-glx-185
 * nvidia-glx-96

Which one should i choose for my video card ?

---

### Post by _mikec_ on 2009-11-14
anyone ?

i've search on packages.ubuntu.com for the right package and i found that nvidia-glx-71 has the Vanta/Vanta LT driver i need but it's only available resptricted in intrepid ubuntu version 8.04 and the only files available for Karmic Koala 9.10 are 
* nvidia-glx-173
 * nvidia-glx-185
 * nvidia-glx-96
and none of them has the Vanta/Vanta LT driver i need.

---

### Post by _mikec_ on 2009-11-14
i am using the nvidia-common driver right

---

### Post by 73ckn797 on 2009-11-14
Have you checked the System/Administration/Hardware Drivers to install the recommended driver if one is listed. You did not state that.

---

### Post by HappyFeet on 2009-11-14
[Here]("http://www.nvidia.com/object/linux_display_ia32_71.86.11.html") is the nvidia 71 driver.

---

### Post by J-Buntu on 2009-11-14
"If the three drivers you posted were suggested by the  System/Administration/Hardware Drivers" - then there is no harm in trying them all, "one by one", making sure you only install one at a time, then removing the current one before you try the next one. Obviously reboot if it tells you to. 
I had an option of two, i tried them both, one at a time and one didn't play well with my fan, so i chose the other.

---

