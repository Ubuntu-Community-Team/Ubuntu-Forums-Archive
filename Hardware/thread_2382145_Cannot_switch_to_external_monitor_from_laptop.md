---
title: "Cannot switch to external monitor from laptop"
date: 2018-01-09
forum: Hardware
---

### Post by br4to92 on 2018-01-09
Hello, i have a problem with my secondary monitor on Ubuntu 16.04: when i switch to it from the built-in display (Display settings), the image goes black and only the mouse shows on it. This happens when i'm not using the nVidia drivers. When using them (installed via Additional Drivers program), the external monitor isn't shown at all. What should i do? The monitor works fine since Windows detects it with no problems. Does anybody know what's wrong? I've set a custom resolution to my built-in display (1600x900, which i'm using it; this was done with the xrandr commands). Thanks!

EDIT #1: It seems that the NVIDIA driver installed via the Additional Drivers program isn't the correct one, as it hasn't all the options. The problem is, when i want to install the latest driver from the NVIDIA website (the .run file), i get an error ("You apppear to be running an X server: pleasae exit X before installing"). What should i do? Thanks!

EDIT #2: Here's the answer that actually worked for me:
disable secure boot
select another driver that is not from nvidia in the additional drivers
restart
sudo apt purge nvidia*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
go to additional drivers
select the nvidia binary driver (proprietary)
restart

---

