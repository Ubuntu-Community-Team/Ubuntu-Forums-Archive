---
title: "I cannot install the nvidia proprietary drivers on Ubuntu. What do I do?"
date: 2022-03-09
forum: Hardware
---

### Post by fordie2 on 2022-03-09
[IMG]https://i.redd.it/spshk46mscm81.png[/IMG]

---

### Post by TheFu on 2022-03-09
Remove the failed drivers. Use the F/LOSS drivers. Let nvidia know about your dissatisfaction. Give your money to a different vendor next time.

For the last 3 yrs, the way to install proprietary GPU drivers is by using the **ubuntu-drivers** tool. I think there is a GUI version, but I've never used it.  It used to support
```
sudo ubuntu-drivers autoinstall
```
which handled everything.  I've read that in 21.10 and later, the autoinstall option has been removed.

Please don't post huge images to the forums. Some people pay by the byte to read stuff here and the image is so tiny I cannot read it anyway.  Text should be posted AS TEXT, inside forum code tags. This makes it easier for people to help.

---

### Post by Tadaen_Sylvermane on 2022-03-10
[https://www.nvidia.com/download/driverResults.aspx/181274/en-us](https://www.nvidia.com/download/driverResults.aspx/181274/en-us)

This may work. The greyed out options on the screenshot likely means your hardware is too new and the proper driver has not been added to your version of Ubuntu thus far.  As the TheFu said, this is an Nvidia problem, not Ubuntu.

These days AMD is the go to choice for Linux. The mesa drivers for it are written with help from AMD whereas Nvidia tells us to go to hell. I'm glad I picked up a modest / decent Radeon card before this shortage rather than an Nvidia card.

---

### Post by TheFu on 2022-03-10
AMD F/LOSS drivers are actually first class, unlike nvidia.  Some proof: [https://www.phoronix.com/scan.php?page=article&item=radeon-spvp2020-linux](https://www.phoronix.com/scan.php?page=article&item=radeon-spvp2020-linux)  
Of course, if you need a high-end GPU, then nvidia is the current leader and dealing with those issues on the 3080 and 3090 lines is just par for the vendor.

---

### Post by Yellow Pasque on 2022-03-10
> **Tadaen_Sylvermane said:**
> The greyed out options on the screenshot likely means your hardware is too new and the proper driver has not been added to your version of Ubuntu thus far.

Agreed. However, instead of trying to download and install the driver from Nvidia's site, the user should use this PPA for newer Nvidia drivers: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

OP - If you need further assistance on which driver version to install, let us know exactly what GPU you have.
```
sudo update-pciids
lspci | grep -i nvidia
```

---

### Post by pissedoffdude on 2022-03-18
Sounds like you installed the drivers from the .run file provided by NVIDIA.  If you have a copy of it, simply run:

sudo ./nvidia-installer.run --uninstall

Or grab the latest one from nvidia's site, and then use the above command, replacing 'nvidia-installer.run' with the filename of the one you downloaded.  You should also sudo chmod +x <fiilename>.run prior to doing the above.  Once complete, reboot and you'll most likely be using the nouveau driver.  If for some reason the GUI doesn't come up on reboot, you can run:

# get available drivers:
sudo ubuntu-drivers devices

Once you locate the latest driver in the list from above, install it using apt-get, e.g.
sudo apt install nvidia-###-updates

And once installed go ahead and reboot

Best,
Gabe

---

