---
title: "Installing older Nvidia driver"
date: 2014-10-24
forum: Hardware
---

### Post by Ferhad_Fidan on 2014-10-24
Hi. I've been a Kubuntu user for a year. I use it on my Nvidia Optimus notebook using the Bumblebee daemon. I run Boinc on it and crunch Gpugrid.net works. Today I stopped the Boinc and backed up its data and installed Kubuntu 14.10. The best Nvidia driver for running Gpugrid works is Nvidia 331.38. In the 14.10 repos there is Nvidia 331.89 version, which can't run Boinc GPU works. Boinc says Nvidia drivers present but there is no GPU. Because of this I wanted to install Nvidia 331.38 drivers but can't.
I added Trusty repos and can see the Nvidia 331.38 drivers in Muon. However, when I try to install them by clicking the force to version button the newest 331.89 driver is installed. And that is problematic as I said. I tried downloading and installing them, but dpkg says xorg-video-abi-11/15 is missing. It's a virtual package provided by other packages but can't succeed installing it and installing the driver.
The driver from Nvidia website is a *.run file and doesn't run under Bumblebee. So I need it from a repository.

How can I install the propriatery Nvidia 331.38 driver? Is there some repos have them? Xedgers removed 331.38 version and has the 331.89 one.

---

