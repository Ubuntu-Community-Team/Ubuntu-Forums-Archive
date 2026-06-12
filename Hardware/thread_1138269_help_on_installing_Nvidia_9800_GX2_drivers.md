---
title: "help on installing Nvidia 9800 GX2 drivers ?"
date: 2009-04-26
forum: Hardware
---

### Post by Blacmoon181 on 2009-04-26
As a user of ubuntu for over a year now i have installed it on my main rig instead of my laptop. I need some help installing a Nvidia 9800GX2 driver for the new release of jaunty jackalope. a step by step tutorial would be fantastic however if anyone knows of one on the web send a link please .

Cheers, Nick

---

### Post by ugriffin on 2009-04-26
Ok:

go to Nvidia.com
go to the "drivers" section
search for Linux drivers and download it.
Now that you've got your linux driver, two important things are needed:
rename your driver to "drivers.run"
move your driver to your home folder ("/home/yourusername/)
**NOW: Write down this on a piece of paper since we're gonna work from a command line.**
Press CTRL+ALT+F1
Login.
type "sudo /etc/init.d/gdm stop" (without the quotations) if you run Ubuntu or
type "sudo /etc/init.d/kdm stop" (without the quotations), if you run kubuntu
type "sudo sh /home/yourusername/drivers.run"
Accept the eula, choose yes to everything.
Once this is done, and the NVIDIA drivers are installed, it's time to restart your GUI.
type "sudo /etc/init.d/gdm start" or "sudo /etc/init.d/kdm start"... you'll know the diffrence now. 


Enjoy.

---

### Post by blackmoon181 on 2009-04-26
i have followed your instructions and it has worked perfectly, thanks!

---

### Post by ugriffin on 2009-04-26
Do this each time there's a kernel upgrade... NVIDIA drivers get messed up during these. 



Have fun. :)

---

