---
title: "need help, Acer Aspire 4740G VGA driver"
date: 2010-04-03
forum: Hardware
---

### Post by Neo Android on 2010-04-03
Hi,

I recently migrate from wi**ows to ubuntu 9.10. My laptop is Acer Aspire 4740G which VGA is Nvidia GeForce 310M. I need the VGA driver. Please help me.

Sorry about my english.

---

### Post by Fafler on 2010-04-03
Go to System -> Administration -> Hardware Drivers and enable the binary Nvidia driver.

---

### Post by Neo Android on 2010-04-03
> **Fafler said:**
> Go to System -> Administration -> Hardware Drivers and enable the binary Nvidia driver.

I've tried this method, but after I restart my laptop, i just see the black screen appear.

---

### Post by byStanderone on 2010-04-03
...well, this is a recurrent question about nvidia and there are clearer and concise explanations out there, but this is how i did it on my box:

- system > administration > clik on hardware drivers
(hardware drivers is installed by default, if not you can install it using the ubuntu software center found under applications use the gtk version)

-once you have your nvidia driver installed, 
sudo dpkg-reconfigure -phigh xserver-xorg

- then: sudo nvidia-xconfig 

- reboot

- once you have rebooted, check if you have nvidia x server settings in 
system > administration...if not, sudo apt-get install nvidia-settings

if installed, adjust your display preferences using it.


NOTE: new xservers (such as of karmic) may not require a xorg.conf file, it uses dbus for its devices...but having an nvidia for graphics...would still require an xorg.conf file, and it is still supported by karmic.

hence the need to still edit the xorg.conf so as to implement the needed preferences that are required. by not specifying your chosen resolutions, the system will default to a lower one....hence the need to list the range of allowed resolutions in the xorg.conf file, with due notice to the higher limit in particular, considering the resolution range of the monitor that is attached to the card. average small screen lcd monitors would probably have a max resolution of 1360x768 , depending on the make and model.

edit this line in your xorg.conf file under the heading as shown in the example below: (of course you can list higher resolutions as per your monitor's capability)

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1360x768" "1024x768" "800x600" "640x480"
    EndSubSection


...as an added safety, had also specified the vertical and horizontal frequency range, there are monitors that would shutdown once their frequency thresholds are exceeded : (hence the need to know your monitor and edit this section as per your specs)

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 81.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

---

