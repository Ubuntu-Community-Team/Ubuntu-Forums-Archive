---
title: "Machine wants 'vesa' I want intel"
date: 2008-11-18
forum: General Help
---

### Post by DougieFresh4U on 2008-11-18
Why is it that my machine wants to use the vesa driver and not the intel? With Hardy and Intrepid, it seems to choose the 'vesa.How can I fix this? When I tried a couple of months ago to use intel and not vesa, it 'borked' my machine. So I am a little leary on messing it up again.
Any suggestions or input I would like to hear
Thanks

---

### Post by amp_man on 2008-11-18
Are you sure the "intel" driver supports your hardware? You should be able to install xserver-xorg-video-intel and then just change "vesa" to "intel". If that doesn't work, you can boot into recovery mode (press ESC at the 2 second delay before ubuntu starts), then there's an option to reconfigure Xorg, that should set it back to vesa. There's also some info on specific applications [here](http://intellinuxgraphics.org/user.html)

---

### Post by easoukenka on 2008-11-18
I have had to play with  my xorg several times so while not a direct fix to your problem but might help you troubleshoot it quicker without rebooting and will not bork your machine.

in terminal do
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

now you need a basic understanding of vim or use your own terminal editor just push i to get to a sorta standard editor when you are ready to save just type :wq 

ok so now you can edit xorg by doing sudo vim /etc/X11/xorg.conf try to change information in there and push ctrl alt backspace to restart x  if it doesn't restart just push ctl alt backspace or ctl alt f2 now type in sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf now you can type startx and voila your back in.

Always have that backup of your xorg it makes things alot quicker to restore.  Now while in terminal you can edit it anyway you like try then just try again.    Good luck

---

### Post by amp_man on 2008-11-18
> **easoukenka said:**
> ok so now you can edit xorg by doing sudo vim /etc/X11/xorg.conf try to change information in there and push ctrl alt backspace to restart x  if it doesn't restart just push ctl alt backspace or ctl alt f2 now type in sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf now you can type startx and voila your back in.

Always have that backup of your xorg it makes things alot quicker to restore.  Now while in terminal you can edit it anyway you like try then just try again.    Good luck

FYI, vim has a very steep learning curve, nano is a much simpler editor ;) Also, restarting X sometimes doesn't load/unload the video modules properly, that's why I recommend rebooting.

---

