---
title: "how to improve screen resolution? (graphical and text mode)"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by mrpivello on 2006-03-22
Hi, I'm working with ubuntu breezi 5.10 with an LG flatron L1750S monitor (LCD). Before that I had a T910B LG Flatron ( not LCD), in which  I got a 1600x1200 screen resolution in graphical mode. Now I "only" get 1280x1024. It's not bad, but it could be better. Is this because my nvidia card doesn't support this L1750s or because the former was detected during ubuntu installation? In xorg.conf my monitor is still set to LG T910B.

Also, in both monitors, I only get 640x480 in the text mode console, and that's my main problem. How can I improve the screen resolution in text mode? I've tried already with SVGATextMode to configure it, but higher resolutions are not supported. I've followed the tutorial listed in [http://www.digitalhermit.com/linux/hiresconsole.html](http://www.digitalhermit.com/linux/hiresconsole.html), which is the only one I found, but I couldn't finish it because in one of the steps we have to modify lilo, and I don't know how to switch from grub to lilo (I've installed it via apt-get, but I couldn't set it as the default boot loader). Can anyone help me?

Thanks in Advance

Márcio Ricardo

---

### Post by localzuk on 2006-03-22
It appears that the L1750S ([http://www.dealtime.com/xPO-LG_LG_Electronics_L1750S_17_TFT_Silver_Swivel_Tilt_Monitor](http://www.dealtime.com/xPO-LG_LG_Electronics_L1750S_17_TFT_Silver_Swivel_Tilt_Monitor)) does not support resolutions greater than 1280x1024 - most TFT screens don't.

I'm not sure about changing the resolution of your console (tty's). May I ask why you need larger resolution on the console?

---

### Post by mrpivello on 2006-03-22
>>>"May I ask why you need larger resolution on the console ?"
I'm developing a numerical solver which demands a lot of memory to run. Since I'm using emacs to develop my code, I can do it in text mode and allow nearly 200MB more memory to the solver. Besides that, I use SuSE 9.3 at home and the text mode resolution is 1024x768 by default, so I thought it was easy to do it here, but I'm having these problems.
Thanks

Márcio

---

### Post by theanorak on 2006-03-22
You're looking for a framebuffer console. The link below might be a place to start:

[http://wiki.linuxquestions.org/wiki/Framebuffer#Configuring_framebuffer_console](http://wiki.linuxquestions.org/wiki/Framebuffer#Configuring_framebuffer_console)

{edit}
Actually, that link's no good...the FBconsole section is "to do". This looks more promising:

[http://www.digitalhermit.com/linux/hiresconsole.html](http://www.digitalhermit.com/linux/hiresconsole.html)

---

### Post by henriquemaia on 2006-03-22
You can change the console resolution by booting up grub with the following command added to its options:

```
vga=n
```

where n can be:

......| 640x480|800x600|1024x768|1280x1024
----+-------------------------------------
.256 |  **0x301**  |   **0x303**   |  **0x305**   |  **0x307**
.32k |  **0x310 ** |  **0x313  **  |** 0x316 **   |** 0x319**
.64k | ** 0x311**  |   **0x314**   |  **0x317**  |   **0x31A**
16M |  **0x312**  |   **0x315**    | **0x318**  |   **0x31B**

---

