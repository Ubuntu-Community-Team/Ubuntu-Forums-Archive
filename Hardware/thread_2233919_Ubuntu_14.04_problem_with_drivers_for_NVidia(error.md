---
title: "Ubuntu 14.04 problem with drivers for NVidia(error during installation)"
date: 2014-07-11
forum: Hardware
---

### Post by superdude2 on 2014-07-11
Hello,
I installed nvidia drivers (version 337 open source) from Software Updater, because online videos(Youtube etc.) wasn't running well and i wanted to play some Steam game.After the reboot and I noticed that the same online videos still wasn't running well(nothing's changed). I opened NVidia X Server Settings to configure but there wasn't any option to change like OpenGL. So i suppose there isn't any installed drivers but i just did it .
My graphic card is NVidia 9500GT.

I'm looking forward to your reply.

edit:Sorry i guess it's wrong section.Please tell me how to delete this topic or please move it to the right section.

---

### Post by grahammechanical on 2014-07-11
Well, software and Updates>Additional Drivers tab is saying that you are running on Nvidia binary driver version 337.25 from Nvidia 337 (open source). Although I am a bit puzzled by it being described as "open source." This is why this driver is listed as an "alternative" and the utility says "no proprietary drivers are in use."

If this is some unofficial Nvidia driver, then I am not surprised that the Nvidia Xserver settings manager is not working well with it. I do note from the Nvidia download site that there is an official 337.25 driver and it is not listed as Beta either. 

Regards.

---

### Post by superdude2 on 2014-07-12
I've tried to install it but when I want to close/stop lightdm I get black screen. At the first time I could back to the text mode"ctrl+alt+F1/F7" and there was a text asking me if I do have permission to stop this service(with sudo on). Then I was getting black screen with no reaction and now I'm getting black screen for a moment and I'm back to my Desktop without any possibility to enter that text zone(ctrl+alt+F1) until reboot.

edit: I've finally managed to stop X by typing > sudo /etc/init.d/lightdm stop but i got an error from installation and i couldn't complete it. Log from this installation[HTML]nvidia-installer log file '/var/log/nvidia-installer.log'creation time: Sun Jul 13 09:01:31 2014installer version: 340.24
PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
nvidia-installer command line:    ./nvidia-installer
Using: nvidia-installer ncurses user interface-> License accepted.-> Installing NVIDIA driver version 340.24.-> Running distribution scripts   executing: '/usr/lib/nvidia/pre-install'...-> done.-> The distribution-provided pre-install script failed!  Are you sure you want to continue? (Answer: Continue installation)ERROR: The Nouveau kernel driver is currently in use by your system.  This driver is incompatible with the NVIDIA driver, and must be disabled before proceeding.  Please consult the NVIDIA driver README and your Linux distribution's documentation for details on how to correctly disable the Nouveau kernel driver.-> For some distributions, Nouveau can be disabled by adding a file in the modprobe configuration directory.  Would you like nvidia-installer to attempt to create this modprobe file for you? (Answer: Yes)-> One or more modprobe configuration files to disable Nouveau have been written.  For some distributions, this may be sufficient to disable Nouveau; other distributions may require modification of the initial ramdisk.  Please reboot your system and attempt NVIDIA driver installation again.  Note if you later wish to reenable Nouveau, you will need to delete these files: /etc/modprobe.d/nvidia-installer-disable-nouveau.confERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.[/HTML]

edit2: I've managed to install it.Finally. I had to purge uninstal previous drivers,reboot and then install it via text mode. Topic can be closed.

---

