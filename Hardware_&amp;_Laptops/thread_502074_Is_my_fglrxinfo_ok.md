---
title: "Is my fglrxinfo ok?"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by JumpyLINUX on 2007-07-16
I have a Asus M2A-VM HDMI motherboard with built in ATI Radeon X1250 graphics card. And I can not play any video files. Either I get the following error message: "Error opening/initializing the selected video_out (-vo) device.", or the whole gui reboots. I found a website where it was said that this was a know bug until AMD fglrx 8.34.8. Correct me if I'm wrong but isn't this included on the FeistyFawn DVD.

Also I noticed that when I configured my screen with "sudo dpkg-reconfigure xserver-xorg" and chose fglrx on a clean Kubuntu installation the selection rectangle in KDE was updated often. But when I installed(not sure if it succeeded) the newest ATI drives with ENVY now the selection rectangle updates very slow especially if the selection area gets big.

Any ideas how I could get my graphicscard drivers working?


PS: I use Kubuntu 7.04 AMD 64bit and I use the DVI-D port to connect to my monitor.
Oh and here's what fglrxinfo gives as output if it's of any help:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

---

### Post by misfitpierce on 2007-07-16
Use the onboard restricted drivers... should auto configure and setup everything

---

### Post by JumpyLINUX on 2007-07-16
> **misfitpierce said:**
> Use the onboard restricted drivers... should auto configure and setup everything

What do you mean by auto configure? Can you watch video files even with the LiveDVD without any configuration. And do you have 32 or 64 bit (K)ubuntu? I read some where that the problem was only with 64 bit version.

---

### Post by misfitpierce on 2007-07-16
I was saying you should use the ATI drivers that come with the distro. I run 32 and 64 bit ubuntu... If newest drivers did not work revert back to one's that came with ubuntu in restricted drivers... If your ATI is configured correctly you should not see anything about MESA... It should say ATI Technologies etc. Try reverting to restricted drivers which are a bit older. Also on my 64 bit only thing I have trouble playing is flash in 64 bit browser so I downloaded 32 bit firefox for that... but all video works. You may need to get automatix and get codecs from it.

---

### Post by JumpyLINUX on 2007-07-20
> **misfitpierce said:**
> 
 You may need to get automatix and get codecs from it.

Downloading Automix2 ans installing the popular codecs and VLC-media player through it helped. Thank you.

---

