---
title: "Kinect not working Ubuntu studio 14.04 64 bits"
date: 2014-08-10
forum: Hardware
---

### Post by mennowo on 2014-08-10
Hi All,  Recently I installed a fresh Ubuntu Studio on my Asus K53SV laptop, 64 bits. 
It has 3 USB 2.0 ports. 

Before, while using I believe it was13.10, the XBOX kinect worked fine. 
Now, after connecting it, the led blinks green a few times, then goes of. 
All freenect test apps report: No Devices found.  

I pulled libfreenect from git, built it. If I start freenect-glview right after plugging in the Kinect, I get this:  ```
K53SV:/etc$ freenect-glview  
Kinect camera test  
Number of devices found: 1 send_cmd: 
Output control transfer failed (-1) 
freenect_fetch_reg_pad_info: send_cmd read -1 bytes (expected 8)  
freenect_camera_init(): Failed to fetch registration pad info for device  
Could not open device 
Device 0xbe4030 open during shutdown, closing..
```  
I searched extensively, found that usb autosuspend might be the problem, installed powernap and ran this command  ```
K53SV:/etc$ sudo powernap-action --disable usb_autosuspend
```  but it has no effect.  

If I run lsusb right after I plug in the Kinect, there is a brief moment when camera, audio and motor show up all three; thereafter audio and camera disappear (disconnect) and only the motor remains in the list.  I have no idea what to do now, and really need this to work. 

It worked like a charm before... Also, it works like a charm on my desktop running the same Ubuntu distro and version. So I guess it really has to do with the laptop, but how to fix this? 

 Any help very welcome!  Bye, Menno

---

### Post by Mayumi_Mohan on 2015-04-02
I am having the same issue. Did you find a solution to this?

---

### Post by Carlos_A_Lugo on 2015-04-16
Hello!

I had the same problem, exactly the same problem. And yes it was autosuspend

My  machine is a laptop Asus x550c running 14.04 lts

My fix was this: ( [http://unix.stackexchange.com/questions/91027/how-to-disable-usb-autosuspend-on-kernel-3-7-10-or-above](http://unix.stackexchange.com/questions/91027/how-to-disable-usb-autosuspend-on-kernel-3-7-10-or-above) )



Edit the /etc/default/grub file and change the GRUB_CMDLINE_LINUX_DEFAULT line to add the usbcore.autosuspend=-1 option:
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
  Note that quit splash were already present options. So keep other options you have too.
  After save the file, update grub:
  sudo update-grub
  And reboot.
  Now check autosuspend value:
  cat /sys/module/usbcore/parameters/autosuspend
  And it should display -1.


If you do that and connect you kinect after reboot it will stay alive and if you have a good installation of openkinect's libfreenect or openNI you can test it immediatly

Regards.

---

