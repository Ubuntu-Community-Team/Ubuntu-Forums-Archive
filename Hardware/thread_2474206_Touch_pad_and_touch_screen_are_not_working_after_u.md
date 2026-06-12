---
title: "Touch pad and touch screen are not working after upgrading to ubuntu 22.04"
date: 2022-04-23
forum: Hardware
---

### Post by mizo on 2022-04-23
I have laptop Acer spin 5 "Spin SP513-54N" and had ubutnu 21.10 installed on it. At first, the touch pad and touch screen were not working so I followed the instructions in this page and it fixed it: [https://sciactive.com/2020/12/04/how-to-install-ubuntu-on-acer-spin-5-sp513-54n-for-the-perfect-linux-2-in-1/](https://sciactive.com/2020/12/04/how-to-install-ubuntu-on-acer-spin-5-sp513-54n-for-the-perfect-linux-2-in-1/)

sudo gedit /etc/default/grub
Add pci=nocrs to the end of the options for GRUB_CMDLINE_LINUX_DEFAULT. It should look something like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nocrs"
sudo update-grub

Later when I upgraded to ubuntu 22.04, touch pad and touch screen stopped working again When ubuntu 22.04 starts up before applying GRUB fix, I get this error:
[IMG]https://i.stack.imgur.com/PfThR.jpg[/IMG]

Ubuntu starts fine but the touch is not working. But when I apply the fix, ubuntu 22.04 fails to start with this error:

[IMG]https://i.stack.imgur.com/yuSmf.jpg[/IMG]

I tried every fix I could possible find online but nothing works. plz help me with this issue as the computer is not usable without touch pad

---

### Post by harry6x on 2022-04-24
I am having exactly same problem with my lenovo V series 15-IIL model. Unable to find any solution. Using the method you described certainly breaks the ubuntu 22.04 LTS system. It used to work in 20.04 LTS. The touchpad is not being recognised.

---

### Post by hamzahsby on 2022-09-01
Please DISABLE wayland on /etc/gdm3/custom.conf


Please read: [https://linuxconfig.org/how-to-enabl...-22-04-desktop](https://linuxconfig.org/how-to-enabl...-22-04-desktop)

---

