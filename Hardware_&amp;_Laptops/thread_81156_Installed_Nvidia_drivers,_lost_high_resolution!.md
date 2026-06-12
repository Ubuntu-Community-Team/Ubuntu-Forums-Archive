---
title: "Installed Nvidia drivers, lost high resolution!"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by greatwhite on 2005-10-23
Hi all,

I installed the nvida drivers for my card as per these instructions:

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

My nvidia card seems to be working now. But I lost the ability to run at 1900 x 1200 and World of Warcraft wont' even start. 

Any idea how to get my high resolution back? I'm stuck at 1024 x 768 right now. Thanks if you can help me out.

---

### Post by professor_chaos on 2005-10-23
In case you were not aware. First look in /etc/X11/xorg.conf and make sure it's listed for the depth you use. 
Or try to reconfigure xserver by "dpkg-reconfigure xserver-xorg" 

If it is listed, you might want to remove the other resolutions and see if that forces it. Although you should know how to use vi or another commandline editor to change it back incase you have problems.

---

### Post by cameleon078 on 2005-10-24
Can you copy/paste your /etc/X11/xorg.conf (just Monitor and Screen section) ?
Can you give me too the result of ddcprobe command ?

---

