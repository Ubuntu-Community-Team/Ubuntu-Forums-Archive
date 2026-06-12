---
title: "No Sound drivers after rt kernel update AMD64"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by gratefulfrog on 2009-03-27
Hi!
After years with no problems, the last kernel update from 8.04 on AMD64 (rt-kernel) left me with no sound device. When I click the volume control I get:

No volume control GStreamer plugins and/or devices found.

I tried this to check the kernel installed:

```
$ aptitude search linux-headers 
v   linux-headers                                      -                                                             
v   linux-headers-2.6                                  -                                                             
i   linux-headers-2.6.11-1                             - Header files related to Linux kernel version 2.6.11         
p   linux-headers-2.6.24-16                            - Header files related to Linux kernel version 2.6.24         
p   linux-headers-2.6.24-16-generic                    - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-16-openvz                     - Linux kernel headers for version 2.6.24 on OpenVZ Virtualiza
p   linux-headers-2.6.24-16-rt                         - Linux kernel headers for version 2.6.24 on Ingo Molnar's ful
p   linux-headers-2.6.24-16-server                     - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-16-xen                        - Linux kernel headers for version 2.6.24 on This kernel can b
p   linux-headers-2.6.24-18                            - Header files related to Linux kernel version 2.6.24         
p   linux-headers-2.6.24-18-generic                    - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-18-openvz                     - Linux kernel headers for version 2.6.24 on OpenVZ Virtualiza
p   linux-headers-2.6.24-18-rt                         - Linux kernel headers for version 2.6.24 on Ingo Molnar's ful
p   linux-headers-2.6.24-18-server                     - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-18-xen                        - Linux kernel headers for version 2.6.24 on This kernel can b
p   linux-headers-2.6.24-19                            - Header files related to Linux kernel version 2.6.24         
p   linux-headers-2.6.24-19-generic                    - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-19-openvz                     - Linux kernel headers for version 2.6.24 on OpenVZ Virtualiza
p   linux-headers-2.6.24-19-rt                         - Linux kernel headers for version 2.6.24 on Ingo Molnar's ful
p   linux-headers-2.6.24-19-server                     - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-19-xen                        - Linux kernel headers for version 2.6.24 on This kernel can b
i   linux-headers-2.6.24-20                            - Header files related to Linux kernel version 2.6.24         
i   linux-headers-2.6.24-20-generic                    - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-20-openvz                     - Linux kernel headers for version 2.6.24 on OpenVZ Virtualiza
p   linux-headers-2.6.24-20-rt                         - Linux kernel headers for version 2.6.24 on Ingo Molnar's ful
p   linux-headers-2.6.24-20-server                     - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-20-xen                        - Linux kernel headers for version 2.6.24 on This kernel can b
i   linux-headers-2.6.24-21                            - Header files related to Linux kernel version 2.6.24         
i   linux-headers-2.6.24-21-generic                    - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-21-openvz                     - Linux kernel headers for version 2.6.24 on OpenVZ Virtualiza
p   linux-headers-2.6.24-21-rt                         - Linux kernel headers for version 2.6.24 on Ingo Molnar's ful
p   linux-headers-2.6.24-21-server                     - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-21-xen                        - Linux kernel headers for version 2.6.24 on This kernel can b
i   linux-headers-2.6.24-22                            - Header files related to Linux kernel version 2.6.24         
i   linux-headers-2.6.24-22-generic                    - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-22-openvz                     - Linux kernel headers for version 2.6.24 on OpenVZ Virtualiza
p   linux-headers-2.6.24-22-rt                         - Linux kernel headers for version 2.6.24 on Ingo Molnar's ful
p   linux-headers-2.6.24-22-server                     - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-22-xen                        - Linux kernel headers for version 2.6.24 on This kernel can b
i   linux-headers-2.6.24-23                            - Header files related to Linux kernel version 2.6.24         
i   linux-headers-2.6.24-23-generic                    - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-23-openvz                     - Linux kernel headers for version 2.6.24 on OpenVZ Virtualiza
p   linux-headers-2.6.24-23-rt                         - Linux kernel headers for version 2.6.24 on Ingo Molnar's ful
p   linux-headers-2.6.24-23-server                     - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-23-xen                        - Linux kernel headers for version 2.6.24 on This kernel can b
i   linux-headers-2.6.24-24                            - Header files related to Linux kernel version 2.6.24         
i   linux-headers-2.6.24-24-generic                    - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-24-openvz                     - Linux kernel headers for version 2.6.24 on OpenVZ Virtualiza
p   linux-headers-2.6.24-24-rt                         - Linux kernel headers for version 2.6.24 on Ingo Molnar's ful
p   linux-headers-2.6.24-24-server                     - Linux kernel headers for version 2.6.24 on x86/x86_64       
p   linux-headers-2.6.24-24-xen                        - Linux kernel headers for version 2.6.24 on This kernel can b
p   linux-headers-amd64-generic                        - Upgrade dummy package. Can be removed                       
p   linux-headers-amd64-k8                             - Upgrade dummy package. Can be removed                       
p   linux-headers-amd64-server                         - Upgrade dummy package. Can be removed                       
p   linux-headers-amd64-xeon                           - Upgrade dummy package. Can be removed                       
i   linux-headers-generic                              - Generic Linux kernel headers                                
v   linux-headers-lbm                                  -                                                             
v   linux-headers-lbm-2.6                              -                                                             
p   linux-headers-lbm-2.6.24-16-generic                - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-16-openvz                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-16-rt                     - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-16-server                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-16-xen                    - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-18-generic                - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-18-openvz                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-18-rt                     - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-18-server                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-18-xen                    - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-19-generic                - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-19-openvz                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-19-rt                     - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-19-server                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-19-xen                    - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-20-generic                - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-20-openvz                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-20-rt                     - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-20-server                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-20-xen                    - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-21-generic                - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-21-openvz                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-21-rt                     - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-21-server                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-21-xen                    - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-22-generic                - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-22-openvz                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-22-rt                     - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-22-server                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-22-xen                    - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-23-generic                - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-23-openvz                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-23-rt                     - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-23-server                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-23-xen                    - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-24-generic                - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-24-openvz                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-24-rt                     - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-24-server                 - Header files related to linux-backports-modules version 2.6.
p   linux-headers-lbm-2.6.24-24-xen                    - Header files related to linux-backports-modules version 2.6.
v   linux-headers-lum                                  -                                                             
v   linux-headers-lum-2.6                              -                                                             
p   linux-headers-lum-2.6.24-16-generic                - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-16-openvz                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-16-rt                     - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-16-server                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-16-xen                    - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-18-generic                - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-18-openvz                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-18-rt                     - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-18-server                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-18-xen                    - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-19-generic                - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-19-openvz                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-19-rt                     - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-19-server                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-19-xen                    - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-20-generic                - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-20-openvz                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-20-rt                     - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-20-server                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-20-xen                    - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-21-generic                - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-21-openvz                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-21-rt                     - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-21-server                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-21-xen                    - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-22-generic                - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-22-openvz                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-22-rt                     - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-22-server                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-22-xen                    - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-23-generic                - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-23-openvz                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-23-rt                     - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-23-server                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-23-xen                    - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-24-generic                - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-24-openvz                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-24-rt                     - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-24-server                 - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-lum-2.6.24-24-xen                    - Header files related to linux-ubuntu-modules version 2.6.24 
p   linux-headers-openvz                               - openvz Linux kernel headers                                 
p   linux-headers-rt                                   - rt Linux kernel headers                                     
p   linux-headers-server                               - Linux kernel headers on Server Equipment.                   
p   linux-headers-xen                                  - xen Linux kernel headers 
```        

The alsa-mixer shows nothing, no controls.

I have no idea what to do to get sound back.

Any ideas would be great!
thanks,
GF.

---

