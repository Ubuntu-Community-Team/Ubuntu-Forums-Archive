---
title: "Increase Battery Life, Cool down Laptop Temperature, Configure Graphics"
date: 2011-10-14
forum: Hardware
---

### Post by razorxpress on 2011-10-14
**My Computer**: Dell, Sandy Bridge, Dual Graphics Card (Intel Integrated, AMD ATI)

**Introduction**: Ubuntu 11.04 did not have good support for sandy bridge computers. AMD released catalyst driver for Linux, but did not work on dual graphics cards (still cannot make it work on Ubuntu 11.10). However good side of Ubuntu 11.04 was 2.6.38 had good battery life compared to 3.0 kernels (although people claim bad battery started after 2.6.37) and the down side is the graphics was glitchy. The 3.0 kernels were at least able to run some high graphics applications with glitches, but they all were huge power hog. I upgraded to Ubuntu 11.10 hoping, that someone would have found a solution till the release. After I installed Ubuntu I was able to boot (In 11.04 I had to pass different acpi options to the kernel to boot). However as expected the computer was like in a burning fire. I even tried to switch to Unity-2D, gnome-panel none were able to bring down the power.

**Solution**:
I have applied quite different solutions to this problem and I think I am able to increase battery life by fair amount, laptop is silent and heat generation is quite low. These are the solutions I applied. May it help you all.

**1. Apply PCIE_ASPM**

(Source: Phoronix)

As everyone suggested adding this for laptops to have longer battery life. I edited /etc/default/grub as

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1"

and then running

$ sudo update-grub

Note: I previously had added acpi_osi=Linux pci=noacpi (on worst condition of black screen), which I think is no more required, because the computer boots on to GUI without them. Above command enables power management, sandy bridge support (rc6) and frame buffer compression.

**2. Apply Support for Hybrid Graphics**

(Source: Linux Hybrid Graphics)

For those of you who don't have two graphics card this step is not required. In Ubuntu 11.04 I had bug while installing this, so I could not run vgaswitcheroo/switch

**a. Install acpi_call**
$ sudo apt-get install git
$ cd /tmp
$ git clone [https://github.com/mkottman/acpi_call.git](https://github.com/mkottman/acpi_call.git)
$ cd acpi_call
$ make
$ sudo insmod acpi_call.ko
$ lscpi -vnnn | grep VGA     # Check status here
$ ./test_off.sh				 # Check for any line that says "it works"
$ lspci -vnnn | grep VGA     # Check with result of above

**b. byo-switheroo**  (Unplug the ac-cord and see if it changes the battery life)

$ git clone [https://github.com/awilliam/asus-switcheroo.git](https://github.com/awilliam/asus-switcheroo.git)
$ cd asus-switcheroo
$ make
$ sudo make install-ubuntu
$ sudo su -
# cat /sys/kernel/debug/vgaswitcheroo/switch
# echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

It is temporary. If you have two graphics cards next time you boot, you will see both cards have Pwr set. If you want this to be permanent add the discrete card (e.g ati as blacklist). This settings will only enable the default intel card and disable other card. I haven't found yet a solution to flawlessly switch intel and ati cards. The better solution would be ati card using dedicated applications via catalyst control center.

$ sudo vi /etc/modprobe.d/blacklist.conf

Add a line at last

blacklist radeon

Then edit /etc/rc.local as
$ vi /etc/rc.local

Make the part after comments look like this

modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

exit 0

**3. Install Jupiter**
Jupiter is a power management tool for laptops. It has options to switch between maximum and high performance and power saving mode. 
$ sudo add-apt-repository ppa:webupd8team/jupiter
$ sudo apt-get update
$ sudo apt-get install jupiter

**4. Install powertop**
Powertop is a tool that helps you see and somehow configure most waking applications. You can see which programs you have been running. E.g May be Clementine is running in back. You did not close firefox even when you did not need it.

$ sudo apt-get install powertop
$ sudo powertop

See Overview of Processes that are running. Using right arrow on keyboard go to Tunables tab. I assume by toggling processes to Good we can stop them on battery mode to save power. E.g By toogling "Changing Autosuspend for USB device USB Optical Mouse (Logitech)" to Good I was able to actually poweroff the lights on USB Mouse. When I toogle it to Bad it lighted back. This is a serious powersaver. Unless you need thinks like USB 3.0, webcam and similar stuffs its good to have them shut down, when on battery.

NOTE: When your AC power is back don't forget to toogle the needed modules back to Bad, else you might wonder what went wrong with your WebCam and why doesn't the Flashdrive work. Though if you restart the computer everything should come back to normal.

**5. Install lm-sensors**
I still cannot figure out if fancontrol (based on lm-sensors) is used to control external laptop fans (plugged via usb) or internal fan, but lm-sensors can do other interesting things too. It had helped to cool down my laptop by controlling the high spinning fan. So, this is the first tool I would install on any Linux Laptop.

$ sudo apt-get install lm-sensors
$ sudo sensors-detect

Type YES for everything, because you want to scan for all hardware (actually except last option everything defaults to YES). It scans for some time and figures out what modules you can add to your current hardware. At last step you can type YES to allow sensors-detect to add those modules to your /etc/modules or you can do it yourself when you know what to add. In my case I was suggested three modules. i.e coretemp, max6650, sbs. However in Ubuntu 11.04 only coretemp had appeared (its a strange world).

**6. Dell related and others.**
If I search synaptic package manager for laptop and dell I see some interesting software options. One I see is i8kutils. The i8kutils is wrapper for i8k kernel module. Since the ubuntu kernel does not include i8k module I have to compile the kernel with this module to see what it does. Another similar package is called apmd and its front end xapm. Since apmd too isn't included I have to compile the kernel to see what it does. Another particular important one is laptop-mode-tools. I hope laptop-detect is already installed by default. Some of the modules that I find running are dell_wmi, dell_laptop. You will have to figure out these specially i8kutils and apmd yourself because I haven't tested them yet. 

**Conclusion:**
I have managed to get lot more battery life now with these settings, though the battery indicator does not show the correct time.

If you have some modifications or suggestions to above article please feel free to submit your solutions or modifications (if something from above did not work).

---

### Post by jozeph78 on 2011-10-14
I'm here just for the gfx switching, the awesome battery tricks are a superb bonus too. Thx!

Can't wait to try this out on my hp dv6qe. Getting graphics to work on  this machine has been a bitch. Time wasted is amounting to more than I  would have spent just buying a 17" MBP. Really pissed at the crappy  drivers provided by ATI. 

Oh, did you install the fglrx or prop Catalyst drivers? Which version (11.8, 11.9)? Thanks!

---

### Post by razorxpress on 2011-10-14
I actually was about to screw the ubuntu installation with the catalyst driver. It does not work. I tried both (fglrx and Catalyst 11.9), but they don't work. They both seem to install but after they are installed 3D is gone. The echo OFF > /sys/kernel/debug/vgaswitcheroo/switch only disables the discrete graphics card (ati). Actually my integrated card is quite good too, so I don't bother much to install ati. I use the xserver-xorg-video-intel and xserver-xorg-video-ati (to keep ati happy, I have totally disabled it) and mesa for 3D graphics. I can still play Nexuiz and Alien-Arena (so its fine). If I have both cards at power the ati card is the one that makes the fan go wild.

---

### Post by collisionystm on 2011-10-14
I had a Vostro 3750 with the i3 Sandy Bridge.

It was awesome and handled ubuntu perfectly. Also fedora 15.

Intel is not the problem. ATI is the problem. AMD flat out sucks.

---

### Post by razorxpress on 2011-10-14
@collisionystm Sometimes it feels good to blame intel. They haven't supported sandy bridge equally as in other platforms. They have made it fairly usable recently but is still way below in performance than their driver releases in other platforms for sandy bridge. People can run fairly high quality games on Intel HD 3000 (the one that comes in sandy bridge) on other platforms but on Ubuntu it still cannot even run the benchmarking tool Unigine_Heaven. Graphics performance are still not up to the mark, they should be, but they are improving (good work, still a large way to go). In this case AMD is the primary culprit not taking care of dual graphics situation (which is default in new processors, if it comes with ATI too).

---

### Post by collisionystm on 2011-10-15
> **razorxpress said:**
> @collisionystm Sometimes it feels good to blame intel. They haven't supported sandy bridge equally as in other platforms. They have made it fairly usable recently but is still way below in performance than their driver releases in other platforms for sandy bridge. People can run fairly high quality games on Intel HD 3000 (the one that comes in sandy bridge) on other platforms but on Ubuntu it still cannot even run the benchmarking tool Unigine_Heaven. Graphics performance are still not up to the mark, they should be, but they are improving (good work, still a large way to go). In this case AMD is the primary culprit not taking care of dual graphics situation (which is default in new processors, if it comes with ATI too).

Well in all fairness, Intel does a good job of making sure usable drivers are packaged into the Linux Kernel. They may not be up to par with performance yet, but who is to say that is not a linux problem? Nvidia and ATI run higher benchmarks on Linux because everyone installs the proprietary driver. I guess it just is what it is

---

