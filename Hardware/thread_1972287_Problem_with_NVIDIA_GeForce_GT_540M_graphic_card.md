---
title: "Problem with NVIDIA GeForce GT 540M graphic card"
date: 2012-05-03
forum: Hardware
---

### Post by blobx on 2012-05-03
Hi!
I have a problem with my NVIDIA GeForce GT 540M graphic card: it isn't recognized in my Ubuntu 12.04.
I tried to install the drivers for it but when I lunch the installer it says:
```
WARNING: You do not appear to have an NVIDIA GPU supported by the 295.49     
           NVIDIA Linux graphics driver installed in this system.  For further 
           details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in 
           the README available on the Linux driver download page at           
           www.nvidia.com.
```
Then
```
ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.
```
And then
```
ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at www.nvidia.com.
```
Actually I'm using the GPU that's included in my CPU, but I'd like to use also my Nvidia card.
Thanks :)
PS.: sorry for my bad English, I'm Italian :/
EDIT: I forgot: I have a [Samsung RC530 S03 Laptop](http://www.samsung.com/it/consumer/pc-peripherals-printer/notebook/high-performance/NP-RC530-S03IT-spec)

---

### Post by mips on 2012-05-03
In a terminal do,
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

From the desktop,
**ctrl-alt-f1** which will drop you into the cli where we now need to stop xorg/lightdm

```
sudo /etc/init.d/lightdm stop
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
sudo reboot

```

If you want to use both gpus and be able to switch between them then I think you need the open source nouveau drivers but I could be wrong.

Read this and some of the links supplied 
[http://askubuntu.com/questions/59037/how-to-get-nvidia-driver-working-properly-running-experimental-3d-support](http://askubuntu.com/questions/59037/how-to-get-nvidia-driver-working-properly-running-experimental-3d-support)
[http://ubuntuforums.org/showthread.php?t=1913114](http://ubuntuforums.org/showthread.php?t=1913114)
[http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04](http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04)
[http://ubuntuforums.org/showthread.php?t=1871226](http://ubuntuforums.org/showthread.php?t=1871226)

---

### Post by blobx on 2012-05-03
When I run
```
sudo apt-get install nvidia-current nvidia-settings
```
it says that nvidia-current and nvidia-settings are already at the latest version.
I'll take a look at the links you posted. Thanks :)

---

