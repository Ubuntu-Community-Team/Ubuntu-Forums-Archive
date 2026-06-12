---
title: "Changing the Graphics Card in Ubuntu"
date: 2017-05-19
forum: Hardware
---

### Post by jhollin on 2017-05-19
Hello,

I have been attempting to make ubuntu use a dedicated Nvidia graphics card rather than an integrated intel graphics card. The first problem I encounter is that, when running nvidia-settings, there is no PRIME profile. I get an error in the command prompt reading: 

```
** Message: PRIME: No offloading required. Abort** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file should have been installed along with this driver at /usr/share/nvidia/nvidia-application-profiles-key-documentation. The application
       profiles will continue to work, but values cannot be prepopulated or validated, and will not be listed in the help text. Please see the README for possible values and descriptions.

```

[B]My Computer:

[/B][http://imgur.com/rjGAV9Z](http://imgur.com/rjGAV9Z)

Input: ```
sudo lshw -C display
```

Output:   ```
*-display                      description: 3D controller
       product: GM107M [GeForce GTX 960M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:324 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:320 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64)

```

Input:  ```
sudo dpkg -l | grep nvidia
```

Output: ```
ii  nvidia-375                                 375.39-0ubuntu0.16.04.1                       amd64        NVIDIA binary driver - version 375.39
ii  nvidia-opencl-icd-375                      375.39-0ubuntu0.16.04.1                       amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                               0.8.2                                         amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                            361.42-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver



```

[http://imgur.com/DA4Tn1v](http://imgur.com/DA4Tn1v)

[B]
My Problem:


[/B]When I run ```
nvidia-settings
``` to change the driver that is used by Ubuntu, I get the message
```
** Message: PRIME: No offloading required. Abort** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file should have been installed along with this driver at /usr/share/nvidia/nvidia-application-profiles-key-documentation. The application
       profiles will continue to work, but values cannot be prepopulated or validated, and will not be listed in the help text. Please see the README for possible values and descriptions.
```
[B]
My Attempted Solutions:

[/B]First, I ran ```
sudo apt-get purge nvidia-*
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-375
sudo reboot
```
Upon rebooting to see if this had helped my issue, my computer would hang on startup at
```
/etc/sda6: recovering journal
/etc/sda6: clean, xxx/xxxx file, xxx/xxxx blocks
```
From this point, I could only boot in recovery mode. I tried booting with the nomodeset parameter, upon which my computer reached the familiar login screen, made a god awful white noise sound, and would keep returning me to the login screen after every login attempt despite successfully entering my password. From googling this issue, I found that the commonly suggested solution was to run sudo apt-get purge nvidia-*, which is unfortunately a step backwards, leading me to believe I've come to a dead end. 

I also tried installing bumblebee as an alternative, but I ran into issues there, too. If this is a worthwhile direction to pursue I can post more about the trouble I had there.

I have not tried to manually install the .run files provided by Nvidia, as this seems to be ill-advised in every instance. 

Any help would be appreciated!

---

### Post by Autodave on 2017-05-19
The best way that I have found to install Nvidia drivers is to go to *Settings -> Software & Updates -> Additional Drivers *and choose the recommended one. Remember to purge the old driver first.

---

### Post by efflandt on 2017-05-19
Where are you running nvidia-settings from? Although, nomodeset is usually used for desktop Nvidia graphics, I read somewhere NOT to use that for a hybrid graphics laptop, so I did not and my gaming laptop worked fine with nvidia drivers, at least until the laptop failed and no longer even turns on. You launch "NVIDIA X Server Settings" in X to switch from Intel to Nvidia (in which case you might need to reboot) or Nvidia to Intel (in which case you just need to log out of X and back in).

---

### Post by jhollin on 2017-05-20
Thank you for your responses!

Autodave -
I should have mentioned in my original post, I have tried downloading the drivers with sudo apt-get install nvidia-375 as well as through the "Software & Updates" tab, however the results were the same, and I still ran into the problem described above.

efflandt- 
I have attempted to launch NVIDIA X Server Settings, however, I ran into the error above, stating that 

```
[COLOR=#000000][FONT=&amp]** Message: PRIME: No offloading required. Abort** Message: PRIME: is it supported? no[/FONT][/COLOR]

ERROR: nvidia-settings could not find the registry key file. This file should have been installed along with this driver at /usr/share/nvidia/nvidia-application-profiles-key-documentation. 
The application [COLOR=#000000][FONT=&amp]profiles will continue to work, but values cannot be prepopulated or validated, and will not be listed in the help text. Please see the README for possible values and descriptions.[/FONT][/COLOR]
```. 

Thank your again for the help!

---

