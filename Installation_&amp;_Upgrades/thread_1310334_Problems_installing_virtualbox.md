---
title: "Problems installing virtualbox"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by JonCage on 2009-11-01
I'm having some problems installing virtual box (v3.0.10) on the latest version of Ubuntu (9.10).

```
jon@uberserver:/usr/src#  sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                                              *  done.
 * Recompiling VirtualBox kernel module
 * Look at /var/log/vbox-install.log to find out what went wrong
```

Looking at the log says:

```
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

uname -r gives me:

```
2.6.31-020631rc9-generic
```

...now the problem is that there don't appear to be headers available for the latest build!?

```
v   linux-headers                                                    -
v   linux-headers-2.6                                                -
i   linux-headers-2.6.27-9                                           - Header files related to Linux kernel version 2.6.27
i   linux-headers-2.6.27-9-core2                                     - Linux kernel headers for version 2.6.27 on x86/x86_64
i   linux-headers-2.6.31-020631rc9                                   - Header files related to Linux kernel version 2.6.31
p   linux-headers-2.6.31-14                                          - Header files related to Linux kernel version 2.6.31
p   linux-headers-2.6.31-14-386                                      - Linux kernel headers for version 2.6.31 on i386
p   linux-headers-2.6.31-14-generic                                  - Linux kernel headers for version 2.6.31 on x86/x86_64
p   linux-headers-2.6.31-14-generic-pae                              - Linux kernel headers for version 2.6.31 on x86
p   linux-headers-2.6.31-302                                         - Header files related to Linux kernel version 2.6.31
p   linux-headers-2.6.31-302-ec2                                     - Linux kernel headers for version 2.6.31 on x86/x86_64
p   linux-headers-2.6.31-9-rt                                        - Linux kernel headers for version 2.6.31 on Ingo Molnar's full real time pre
i   linux-headers-2.6.31-999                                         - Header files related to Linux kernel version 2.6.31
i   linux-headers-2.6.31-999-generic                                 - Linux kernel headers for version 2.6.31 on x86/x86_64
p   linux-headers-386                                                - Generic Linux kernel headers
p   linux-headers-ec2                                                - Linux kernel headers for ec2 machines
p   linux-headers-generic                                            - Generic Linux kernel headers
p   linux-headers-generic-pae                                        - Generic Linux kernel headers
v   linux-headers-lbm                                                -
v   linux-headers-lbm-2.6                                            -
p   linux-headers-lbm-2.6.31-14-generic                              - Header files related to linux-backports-modules version 2.6.31
p   linux-headers-lbm-2.6.31-14-generic-pae                          - Header files related to linux-backports-modules version 2.6.31
p   linux-headers-rt                                                 - Rt Linux kernel headers
p   linux-headers-server                                             - Linux kernel headers on Server Equipment.
p   linux-headers-virtual                                            - Linux kernel headers for virtual machines

```

The closest match as far as I can see is linux-headers-2.6.31-020631rc9 but how do I tell the virtual box installer to use those instead? I can't see where I'm supposed to put the "KERN_DIR=" setting.. ?

---

### Post by mikewhatever on 2009-11-01
How about linux-headers-2.6.31-14-generic? The package is not installed, so give it a try.

---

