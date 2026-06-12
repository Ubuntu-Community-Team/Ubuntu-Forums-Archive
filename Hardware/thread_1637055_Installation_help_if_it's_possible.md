---
title: "Installation help if it's possible"
date: 2010-12-03
forum: Hardware
---

### Post by JBoynton on 2010-12-03
I have a toshiba c655d s5048 and i was wondering if it was even possible to install ubuntu on it and it to actually work, 10.10 installs with acpi workaround but won't boot afterwards, any solutions?

---

### Post by oldfred on 2010-12-03
Welcome to the forums.

How far does it boot. Do you get a grub menu and after making a choice it stops or do you not get a  grub menu? Are you dual booting? If only Ubuntu you will not normally get a menu unless you hold shift key from BIOS until menu appears.

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by JBoynton on 2010-12-04
ok after a fresh installation of dual boot it gives me the options: "Ubuntu, Linux 2.6.35-22-generic
Ubuntu, Linux 2.6.35-22-generic (recovery mode)
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)
Windows Vista (loader) (on /dev/sda3)" (this is inside of a box)
Above the box: "GNU GRUB  version 1.98=20100804-5ubuntu2"
Under the box: "Use the(up) and (down) keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' for a command-line. ESC to return to previous menu."
it's Ubuntu 10.10 64-Bit

---

### Post by oldfred on 2010-12-04
Usually one windows is the recovery and the other is the main install. Often the recovery is the one listed as Vista. Not sure why 3 windows unless you have another install.

If you boot Ubuntu (first) does it hang. And can you boot the recovery mode that should take you to a command line?

Often if you are this far grub is ok and it is configuration parameters for Ubuntu, most often lately relating to video.

For my nvidia I had to do this:
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

If able to boot to recovery mode & netroot
list of recommended drivers
jockey-text -l
Install a driver
sudo jockey-text -e <driver>

---

### Post by JBoynton on 2010-12-05
no that didn't wor I'll take a picture and post what it does to see if you can help out at all

---

