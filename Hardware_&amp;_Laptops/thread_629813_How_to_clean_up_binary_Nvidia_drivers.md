---
title: "How to clean up binary Nvidia drivers?"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by pollyp on 2007-12-02
Hi,

I had a 7.10 installation with the Nvidia-glx-new restricted driver working just fine on it. Then I was trying to track down a problem where vmplayer would work only with the nv driver, and ill-advisedly tried to install the drivers from nvidia.com to see if that would fix the problem. I couldn't get their drivers to work, so I gave up on that idea and tried to revert back to the restricted driver. But now I can't get that to work, either.

I've tried reinstalling nvidia-glx-new, and rebooting, but all it gives me is a single white screen. I've tried running the nvidia shell script's uninstall command, and then reinstalling nvidia-glx-new, but it gives me that same white screen. I don't see any noteworthy messages in my system logs. I can edit the xorg.conf to point me to the nv driver, and that works. But I miss my neat-o desktop effects. :^)

Does anyone know what I have to do to get nvidia-glx-new working again?

My video card is the GeForce 7600 GS. The nvidia driver I tried to install is 100.14.19. The restricted driver I would lik to get working again is 100.14.19+2.6.22.4-14.10. My machine is a 32-bit x86 machine.

Thanks in advance for your help.

---

### Post by pollyp on 2007-12-02
I have some success to report: I have desktop effects working with the nvidia-glx-new driver, The first thing I did was regenerate my xorg.conf file by removing the existing one and running nvidia-xconfig. The other thing I did was to find and remove some cruft from the machine's previous life as a Feisty Fawn machine and I was trying to get Fuzion going. I thought I had gotten it all, but I was wrong; I still the xserver-glx package lying around and causing trouble. Once I did those two things, then it was back to the land of rotating cubes. :^)

As an extra-special bonus, my vmware started working under compiz. This makes me very happy indeed.

---

