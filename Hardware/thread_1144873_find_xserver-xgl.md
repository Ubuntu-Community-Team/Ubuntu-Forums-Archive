---
title: "find xserver-xgl?"
date: 2009-05-01
forum: Hardware
---

### Post by joe2me on 2009-05-01
Noob to linux and trying to get my graphic card to work...

I'm trying to follow the steps below from [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%208.04%20and%20Ubuntu%208.10]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%208.04%20and%20Ubuntu%208.10") but what to do when first step fails? (not running xserver-xgl?)

```
Nvidia driver installed but nvidia X server settings says you don't appear to be using the nvidia driver (on 8.10)

drives you crazy doesn't it try

    * apt-cache policy xserver-xgl 

that will let you know if your running it then

    * sudo apt-get remove --purge xserver-xgl 

then Ctrl alt backspace to restart X log back in and try to enable desktop effects it worked for me with a geforce 6200 and now nvidea settings should work, also

    * glxinfo | grep direct 

returns something like

    * direct rendering: Yes
          o GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 

It might be that you need to run nvidia-xconfig as well but chances are you have several times be aware it's not friendly to custom settings It wiped out the fix for my wireless keyboard. The driver used was the Nvidia Accelerated Proprietary driver (version 180).

    *

      For other problems, please visit the forums at http://www.ubuntuforums.org/ . 
```

---

