---
title: "Wireless internet DLink DWA-130 Rev C"
date: 2010-02-03
forum: Hardware
---

### Post by Darkcrosbone on 2010-02-03
I have just installed Ubuntu 9.10 and I want to get my Wireless USB Adapter to work, It is a DWA-130 Rev C from DLink, The one that has Linux drivers. I have tried on multiple occasions to install this device and have failed. I am a total newbie to Linux, and how to install any linux Drivers/programs other than using the Ubuntu Software Central. 

1. How do I install the DWA-130 Drivers. 
After downloading the drivers in the zip file, i extract them and here is what I get:
[http://s202.photobucket.com/albums/aa272/Album_Sora/?action=view&current=Screenshot-1.png](http://s202.photobucket.com/albums/aa272/Album_Sora/?action=view&current=Screenshot-1.png)
[http://s202.photobucket.com/albums/aa272/Album_Sora/?action=view&current=Screenshot.png](http://s202.photobucket.com/albums/aa272/Album_Sora/?action=view&current=Screenshot.png)
[http://s202.photobucket.com/albums/aa272/Album_Sora/?action=view&current=Screenshot-2.png](http://s202.photobucket.com/albums/aa272/Album_Sora/?action=view&current=Screenshot-2.png)

Here is what it says in the Readme on how to install:
=============================================================================== 
                Installation  
=============================================================================== 
<<Method 1>> 
Runing the scripts accomplish all operations including building up modules  
from the source code, installing driver to the kernel and starting up the nic. 
    1. Build up the drivers from the source code 
      make 
 
    2. Install the driver to the kernel 
          make install 
          reboot 
 
    3. bring up wlan if nic is not brought up by GUI, such as NetworkManager 
      ifconfig wlan0 up  
      Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name,  
                since it may change wlan0 to wlan1,etc. 
 
<<Method 2>> 
Or only load the driver module to kernel and start up nic. 
     1. Build up the drivers from the source code 
      make 
         2. Copy firmware to /lib/firmware/ or /lib/firmware/(KERNEL_VERSION)/ 
            cp -rf firmware/RTL8192U /lib/firmware 
          or 
            cp -rf firmware/RTL8192U /lib/firmware/(KERNEL_VERSION) 
          Note: This depends on whether (KERNEL_VERSION) subdirectory exists under /lib/firmware 
 
     3. Load driver module to kernel and start up nic. 
      ./wlan0up 
          Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out 
                after run ./wlan0up, please run ./wlan0down first, then it should  
                be ok.. 
      Note: If you see the message of "unkown symbol" during ./wlan0up, it 
        is suggested to build driver by <<Method 1>>. 





I have tried both methods unsuccessfully, an Error message here and permission denied there..... 

please provide specific instruction on how to install!  I'm a total newbie, so please go into detail on stuff that a newbie wouldn't know.

2. How do I make it so that I don't have to keep entering my password at system changes? its really annoying!



Thanks in Advance!

-Darkcrosbone

---

### Post by Darkcrosbone on 2010-02-03
OK i got the drivers working with the ndisgkt thing, now i can see the networks but I cannot connect I have tried WPA and WEP, neither are working for me.

---

