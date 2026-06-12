---
title: "Updating Nvidia drivers out of X"
date: 2008-08-03
forum: Hardware
---

### Post by Algo2 on 2008-08-03
I just got a new laptop, a Compaq CQ50-115NR (laugh, but it was cheap).  Anyways...

It has an nvidia chip inside so I can't go beyond 800x600 without updating the drivers.  It's an AMD Turion x2 64 bit processor so I went to nvidia, go the drivers.  Open terminal, use root access, it says I have to be outside of X.

I have no idea how to do that exactly with the new Ubuntu 8.04 so I restart and log in as Ubuntu (recovery mode) and choose root shell.  I run the drivers again and this time it says they are outdated and it tries to download from nvidia.com.  Problem is my internet isn't working in the root shell there so it can't.

Any advice?

---

### Post by phidia on 2008-08-03
There are easier ways to install the nvidia driver with ubuntu.
Does System > Administration > Hardware Drivers show a driver for your card?

[This page]("http://seogadget.co.uk/how-to-install-a-nvidia-display-driver-in-ubuntu/") gives a nice visual guide to that.

---

### Post by Algo2 on 2008-08-04
> **phidia said:**
> There are easier ways to install the nvidia driver with ubuntu.
Does System > Administration > Hardware Drivers show a driver for your card?

[This page]("http://seogadget.co.uk/how-to-install-a-nvidia-display-driver-in-ubuntu/") gives a nice visual guide to that.

No it doesn't

---

### Post by tuxxy on 2008-08-04
You could try and install them through Envy, search for it in synpatic to install

---

### Post by JeSTeR7 on 2008-08-04
Hey, I was thinking about picking this laptop up.  Can you update if you happen to get the drivers working, also, does the wireless work well?  What chipset does it use?

---

### Post by Algo2 on 2008-08-04
> **JeSTeR7 said:**
> Hey, I was thinking about picking this laptop up.  Can you update if you happen to get the drivers working, also, does the wireless work well?  What chipset does it use?

I have not been able to update the nvidia drivers yet and it's stuck at a maximum resolution of 800 x 600.  I don't even want to log into Ubuntu unless it's to try a new way of updating it.

It uses broadcom wireless.  AMD Turion X2 64bit processor.

The first NDISWrapper I tried didn't work but I really didn't care about trying more until I get the graphics fixed.  Looks like i'm stuck with Vista until then.

---

### Post by phidia on 2008-08-04
You can use a wired ethernet connection until then-but that is sort of a pain. Which broadcom card do you have?
You can try [this howto]("http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+howto") or use the Ubuntu wiki [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") to enable your card.

For a comprehensive nvidia install guide click [here]("http://ubuntuguide.org/wiki/Ubuntu:Hardy").

---

### Post by Acurus on 2008-08-07
Hi, I have the same computer and got the videocard to work using Envy. It doesnt automagic detect it, but manualy installing it using the driver named 17* something worked flawlessly.

That was the easy part.. But I got problems getting the wifi to work. Managed to get i working once using MadWifi but since I messed things up trying to get the sound working I cant replicate the sucess hehe.

My sound is crackling and not useable.

Hating it here in Vista at the moment. so if you or anyone else have come across somthing working for WiFi and sound I would appritiate a hint :)

---

### Post by dabl on 2008-08-07
All about madwifi on Ubuntu:

[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

:)

---

### Post by SandyM on 2008-08-07
> **Algo2 said:**
> I just got a new laptop, a Compaq CQ50-115NR (laugh, but it was cheap).  Anyways...

It has an nvidia chip inside so I can't go beyond 800x600 without updating the drivers.  It's an AMD Turion x2 64 bit processor so I went to nvidia, go the drivers.  Open terminal, use root access, it says I have to be outside of X.

I have no idea how to do that exactly with the new Ubuntu 8.04 so I restart and log in as Ubuntu (recovery mode) and choose root shell.  I run the drivers again and this time it says they are outdated and it tries to download from nvidia.com.  Problem is my internet isn't working in the root shell there so it can't.

Any advice?
HERE IS WHAT YOU NEED TO DO

1. install latest nvidia drivers on your Desktop. It will be a .run file
2. press alt + ctrl + F1 u will u will reach the shell.

Before 3rd point here are certain assumptions and things u need to do. First of all rename the drivers to NVIDIA as it will be quite pain to input its default file name. Secondly I am telling u to how to install a .run file through shell and I am naming this file as example.run , u will use NVIDIA or whatever name u have given to NVIDIA drivers instead of example.

3. following are the commands u need.
    a) sudo /etc/init.d/gdm stop
u will be asked for password. input ur password but u won't be able to see it  (not even dots or stars). This will stop ur X server. then next command is
    b) cd ~/Desktop
    c)sudo chmod +x example.run
    d)sudo ./example.run
After this u will reach to Nvidia window where u will be asked certain options to be checked as yes or no.
    e)Afte drivers are succesfully installed u have to use this command to restart ur X server.
      sudo /etc/init.d/gdm start

HERE U ARE AFTER SUCCESSFULLY INSTALLING MANUALLY DOWNLOADED NVIDIA DRIVERS.

THERE  IS A SECOND METHOD TOO. U CAN GO TO SYNAPTIC AND INSTALL ENVYNG-GTK.THIS IS A SOFTWARE WHICH CAN DIRECTLY DOWNLOAD AND INSTALL LATEST STABLE VERSION OF NVIDIA DRIVERS.
BUT I PREFER MANUAL INSTALL.MORESOEVER BECAUSE I AM USING LATES BETA VERSION OF NVIDIA DRIVERS WHICH IS AMAZING.

---

### Post by karthik2fun on 2008-08-29
[QUOTE=Algo2;5518937]I just got a new laptop, a Compaq CQ50-115NR (laugh, but it was cheap).  Anyways...

Hi,


I am also using the laptop which you have ( Compaq Presario CQ50-115NR). But i am not able to install ubuntu 8.0.4 (32 and aslo 64 bit)on that laptop.When i am trying to install the laptop hangs when ubuntu loading screen pop ups. How did you install ? Kindly give details to install ubuntu on that laptop. 

Regards,

Karthik.S

---

### Post by cordoba57 on 2008-09-01
OK, I've got two of these machines.  I took a bit of research but I've got both working pretty well.  (Although I have kept Vista as an alternative boot).

First, installation from Ubuntu 8.04 CD works well. No real issues -- except audio is pretty awful.  Someone has a post saying that OSS works better than ALSA.  I haven't tried that yet.

Video:  You'll want the new 173.14.xx driver.  For that, you can either use Envy or follow the manual instructions here -- [http://ubuntu-virginia.ubuntuforums.....php?p=5632582](http://ubuntu-virginia.ubuntuforums.....php?p=5632582).

If you do the manual route, you might want to follow the link at the end to automatically re-build video driver if the kernel gets updated.

WIFI I am using ndiswrapper with the windows driver.  I might experiment with madwifi later this week..but ndis is working (right now as a matter of fact).

BUT HERE IS A GOTCHA: The machine's wifi button has a red/blue light.  In Vista, the light is blue when the card is powered on and red when it is not.  In Linux, however, it is ALWAYS RED.  The button really does turn the card off and on!  So, when setting up your wireless, if you don't see the card, push the button.  (Hint: it will be nice when someone posts a correction for the light...)

Oh, another nuissance is the touchpad switch.  Presently, hitting it brings up Ubuntu help pages.  Can someone tell me how to make enable/disable the touchpad?

---

### Post by cordoba57 on 2008-09-01
Ok, I suppose it is gosch to respond to MY OWN post, but I've just noticed that Nvidia actually mentions the mobile version of the GForce 8xxx series has some functions with the keys like the wifi, etc.

So, has anyone tried this driver?  

 NVIDIA-Linux-x86-169.12-pkg1.run

Two options are offered on Nvidia.com

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)  allows me to select either GeForce or GeForce M/Go

Selecting GeForce 8 series takes me to 
[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

Selecting GeForce M series takes me to
[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

I understand that Nvidia produces the video card as well as mainboard for many laptops. This machine seems to be one.

---

