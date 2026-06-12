---
title: "Wacom Intuos 2 usb stuck problem"
date: 2004-10-26
forum: Hardware &amp; Laptops
---

### Post by Grenshad on 2004-10-26
Hi here

Just after installing Ubuntu official release, I see my wacom tablet react when I use my pen on it, but the cursor goes stuck to the top right corner of the screen. My ps2 mouse (mx700) was well detected and work fine.

After customize my XF86Config-4 file to make my tablet to work, it just ... the same, I try with all the /dev/input/filename and it's the same again... Since I usually know how to make XF86Config-4 files works withs my tablet (it's my third, I haved an artpad and a graphire in the past), I think maybe udev (all new for me) or something else that I don't understand make me pain...

As I failed to find a solution by myself, I come to request your ideas about that.

Please help me :) If you save my soul from becoming mad, I'll draw a little oekaki for you   [ [-o<

---

### Post by tambooki on 2004-10-27
Hmmm... I just finished getting my aiptek tablet set up under ubuntu, so here's what little advice I can offer. I believe the aiptek driver was adapted from the wacom, so some of this may apply to you. I know w/ the aiptek, symptoms such as you're describing result from using the /dev/input/mice or similar device for the tablet, as well as the mouse. In my case, the solution was to check /sys/bus/usb/drivers/aiptek/<sum number>/input_path, which was a file that contained "/dev/input/event<X>", X being some number that depends on where udev decided to throw the device. I know there is a /sys/bus/usb/drivers/wacom, but since I don't have a wacom tablet, I can't tell you what files and such appear in here when one is connected. Hopefully, there is something similar for you that you can determine what eventX the device is on, once attached. If not, you could also manually "cat /dev/input/event<X>" for each event device, and see which one prints garbage when you use the tablet. To simplify my life, I wrote a little script (which runs at boot-time, or manually), that checks my /sys/.../aiptek/input_path, and uses that to create a symlink from /dev/input/aiptektablet -> /dev/input/event<X>. Then, I can just put
Option "Device" "/dev/input/aiptektablet"
in my XF86Config, and things should work. I'm not sure, but I believe that this device needs to point to an existing tablet when X starts, so I think you have to create the symlink and restart X if you plug the tablet in after starting X. Anyway, like I said, this is all info that pertains to the aiptek, but hopefully something in here will be helpful!

---

