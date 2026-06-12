---
title: "Nvidia driver not working"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by cris on 2007-04-06
I followed an installation tutorial for my GeForce 6600 driver , it all worked fine until restart.When rebooted , i got some errors about X ,it couldn't configure it , and if I wanted to see the report . This is what I did : 
downloaded the latest nvidia driver 
sudo /etc/init./gdm stop
sudo sh NVIDIA...
it said that I have a kernel problem , and asked me if i want it to create one , anwered yes to all of it's questions , all finished just fine 
started X , it gave me the NVIDIA logo at the start , and the control panel in the menu.
after that i completely removed the nvidia common kernel (i read that it had some conflicts with the actual kernel) , and after reboot , x didn;t start at all. Please help

---

### Post by tommcd on 2007-04-06
You can just use the nvidia-glx driver from the repositories in synaptic. It is easier. You don't need the driver from nvidia.
First, boot to recovery mode, and do <sudo dpkg-reconfigure xserver-xorg>. Go through this and answer defaults to all if you don't know the answers. This will get your GUI back.
Second, see this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Uninstall the nvidia driver in "Method 2" listed there.
----------------------------------------------------------------------------
(You should not have both nvidia drivers installed together.)

Third, install the nvidia-glx driver like this:
<sudo apt-get install nvidia-glx> or get nvidia-glx from synaptic. Then run<sudo nvidia-xconfig>.
Then hit ctrl+alt+backspace and login, or reboot. You should see the nvidia splash indicating the diver was installed. If not, you may need to edit xorg.conf as explained in the link I gave.

Hope this helps.
(Edited to try to simplify things, and fix typos.)

---

