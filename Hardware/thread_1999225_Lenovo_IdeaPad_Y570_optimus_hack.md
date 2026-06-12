---
title: "Lenovo IdeaPad Y570 optimus hack"
date: 2012-06-07
forum: Hardware
---

### Post by atkane on 2012-06-07
Hey ya'll, I am relatively new to linux, been using it for about six months or so as my primary operating system, and I had just gotten my new idea pad y570, installed ubuntu, when I found out that ubuntu didnt have nvidia switchable graphics support, and worse, there was a bug in lenovo's laptops dealing with it. So I found the hack over on the bumblebee project, and I'm going to just copy-paste the steps I took until the point where it goes wrong.
$ git clone git://github.com/Bumblebee-Project/bbswitch.git -b hack-lenovo $ cd bbswitch
so i get the file, and i change into the directory, then when I try
$ mkdir /usr/src/acpi-handle-hack-0.0.1
It tells me it already exists, then these next commands won't work,for varying reasons,
# cp Makefile acpi-handle-hack.c /usr/src/acpi-handle-hack-0.0.1 # cp dkms/acpi-handle-hack.conf /usr/src/acpi-handle-hack-0.0.1/dkms.conf # dkms add acpi-handle-hack/0.0.1 # dkms build acpi-handle-hack/0.0.1 # dkms install acpi-handle-hack/0.0.1

please help? the whole reason I purchased a laptop with a nvidia graphics card is so I could work with CUDA and this is preventing me from doing just that =(

---

### Post by m-tee on 2012-06-12
please provide also the output with error messages

---

### Post by pasoleatis on 2012-11-01
Hello,

I tried the hack mentioned above. The compilation had no errors, but at the end the module has to be put in a list to be loaded at boot. 
How can this be done on Ubuntu 12.04?? How to load a specific module automatically at boot?

---

