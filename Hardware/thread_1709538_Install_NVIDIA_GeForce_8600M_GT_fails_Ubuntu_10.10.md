---
title: "Install NVIDIA GeForce 8600M GT fails? Ubuntu 10.10"
date: 2011-03-18
forum: Hardware
---

### Post by janoschhcsonaj on 2011-03-18
Dear Linux/Ubuntu community.

I really think Linux is a great thing! However I did not use it since I thought to learn all about Ubuntu will take too much time I do not have...

However my brother told me this is not the case.

Now I am working since three days to get my graphic card running (reading and following all kind of advices to be found through Google). It is a NVIDIA GeForce 8600M GT.

I already tried about three ways to install the graphic card and reinstalled Ubuntu 10.10 a couple of times. I tried:

1. System -> Administration ->  Additional drivers.

2. [http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat](http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat)

3. [http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux](http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux)

And some other things...

I will give it one more try now. Thus I will reinstall Ubuntu 10.10 and wait what kind of recommendations I will get here (so it will be evident what I did and did not do...).

What happened most time when I tried 1., 2. or 3. is: The driver has been installed (and I think was working) but the Laptop restarted only to the Terminal. When I entered "sudo service gdm start" the desktop loaded (and I think the driver worked).

I hope I can find a solution otherwise I will be stuck with Windows.

Thanks a lot for any help.
Janosch

---

### Post by janoschhcsonaj on 2011-03-18
Ubuntu is reinstalled now. I am ready to take action! Any recommendations how to start?

Help is really required and appreciated!

Thanks. Janosch

---

### Post by janoschhcsonaj on 2011-03-19
Dolphin2011 has a similar problem: [http://ubuntuforums.org/showthread.php?t=1664960](http://ubuntuforums.org/showthread.php?t=1664960)

However I tried some recommendations before (as far as I understand it). Nothing helped.

Anyway. I am hesitating to start since I do not know the most promising way to do so. And: Should I install the Ubuntu security / recommendet updates (update manager) first and later install the driver? Or is it for some reason important to proceed the other way around? Which driver should I install according to 1., 2. or 3. above. Please. I need help.
Janosch

---

### Post by janoschhcsonaj on 2011-03-20
Am I in the wrong forum here???

Anyway. I proceeded since maybe some of you require more specific errors.

For some reason I followed this installation procedure:

[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

Know I get the usual errors:

The computer starts as usual but does not load the desktop but the terminal/console(/what you would call DOS from Microsoft).

When I do not do anything the error "[ 139.500127] tpm_tis 00.0a: tmp_transmit: tpmsend: error -62" apears after about two minutes and about one minute later the desktop is loaded.

When I log in and type "sudo service gdm start" the desctop is loaded. 

Clicking on System -> Administration -> Additional drivers the recommended accelerated graphics driver is installed (current version). 

I can choose the NVIDIA X server settings and the graphic card seems to be installed.

When I enter "lspci | grep VGA" into the terminal the output is:
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)

When I reboot my computer I get strange errors I tried to take a photo of (see attachments?).

Any idea. Please be so kind and help.
Janosch

---

### Post by matek09 on 2011-04-02
1. Boot into recovery mode and choose root console.
2. Edit /etc/X11/xorg.conf (you can use vim). Change Driver from "nvidia" to "nv" in section "Device".
3. Now you should be able to boot into normal mode.
4. Follow this instructions [http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html](http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html).
Hope this helps.

---

### Post by beew on 2011-04-02
What are your computer's specs? Is it  a laptop?

---

### Post by janoschhcsonaj on 2011-04-04
Yes it is a laptop:

Zepto Znote 6625WD
 :: Prozessor: Intel Core 2 Duo T7300 2 GHz  
 :: Mainboard: Intel PM965
 :: Speicher: 2048 MB, DDR2 PC6400 800Mhz, 2x 1024MB, 4096MB
 :: Grafikkarte: NVIDIA GeForce 8600M GT - 512 MB, Kerntakt: 475 MHz, Speichertakt: 400 MHz
 :: Bildschirm: 15.4 Zoll 16:10, 1680x1050 Pixel, UltraCrisp, spiegelnd: ja
 :: Festplatte: 200 GB - 7200 rpm, 200GB 7200U/Min Hitachi HTS722020K9SA00
 :: Soundkarte: Realtek ALC268 HD Audio
 :: Anschlüsse: 1 Express Card 54mm, 4 USB 2.0, 1 Firewire, 1 VGA, 1 S-Video, RJ-11 Modem, 1 Infrared, 1 Kensington Lock, 1 Docking Station Anschluss, Audio Anschlüsse: Microphone, Headphones (kombiniert mit optischem Ausgang), Card Reader: 3in1,  
 :: Netzwerkverbindungen: 10/100/1000 LAN Card (10/100/1000MBit), Intel Wireless WiFi Link 4965AGN (abgn), VV2.0+EDR Bluetooth
 :: Optisches Laufwerk: DVD +/- RW Double Layer
 

 (sorry - some things in german but I think you can understand)

I will turn to matek09's recommendations as soon as I have time.

Thanks
Janosch

---

### Post by janoschhcsonaj on 2011-04-12
If I follow the installation procedure of matek09 it does not work neither (thanks anyway).

I actually reinstalled Ubuntu again. I am not sure  whether step 1 to 3 is required therefore.

1. Boot into recovery mode and choose root console.
2. Edit /etc/X11/xorg.conf (you can use vim). Change Driver from "nvidia" to "nv" in section "Device".
3. Now you should be able to boot into normal mode.

However I have difficulties to use vim anyway. I can start it but did not understand how to save the changes...

Is that important?

4. Follow this instructions [http://www.socialblogr.com/2010/10/h...ntu-10-10.html]("http://www.socialblogr.com/2010/10/how-to-install-nvidia-graphic-card-driver-on-ubuntu-10-10.html").
Which are:
1. Go to [NVIDIA website]("http://www.nvidia.com/") and download the compatible driver for your graphic card series.
2. Reboot your Ubuntu.
3. Choose the ‘Recovery Mode’ on GRUB.
4. Go to the bottom of menu list, choose ‘root console’.
5. Disable the Kernel Nouveau.
 #echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
#update-initramfs -u Reboot.
 6. Change to init 3
 #init 3
7. Install the NVIDIA driver
 #sh NVIDIA-XXXXXX.run

I get the message that I need to be in root modus or something.

If I install the driver from root modus I get:

The distribution-provided preinstall script failed. -> Continue

Would you like to run the nvidia-xconfig utility to automatically update your X configuration file so that Nvidia X driver will be used when you restart X? -> yes 
8. Reboot your Ubuntu.



Now the Desctop does not load under any circumstances. Hence I disabled the driver again and installed the recommended Driver via System -> Administration ->  Additional drivers and installed all recommended updates.

Now I have the same problem as before. mI think my driver works but the desctop is not loaded after boot. Entering sudo service gdm start the desctop loades.

Help please!

Thanks for any approach.

Janosch

---

