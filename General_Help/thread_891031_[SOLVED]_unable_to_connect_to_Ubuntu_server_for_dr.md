---
title: "[SOLVED] unable to connect to Ubuntu server for driver update"
date: 2008-08-15
forum: General Help
---

### Post by eckeroo on 2008-08-15
When I try and update a proprietary driver for my graphics card, It fails to download and I get the following error message:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.13-18.41_i386.deb)
  404 Not Found

Even though it fails to install, a 'system restart required' icon appears in the tool tray.

My internet connection does work, I can browse on firefox and my synaptic package manager can still download.

Is the Ubuntu server temporarily down?

Regards

---

### Post by jerome1232 on 2008-08-15
That site works put that particular package doesn't exist
[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/)
so i'm not sure why it's looking for that package
> [   ] nvidia-glx-dev_96.43.05+2.6.24.12-16.34_amd64.deb                       11-Apr-2008 02:03  179K  
[   ] nvidia-glx-dev_96.43.05+2.6.24.12-16.34_i386.deb                        11-Apr-2008 02:04  160K  
[   ] nvidia-glx-dev_96.43.05+2.6.24.13-19.45_amd64.deb                       09-Jul-2008 18:06  180K  
[   ] nvidia-glx-dev_96.43.05+2.6.24.13-19.45_i386.deb                        09-Jul-2008 18:06  161K  
[   ] nvidia-glx-dev_96.43.05+2.6.24.14-21.47_amd64.deb                       14-Aug-2008 17:04  180K  
[   ] nvidia-glx-dev_96.43.05+2.6.24.14-21.47_i386.deb                        14-Aug-2008 17:05  161K  
[   ] nvidia-glx-new-dev_169.12+2.6.24.12-16.34_amd64.deb                     11-Apr-2008 02:03  167K  
[   ] nvidia-glx-new-dev_169.12+2.6.24.12-16.34_i386.deb                      11-Apr-2008 02:04  151K  
[   ] nvidia-glx-new-dev_169.12+2.6.24.13-19.45_amd64.deb                     09-Jul-2008 18:06  168K  
[   ] nvidia-glx-new-dev_169.12+2.6.24.13-19.45_i386.deb                      09-Jul-2008 18:06  152K  
[   ] nvidia-glx-new-dev_169.12+2.6.24.14-21.47_amd64.deb                     14-Aug-2008 17:04  168K  
[   ] nvidia-glx-new-dev_169.12+2.6.24.14-21.47_i386.deb                      14-Aug-2008 17:05  152K  
[   ] nvidia-glx-new_169.12+2.6.24.12-16.34_amd64.deb                         11-Apr-2008 02:03  8.9M  
[   ] nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb                          11-Apr-2008 02:04  5.0M  
[   ] nvidia-glx-new_169.12+2.6.24.13-19.45_amd64.deb                         09-Jul-2008 18:06  8.9M  
[   ] nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb                          09-Jul-2008 18:06  5.0M  
[   ] nvidia-glx-new_169.12+2.6.24.14-21.47_amd64.deb                         14-Aug-2008 17:04  8.9M  
[   ] nvidia-glx-new_169.12+2.6.24.14-21.47_i386.deb                          14-Aug-2008 17:05  5.0M  
[   ] nvidia-glx_96.43.05+2.6.24.12-16.34_amd64.deb                           11-Apr-2008 02:03  7.0M  
[   ] nvidia-glx_96.43.05+2.6.24.12-16.34_i386.deb                            11-Apr-2008 02:04  3.7M  
[   ] nvidia-glx_96.43.05+2.6.24.13-19.45_amd64.deb                           09-Jul-2008 18:06  7.0M  
[   ] nvidia-glx_96.43.05+2.6.24.13-19.45_i386.deb                            09-Jul-2008 18:06  3.7M  
[   ] nvidia-glx_96.43.05+2.6.24.14-21.47_amd64.deb                           14-Aug-2008 17:04  7.0M  
[   ] nvidia-glx_96.43.05+2.6.24.14-21.47_i386.deb                            14-Aug-2008 17:05  3.7M  


---

### Post by eckeroo on 2008-08-16
It's sorted now.

All I needed to do was to run the updates from the synaptic package manager.

The proprietary driver then updated fine. I'm assuming after the updates, it looked for another file.

:)

---

