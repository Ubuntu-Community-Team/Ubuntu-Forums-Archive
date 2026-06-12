---
title: "for those that kernel update killed gui"
date: 2005-11-25
forum: General Help
---

### Post by teaker1s on 2005-11-25
hit esc on boot and you can run previous kernel that will boot with gui next install kernel restricted module that is right for you eg 386i /686/k7
reboot if you still have no gui you will need to repeat restart with old kernel as before and use synaptic to install nvidia-glx-legacy if you have nvidia card. as many older nvidia cards now appear to be supported under legacy still problems then boot latest kernel
if need be
sudo dpkg-reconfigure xserver-xorg
NV is basic no thrills or open gl driver
nvidia is open gl driver
mb x 1024 will give you required memory amount to type in xserver for your card
as for other brands you will have to select as required

---

### Post by teaker1s on 2005-11-25
bump

---

### Post by echo $USER on 2006-06-15
me too.

---

