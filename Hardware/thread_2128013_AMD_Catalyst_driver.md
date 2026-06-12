---
title: "AMD Catalyst driver"
date: 2013-03-21
forum: Hardware
---

### Post by kobras on 2013-03-21
Hi!

I have a problem with installing Amd Catalyst driver. My notebook HP ProBook 4530s have two video cards, integrated and discrete (AMD Radeon HD 6490M).

I have download amd-driver-installer-catalyst-13.1-linux-x86.x86_64 and tried to install it. First I have got an error: "Check if system has the tools required for installation. fglrx installation requires that the system have kernel headers. /lib/modules/3.5.0-17-generic/build/include/linux/version.h cannot be found on this system."

After that I have run that driver with flag --force, and after installation finished get next message: "Supported adapter detected. Check if system has the tools required for installation. fglrx installation requires that the system have kernel headers. /lib/modules/3.5.0-17-generic/build/include/linux/version.h cannot be found on this system. fglrx installation is being forced. Installation will proceed without the required tools on the system. Uninstalling any previously installed drivers. Unloading radeon module... ERROR: Module radeon is in use Unloading drm module... ERROR: Module drm is in use by radeon,i915,ttm,drm_kms_helper [Message] Kernel Module : Trying to install a precompiled kernel module. [Message] Kernel Module : Precompiled kernel module version mismatched. [Error] Kernel Module : Kernel module build environment not found - please consult readme. [Reboot] Kernel Module : update-initramfs"

And after rebooting, I have get a message that system can be run only in low level graphic mode and I can work only with console. 

I have asked question also on askubuntu.com, but we haven't found a way to install this driver. Maybe someone knows soluton?

---

### Post by QIII on 2013-03-21
Is this a hybrid Intel/ATI combination of a dual ATI/ATI?

---

### Post by kobras on 2013-03-21
Intel/Ati

---

### Post by Yellow Pasque on 2013-03-21
Then general procedure is this: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

However, that may not work on Intel/ATI hybrid, or it may take additional configuration. I've read different things.. *shrug*

---

