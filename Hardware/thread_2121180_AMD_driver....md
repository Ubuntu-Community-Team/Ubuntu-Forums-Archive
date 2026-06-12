---
title: "AMD driver..."
date: 2013-03-01
forum: Hardware
---

### Post by Spae on 2013-03-01
System gave me a message that it was using software rendering because something was wrong. I have the standard fglrx installed that comes with ubuntu but it seems bugged. That's why I am wanting to install from amds site.

Tried to install the driver on amds website like below but it doesn't work. It says one or more tools required for installation cannot be found on my system. Directs me to a log file
> Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-25-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

> 
chmod +x amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run 
./amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run

---

### Post by ajgreeny on 2013-03-01
Check that you have the kernel-headers and kernel-headers-generic for the kernel version you are using and see if that helps.

I suggest the easiest way to check such details is using synaptic, which you will need to install; I find the software-centre too simplified for me, but it's your choice.

---

### Post by Spae on 2013-03-01
Thanks. I should really know this by now. Stupidity isn't making a mistake but repeating it over and over :P.

Honestly there hasn't been a single time EVER that I haven't needed to install headers after installing ubuntu or debian. Usually someone gives me the version to install via terminal but I guess using synaptic means I don't have to know the version as the latest would be on there.

I don't know why this wouldn't just be installed with ubuntu though. It seems super strange to me.

Oh well, the latest driver from AMDs site works OK. So all's good.

---

