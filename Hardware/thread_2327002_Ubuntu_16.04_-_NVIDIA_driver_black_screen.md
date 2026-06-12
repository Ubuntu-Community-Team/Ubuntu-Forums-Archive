---
title: "Ubuntu 16.04 - NVIDIA driver black screen"
date: 2016-06-06
forum: Hardware
---

### Post by dr-cono on 2016-06-06
Hi, im trying to use my GK208M [GeForce 920M] in a fresh install of ubuntu gnome 16.04. I first tried with Additional drivers, after installing and rebooting, black screen. Had to chroot from a live usb to purge nvidia drivers following this: [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

Then i googled my error and found this: 
[http://askubuntu.com/questions/760374/ubuntu-16-04-nvidia-driver-blank-screen](http://askubuntu.com/questions/760374/ubuntu-16-04-nvidia-driver-blank-screen)

tried the nomodeset fix and didn't work.
After that, chroot again and purge the driver,  i tried this.
[http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics](http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics)
Installed nvidia-364 and same problem.

Then i tried to download from nvidia's webpage. I downloaded the .sh and it said i already had nvidia running:

> An NVIDIA kernel module 'nvidia' appears to already be loaded in your  
         kernel.  This may be because it is in use (for example, by an X        
         server, a CUDA program, or the NVIDIA Persistence Daemon), but this    
         may also happen if your kernel was configured without support for      
         module unloading.  Please be sure to exit any programs that may be     
         using the GPU(s) before attempting to upgrade your driver.  If no      
         GPU-based programs are running, you know that your kernel supports     
         module unloading, and you still receive this message, then an error    
         may have occured that has corrupted an NVIDIA kernel module's usage    
         count, for which the simplest remedy is to reboot your computer. 


with lsmod i found that a module called nvidia is running

> 
&#10140; lsmod | grep nvidia
nvidia              10080256  2
drm                   360448  8 ttm,i915,drm_kms_helper,nvidia,nouveau



but rmmod nvidia outputs

> 
&#10140;  ~ rmmod nvidia
rmmod: ERROR: Module nvidia is in use


but the only thing i find with nvidia is nvidia-detector and it outputs 'none'


Does anyone know the fix for this? Thanks a lot

---

