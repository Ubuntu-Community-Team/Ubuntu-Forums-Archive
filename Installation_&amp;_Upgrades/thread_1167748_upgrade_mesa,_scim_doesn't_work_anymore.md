---
title: "upgrade mesa, scim doesn't work anymore"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by gjzeus on 2009-05-23
OS: ubuntu 9.04 ( upgrade from 8.10 )

$> wajig upgrade

2009-05-17 15:13:54 upgrade libgl1-mesa-dri 7.4-0ubuntu3 7.4-0ubuntu3.1
2009-05-17 15:13:54 status half-configured libgl1-mesa-dri 7.4-0ubuntu3
2009-05-17 15:13:54 status unpacked libgl1-mesa-dri 7.4-0ubuntu3
2009-05-17 15:13:54 status half-installed libgl1-mesa-dri 7.4-0ubuntu3
2009-05-17 15:13:55 status half-installed libgl1-mesa-dri 7.4-0ubuntu3
2009-05-17 15:13:56 status unpacked libgl1-mesa-dri 7.4-0ubuntu3.1
2009-05-17 15:13:57 status unpacked libgl1-mesa-dri 7.4-0ubuntu3.1
2009-05-17 15:13:57 upgrade libgl1-mesa-glx 7.4-0ubuntu3 7.4-0ubuntu3.1
2009-05-17 15:13:57 status half-configured libgl1-mesa-glx 7.4-0ubuntu3
2009-05-17 15:13:57 status unpacked libgl1-mesa-glx 7.4-0ubuntu3
2009-05-17 15:13:57 status half-installed libgl1-mesa-glx 7.4-0ubuntu3
2009-05-17 15:13:57 status half-installed libgl1-mesa-glx 7.4-0ubuntu3
2009-05-17 15:13:57 status unpacked libgl1-mesa-glx 7.4-0ubuntu3.1
2009-05-17 15:13:57 status unpacked libgl1-mesa-glx 7.4-0ubuntu3.1
2009-05-17 15:13:57 upgrade libglu1-mesa-dev 7.4-0ubuntu3 7.4-0ubuntu3.1
2009-05-17 15:13:57 status half-configured libglu1-mesa-dev 7.4-0ubuntu3
2009-05-17 15:13:57 status unpacked libglu1-mesa-dev 7.4-0ubuntu3
2009-05-17 15:13:57 status half-installed libglu1-mesa-dev 7.4-0ubuntu3
2009-05-17 15:13:58 status half-installed libglu1-mesa-dev 7.4-0ubuntu3
2009-05-17 15:13:58 status unpacked libglu1-mesa-dev 7.4-0ubuntu3.1
2009-05-17 15:13:58 status unpacked libglu1-mesa-dev 7.4-0ubuntu3.1
2009-05-17 15:13:58 upgrade libglu1-mesa 7.4-0ubuntu3 7.4-0ubuntu3.1
2009-05-17 15:13:58 status half-configured libglu1-mesa 7.4-0ubuntu3
2009-05-17 15:13:58 status unpacked libglu1-mesa 7.4-0ubuntu3
2009-05-17 15:13:58 status half-installed libglu1-mesa 7.4-0ubuntu3
2009-05-17 15:13:58 status half-installed libglu1-mesa 7.4-0ubuntu3
2009-05-17 15:13:58 status unpacked libglu1-mesa 7.4-0ubuntu3.1
2009-05-17 15:13:58 status unpacked libglu1-mesa 7.4-0ubuntu3.1
2009-05-17 15:13:58 upgrade libgl1-mesa-dev 7.4-0ubuntu3 7.4-0ubuntu3.1
2009-05-17 15:13:58 status half-configured libgl1-mesa-dev 7.4-0ubuntu3
2009-05-17 15:13:58 status unpacked libgl1-mesa-dev 7.4-0ubuntu3
2009-05-17 15:13:58 status half-installed libgl1-mesa-dev 7.4-0ubuntu3
2009-05-17 15:13:58 status half-installed libgl1-mesa-dev 7.4-0ubuntu3
2009-05-17 15:13:58 status unpacked libgl1-mesa-dev 7.4-0ubuntu3.1
2009-05-17 15:13:58 status unpacked libgl1-mesa-dev 7.4-0ubuntu3.1
2009-05-17 15:13:58 upgrade mesa-common-dev 7.4-0ubuntu3 7.4-0ubuntu3.1
2009-05-17 15:13:58 status half-configured mesa-common-dev 7.4-0ubuntu3
2009-05-17 15:13:58 status unpacked mesa-common-dev 7.4-0ubuntu3
2009-05-17 15:13:58 status half-installed mesa-common-dev 7.4-0ubuntu3
2009-05-17 15:13:59 status half-installed mesa-common-dev 7.4-0ubuntu3
2009-05-17 15:13:59 status unpacked mesa-common-dev 7.4-0ubuntu3.1
2009-05-17 15:13:59 status unpacked mesa-common-dev 7.4-0ubuntu3.1
2009-05-17 15:13:59 upgrade mesa-utils 7.4-0ubuntu3 7.4-0ubuntu3.1
2009-05-17 15:13:59 status half-configured mesa-utils 7.4-0ubuntu3
2009-05-17 15:13:59 status unpacked mesa-utils 7.4-0ubuntu3
2009-05-17 15:13:59 status half-installed mesa-utils 7.4-0ubuntu3
2009-05-17 15:13:59 status triggers-pending man-db 2.5.5-1build1
2009-05-17 15:13:59 status half-installed mesa-utils 7.4-0ubuntu3
2009-05-17 15:13:59 status half-installed mesa-utils 7.4-0ubuntu3
2009-05-17 15:13:59 status unpacked mesa-utils 7.4-0ubuntu3.1
2009-05-17 15:13:59 status unpacked mesa-utils 7.4-0ubuntu3.1
2009-05-17 15:13:59 upgrade libical0 0.43-2 0.43-2ubuntu1
2009-05-17 15:13:59 status half-configured libical0 0.43-2
2009-05-17 15:13:59 status unpacked libical0 0.43-2
2009-05-17 15:13:59 status half-installed libical0 0.43-2
2009-05-17 15:13:59 status half-installed libical0 0.43-2
2009-05-17 15:13:59 status unpacked libical0 0.43-2ubuntu1
2009-05-17 15:13:59 status unpacked libical0 0.43-2ubuntu1
2009-05-17 15:13:59 trigproc man-db 2.5.5-1build1 2.5.5-1build1
2009-05-17 15:13:59 status half-configured man-db 2.5.5-1build1
2009-05-17 15:14:00 status installed man-db 2.5.5-1build1
2009-05-17 15:14:02 startup packages configure
2009-05-17 15:14:02 configure libgl1-mesa-glx 7.4-0ubuntu3.1 7.4-0ubuntu3.1
2009-05-17 15:14:02 status unpacked libgl1-mesa-glx 7.4-0ubuntu3.1
2009-05-17 15:14:03 status half-configured libgl1-mesa-glx 7.4-0ubuntu3.1
2009-05-17 15:14:03 status installed libgl1-mesa-glx 7.4-0ubuntu3.1
2009-05-17 15:14:03 status triggers-pending libc6 2.9-4ubuntu6
2009-05-17 15:14:03 configure libgl1-mesa-dri 7.4-0ubuntu3.1 7.4-0ubuntu3.1
2009-05-17 15:14:03 status unpacked libgl1-mesa-dri 7.4-0ubuntu3.1
2009-05-17 15:14:03 status half-configured libgl1-mesa-dri 7.4-0ubuntu3.1
2009-05-17 15:14:03 status installed libgl1-mesa-dri 7.4-0ubuntu3.1
2009-05-17 15:14:03 configure libglu1-mesa 7.4-0ubuntu3.1 7.4-0ubuntu3.1
2009-05-17 15:14:03 status unpacked libglu1-mesa 7.4-0ubuntu3.1
2009-05-17 15:14:03 status half-configured libglu1-mesa 7.4-0ubuntu3.1
2009-05-17 15:14:03 status installed libglu1-mesa 7.4-0ubuntu3.1
2009-05-17 15:14:03 configure mesa-common-dev 7.4-0ubuntu3.1 7.4-0ubuntu3.1
2009-05-17 15:14:03 status unpacked mesa-common-dev 7.4-0ubuntu3.1
2009-05-17 15:14:03 status half-configured mesa-common-dev 7.4-0ubuntu3.1
2009-05-17 15:14:03 status installed mesa-common-dev 7.4-0ubuntu3.1
2009-05-17 15:14:03 configure libgl1-mesa-dev 7.4-0ubuntu3.1 7.4-0ubuntu3.1
2009-05-17 15:14:03 status unpacked libgl1-mesa-dev 7.4-0ubuntu3.1
2009-05-17 15:14:03 status half-configured libgl1-mesa-dev 7.4-0ubuntu3.1
2009-05-17 15:14:03 status installed libgl1-mesa-dev 7.4-0ubuntu3.1
2009-05-17 15:14:03 configure libglu1-mesa-dev 7.4-0ubuntu3.1 7.4-0ubuntu3.1
2009-05-17 15:14:03 status unpacked libglu1-mesa-dev 7.4-0ubuntu3.1
2009-05-17 15:14:03 status half-configured libglu1-mesa-dev 7.4-0ubuntu3.1
2009-05-17 15:14:03 status installed libglu1-mesa-dev 7.4-0ubuntu3.1
2009-05-17 15:14:03 configure mesa-utils 7.4-0ubuntu3.1 7.4-0ubuntu3.1
2009-05-17 15:14:03 status unpacked mesa-utils 7.4-0ubuntu3.1
2009-05-17 15:14:03 status half-configured mesa-utils 7.4-0ubuntu3.1
2009-05-17 15:14:03 status installed mesa-utils 7.4-0ubuntu3.1

After I upgrade those parts shown above, scim doesn't work anymore. It eats CPU usage(50%), memeory(40%). If I run in command-line, it just output zero all the times. So everytime I have to kill it after booting.

Any idea about how to fix it?  

BTW, I felt 8.10 was much stable than 9.04.

---

