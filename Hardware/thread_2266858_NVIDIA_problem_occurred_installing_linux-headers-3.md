---
title: "NVIDIA problem occurred installing linux-headers-3.16.0-31-generic"
date: 2015-02-25
forum: Hardware
---

### Post by TWFJR on 2015-02-25
Ubuntu 14.10 updating linux-headers-3.16.0-31-generic says a problem occurred installing software, package: nvidia-331-umv. I've listed some results to two commands below. I do not understand what “bbswitch” represents under command: dkms status. Nor do I understand whether all the listings of drivers is causing a  problem. What needs to be eliminated? Please give an example of command to uninstall/purge problem graphics drivers. My problem with uninstall would be how to list the graphics driver in the command.


tom@tom-desktop:~$ dkms status
bbswitch, 0.7, 3.16.0-29-generic, x86_64: installed
bbswitch, 0.7, 3.16.0-30-generic, x86_64: installed
bbswitch, 0.7, 3.16.0-31-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-29-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-30-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-31-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-29-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-30-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-31-generic, x86_64: installed

tom@tom-desktop:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0 ==
vendor   : NVIDIA Corporation
model    : GK104 [GeForce GTX 660 Ti]
modalias : pci:v000010DEd00001183sv00001043sd0000841Fbc03sc00i00
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-331 - distro non-free recommended
driver   : nvidia-331-updates - distro non-free
driver   : nvidia-304 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

---

