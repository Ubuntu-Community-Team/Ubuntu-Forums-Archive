---
title: "kernel error while installing nvidia driver"
date: 2016-07-04
forum: Hardware
---

### Post by faraz_k86 on 2016-07-04
I have a toshiba tecra M2 laptop. It has the nvidia geforce FX go5200 graphics in it.

To install its driver I went here to download the correct display driver for my device: [http://www.nvidia.com/Download/driverResults.aspx/71302/en-us](http://www.nvidia.com/Download/driverResults.aspx/71302/en-us)

Then followed this guide step by step to install my driver: [http://www.allaboutlinux.eu/remove-nouveau-and-install-nvidia-driver-in-ubuntu-15-04/2/](http://www.allaboutlinux.eu/remove-nouveau-and-install-nvidia-driver-in-ubuntu-15-04/2/)

But I am given the error:

>     error: unable to build the nvidia kernel module.

I would appreciate some help. I want to install this legacy driver as I am getting problems while streaming videos and think maybe this driver fixes it.

---

### Post by X-RED_Tech on 2016-07-05
The legacy driver should be available directly in the official Ubuntu repositories if available.
The point is do not use the script from Nvidia, especially an old one that doesn't compile in the new kernels.

What is your Ubuntu release? Certainly not the 9.10 that shows in your profile...
Regardless of the (supported) release, you should always find the available drivers in "additional drivers". If it doesn't show 173 but newer ones try that. If not you'll have to work with the current open source driver.

---

