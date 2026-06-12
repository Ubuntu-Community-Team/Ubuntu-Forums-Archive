---
title: "Ubuntu 12.04 booting with purple (graphics artifacts) lines with NexStar 6G Usb 3.0"
date: 2017-01-07
forum: Hardware
---

### Post by helloworld1215 on 2017-01-07
[COLOR=#111111][FONT=Ubuntu]Question(s): How does one configure Ubuntu (whether by downloading drivers,updating Ubuntu to a particular version, debugging) to be able to boot and mount error free with this device attached?

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The Vantec NexStar 6G USB 3.0, can be attached when Ubuntu is booted. However, when booting the system with the device plugged into the USB 3.0 ports on the left side of this laptop ubuntu boots with:[/FONT][/COLOR]

[LIST=1]
[*]The purple color of Ubuntu's boot splash graphic appearing to be bleed into the boot messages. Parts of the boot messages are purple.
[*]Purple graphical artifact lines along the top of the screen. Booting into lightdm login results in the USB mouse being unusable I believe.
[/LIST]
[COLOR=#111111][FONT=Ubuntu]I am hesitant to continue to boot in this way because I think this is a power and or hardware incompatibility prior to getting some preliminary information to attempt to avoid any possible damage to the motherboard or USB ports.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]In addition there is a possibility that the USB 2.0 port on the opposite side of the laptop is either damaged, rusty or dirty. Plugging into it is a tight squeeze and a different USB enclosure had driver malfunctions (incorrect mount output and ls) issues.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have a Inspiron 3521 2011:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Specs [http://www.dell.com/support/home/us/en/04/product-support/servicetag/C9Q10X1/drivers](http://www.dell.com/support/home/us/en/04/product-support/servicetag/C9Q10X1/drivers)[/FONT][/COLOR]

---

### Post by DuckHook on 2017-01-07
My first recommendation would be to try Xenial. Precise (12.04) is at EoL and will no longer be supported. It is possible that an up-to-date kernel will itself solve your problem. If not, then at least you are no worse off than you now are. I would recommend first booting from a Xenial LiveUSB with your problematic USB drive *connected* and seeing if things go okay. If so, then you can kill two birds with one stone by simply upgrading.

I would recommend a full pristine install in your case. The path to Xenial from Precise for a network upgrade must run through Trusty and that's asking for a lot of things to go right to attain success. In all cases, to avert disaster, backup your data with proven restorable backups first.

---

### Post by helloworld1215 on 2017-01-07
Hehe, thank for the advice. I've decided to return this device and try with a Inatech.

---

