---
title: "Resume fails unless laptop is plugged in"
date: 2009-06-26
forum: Hardware
---

### Post by michaeljmcd on 2009-06-26
I am running Kubuntu 9.04 on a Compaq Presario F700 laptop. At present, I have a problem where resume fails unless the laptop is plugged into the AC Adapter. It suspends either way. If it is plugged in, it will resume. If not, the lights will come on, but the backlight remains off and the laptop never fully resumes. 

The install is a clean one, except that I have added ath5k to SUSPEND_MODULES, added the nvidia drivers (which I do not believe is the issue, otherwise the suspend/resume would fail always and I have been able to suspend/resume with this driver in past versions of Ubuntu, like 8.04), and added hpet=disable to the kernel options. Suspend/resume fails unless ath5k is removed first. The nvidia drivers were added because I am weak and like my eye candy :) hpet=disable was added to the kernel options because, if it is not, the startup will freeze until a key is hit (or held down, because it must be done many times sequentially). On older kernels, this was not necessary, but on recent distro releases (for Ubuntu, PCLinuxOS, and Fedora) it is. I was wondering whether anyone knew what to do to get this working 100%.

---

### Post by michaeljmcd on 2009-06-29
Has anyone else observed this?

---

### Post by michaeljmcd on 2009-07-12
In case anyone else comes across this problem, I solved it by upgrading the kernel to either 2.6.29 or 2.6.30 (running 2.6.30 now). Some notes on how to do this can be found:

[http://joshuaredstone.blogspot.com/2009/06/jaunty-and-2630-kernel-with-nvidia.html]("http://joshuaredstone.blogspot.com/2009/06/jaunty-and-2630-kernel-with-nvidia.html")

Since it works on an earlier kernel (whichever shipped with Ubuntu 8.04) and these two later ones, I assume it is a bug in the versions of the kernel that shipped with Ubuntu 8.10 and 9.04.

---

