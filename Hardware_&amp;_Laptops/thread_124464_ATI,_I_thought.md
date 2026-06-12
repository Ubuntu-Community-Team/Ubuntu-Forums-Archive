---
title: "ATI, I thought"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by Il_Tuo_Nome on 2006-02-01
The card I have is a Radeon 8500, however, I don't know if it was detected correctly or not. Is there a way to know what card is being detected? Assuming it was, would it be necessary for me to still : 

> 3.&#8195;How do I install the 3D ATI video card driver?
      1. Install the xorg-driver-fglrx package with Synaptic (See How do I use Synaptic to install packages?)

          Miscellaneous - Graphical (restricted) > xorg-driver-fglrx
       2. echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf??

At least that's what I understood from here [http://www.ubuntuforums.org/showthread.php?t=99154&highlight=wine]("http://www.ubuntuforums.org/showthread.php?t=99154&highlight=wine")




Thank you :)

---

