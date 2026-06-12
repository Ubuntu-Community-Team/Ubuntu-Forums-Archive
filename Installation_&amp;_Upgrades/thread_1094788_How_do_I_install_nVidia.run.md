---
title: "How do I install nVidia.run"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by limiz on 2009-03-12
I install NVIDIA-Linux-x86-180.29-pkg1.run to my desktop. But not sure how do i Install to the computer? Using kubuntu 8.10. Have a nVidia GeForce 6100.

---

### Post by cariboo on 2009-03-13
The 6100 is well supported, why not install the drivers from the repositories, Go to System--Adminnistration-->Hardware Drivers and install the recommended drivers.

If you really have to install the Nvidia drivers manually, remember you will have to do this for every kernel update. 

[list=1]
[*] Press Ctrl-ALt-F1
[*] At the prompt type:
```
sudo /etc/init.d/kdm stop
```
This will stop KDM

[*] cd to the directory that the .run file is located in, assuming it is located on the desktop type:
```
cd ~/Destop
```

[*] Next make the file executeable, type:
```
sudo chmod +x *run
```

This assumes you don't have any other .run files on your desktop.

[*] Now run the file:
```
sudo ./NVIDIA-Linux-x86-180.29-pkg1.run
```

You can shorten the above command to:
```
sudo ,/*run
```

if you don't have any other .run files on your on your desktop. Answer **yes** to all the question. Wait for the driver to finish compiling

[*] Restart KDM:
```
sudo /etc/init.d/kdm start
```

This should bring you back to your desktop, if not press Ctrl-ALt-F7
[/list]

Jim

---

