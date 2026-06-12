---
title: "Cannot install Nvidia Drivers"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by Dr Zolygon on 2007-07-08
Hi

    Im new to linux and am having trouble getting a nvidia driver to install.

I have an 8800gts and i trying to install this driver [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

I have a read a few guides online but nothing seems to help.

I exited out of xserver and installed the nvidia driver and ran nvidia-xconfig yet i still get the x fails to load error. I have the driver unrestricted.

I just don't know what to do.

Any help is appreciated. Thanks.

---

### Post by kingof1981 on 2007-07-08
maybe it's the wrong driver
try this...
sudo apt-get update
sudo apt-get install nvidia-glx

restart x

ctrl+alt+backspace

---

### Post by Dr Zolygon on 2007-07-08
Thanks for the response.


When i do sudo apt-get install nvidia-glx its says,


"nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

So i guess that wasn't my problem.

Any other ideas?

---

### Post by Dr Zolygon on 2007-07-08
I read a few posts suggesting to manually install the 9755 drivers for my card.

During installation it comes up with an error saying,

"The installer has encountered the follwing error during installation: 'cannot create symlink /usr/lib/xorg/modules/libwfb.so(file exists).' continue anyway?"

I tried continuing but after the installation is complete i get an error from the xserver upon startup.

"Failed to load Nvidia Kernel Module"

Hopefully this helps.

---

### Post by jimbob on 2007-07-08
On a root terminal  try running apt-get install linux-restricted-modules-$(uname -r)

Then run dpkg-reconfigure -phigh xserver-xorg and restart gdm,

/etc/init.d/gdm restart
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by l-fever on 2007-07-08
Good info here:

[http://ubuntuforums.org/showthread.php?t=301499]("http://ubuntuforums.org/showthread.php?t=301499")


I have had good luck with the envy script as well.

---

### Post by Dr Zolygon on 2007-07-08
> **l-fever said:**
> Good info here:

[http://ubuntuforums.org/showthread.php?t=301499]("http://ubuntuforums.org/showthread.php?t=301499")


I have had good luck with the envy script as well.

Thank you for the link. It works! Thank you everyone who helped.

---

### Post by l-fever on 2007-07-08
> **Dr Zolygon said:**
> Thank you for the link. It works! Thank you everyone who helped.

Sweet! :biggrin:

---

### Post by dragonwings on 2007-07-08
[http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver](http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver)

---

