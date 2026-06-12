---
title: "Optimus problems with Boinc"
date: 2014-12-11
forum: Hardware
---

### Post by Ferhad_Fidan on 2014-12-11
I have Lenovo Z510 Optimus notebook. I was crunching on Gpugrid Boinc project since I bought it with Nvidia 331 drivers. However, lately project upgraded to CUDA6 jobs which needs Nvidia-343 drivers and I started to have problems. Firstly Boinc couldn't detect the CUDA support, I solved by installing nvidia-modprobe package and changing to /usr/lib/nvidia-343/ld.so.conf  variable in /usr/lib/nvidia-343/ld.so.conf  from /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf . To do this I run the command below, select 0 or 2 and run sudo ldconfig:"sudo update-alternatives --config x86_64-linux-gnu_gl_conf" However, when I restart the notebook, path is returned to mesa path (/usr/lib/x86_64-linux-gnu/mesa/ld.so.conf ). Then I need to rerun update-alternatives command and select Nvidia driver paths.Now, how I can fix this x86_64-linux-gnu_gl_conf to /usr/lib/nvidia-343/ld.so.conf path? Or how I can run the application with a specific path. I tried the command below but the same result, probably it's something else I don't know: "/lib/x86_64-linux-gnu/ld-2.19.so --library-path /usr/lib/nvidia-343/ld.so.conf /usr/bin/optirun /media/sis651/BOINC-DRIVE/BOINC/run_manager" Also when I quit boinc I need to run the codes below to switch off the discrete Nvidia GPU:sudo rmmod nvidia_uvmsudo rmmod nvidiasudo tee /proc/acpi/bbswitchHow I can make it switch off automatically? I have Kuubuntu 14.10 and it is the same in 14.04 too. --Sorry for the view, editor always saves it without line brakes.

---

