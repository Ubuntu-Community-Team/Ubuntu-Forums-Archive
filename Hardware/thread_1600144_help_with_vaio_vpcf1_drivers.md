---
title: "help with vaio vpcf1 drivers"
date: 2010-10-18
forum: Hardware
---

### Post by magnetpest2k7 on 2010-10-18
Hello all,

I am a long term ubuntu user. I just go a vaio Vpcf1 series laptop but i found there are no drivers for this laptop. Ubuntu 10.10 has some problems with caliberating the signal strength of certain wifi signals hence I wanted to install 10.04. It does get installed but there are no video drivers, the touch pad doesn't work and there is no sound too. 

How ever in 10.10 it was able to detect the sound. The gpu is Geforce 425m.


Any help is appreciated I mostly work on linux and its hard that there are always driver issues with any new model of systems.

---

### Post by spicywafflefries on 2010-10-26
I have the same system with exactly same problems, please let me know how and if you manage to resolve them.

---

### Post by revidnus on 2010-10-29
I have same graphics card on my Vaio I just bought and same problem. I think Nvidia has a driver you can download and try out but its still in beta. 10.04 works but no sound and no touchpad...10.10 doesn't load at all. I just get a purple screen.
Going to wait a while myself.
:(

---

### Post by sirrommit on 2010-12-03
I have had the same problem and have a partial solution.

If you boot into the recovery mode, it will boot to just a terminal. Then you can go to /etc/X11 and edit xorg.conf

Under Section "Device" Change Driver from "nvidia" to "nv".

For me this got most things working.  My only issue is that I can not use compiz.

As an interesting side note, I installed 10.10 about 2 weeks before it became final and it installed the nvidia driver and it worked perfectly.  Then about a week later, I updated my system and it no longer worked.

The only other problems I still have are:
- I haven't gotten the mic working
- wifi doesn't work at my office (a mode), at home (g mode) it does.

---

### Post by phrqas on 2010-12-25
Well, the Nvidia driver that ships with Ubuntu 10.10 only gave me an ever lasting purple screen, so I decided to try the manufacturer driver directly and it worked perfectly! It was actually pretty simple: go to [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and select your graphics card model. I have a Sony Vaio VPCF1, so I chose

Product Type: GeForce
Product Series: GeForce 400M Series
Product: GeForce GT 425M
Operating System: Linux 32 bits
Language: English (US)

Download and save the 260.19.29 driver installation script anywhere you find convenient. Then, make it executable

sudo chmod ugo+x <script path> 

Reboot the computer, choose Ubuntu Safe Mode and boot into root shell. Then, change the runlevel 

telinit 3

Run the installation script and follow the instructions on screen. That`s all you need.

---

### Post by revidnus on 2010-12-25
The nest time you upgrade ubuntu you may have to manualy install the driver again. Glad its working for you. How about the touchpad does it work after installing the driver, mine doesn't.

---

### Post by lengau on 2010-12-28
I'm busy documenting the problems with this particular model of laptop [on the Wiki]("https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Maverick"). I have a workaround to the touchpad problem as documented on Launchpad [(1)]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/641324") [(2)]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/681748"), [elsewhere on this forum]("http://ubuntuforums.org/archive/index.php/t-1526740.html") and [on a Google Code project]("http://code.google.com/p/vaio-f11-linux/issues/detail?id=1") created to deal with problems with the F series notebooks.

[My documentation]("https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Maverick") also contains a fix for the video problem, as I read [here.]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup") This will not let you control the LCD backlight. However, that may be achieved using [these instructions.]("http://code.google.com/p/vaio-f11-linux/wiki/DisplayBacklight")

As far as sirrommit's wifi problem is concerned: according to [Atheros's documentation,]("http://www.atheros.com/technology/technology.php?nav1=47&product=80") this wifi chip does not support 5 GHz mode (802.11a). I would suggest buying another card such as [this one]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5073816&CatId=2704") (based on a [RaLink RT2870 (PDF WARNING)]("http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1EQTVMekEzTHpJNEwzQnliMlIxWTNRMk56TTFOekE1TVRRekxuQmtaajA5UFZKVU1qZ3dNRjl3TWw5dVpYYz1D") according to [this]("http://www.wireless-driver.com/engenius-eub-9801-wireless-driver-utility/"), which is compatible with Linux).

I have had no problems with the wifi on this laptop so far - it worked out of the box without any proprietary drivers.

---

### Post by revidnus on 2010-12-29
Just a note Ubuntu 10.10 runs really well on my sony vpcf1 with oricale virtual box for those who need a quick fix. I have windows 7 64bit with Oricle VM software installed ...sound and video is great with this laptop. So until drivers are available its a quick fix for me.
:guitar:

---

### Post by lengau on 2010-12-29
Unfortunately, that's not an option for me. With what I do, I actually need direct access to the hardware.

---

### Post by vdberghm on 2011-01-07
I have a Vaio VPCF1 as well. I am a simple biologist and a long time Windows user. At last new years dinner I had an interesting conversation with someone who explained me the benefits of Linux and that it is as easy and intuitive to use as MS Windows. 
So I downloaded Ubuntu and gave it a try. Nothing works! The touchpad doesn't move the cursor, the wifi is not working, the screen resolution is 800x600 max etc. After hours of trying I finally manage to update the Nvdia drivers and then nothing worked anymore. Just a purple screen.
I went back to Windows and landed on this page: The solution proposed here is to configure xorg.conf, adding i8042.nopnp to GRUB_CMDLINE_LINUX somewhere and a lot of other things only people with a brain 10 times my size can understand. 
And IF all this makes Ubuntu work, then I risk to have to do new tricks the next time I upgrade the OS. 
I understand that Ubuntu doesn't have the same manpower as MS, but if after more than 6 months it still full of bugs and still doesn't work, then i can't use it and I will need stick to MS Windows.

---

### Post by lengau on 2011-01-07
> **vdberghm said:**
> So I downloaded Ubuntu and gave it a try. Nothing works! The touchpad doesn't move the cursor, the wifi is not working, the screen resolution is 800x600 max etc.

A nasty little secret Microsoft don't want you to know is that a clean install of Windows would probably be as working as your Ubuntu install (it's only thanks to the drivers Sony installed before you got your laptop that you have a properly functioning system on arrival).

I have written [some documentation]("https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Maverick") regarding the installation of the latest version of Ubuntu on the F series that may help you out (including the known problem with the Nvidia driver). You're also welcome to ask more questions here or on [IRC]("http://www.ubuntu.com/support/community/chat"). If the documentation I have written is unclear, please tell me so I can improve it.

Alternatively, you could wait until the release of Ubuntu 11.04 in April. I'm using a development version (REALLY not recommended, but I'm doing so anyway) and it seems to have taken care of the major issues (the only problem I have left is that the internal microphone is not working, but plugging in a microphone works like a charm and that's what I tend to do anyway).

If you would like help in person, you may want to look to see if there's an [Ubuntu Local Community]("http://loco.ubuntu.com/teams/") in your area and perhaps ask them for help. Often, one of them will be willing to meet you in a coffee shop (or similar location) one weekend to help you hammer out any issues.

---

### Post by magnetpest2k7 on 2011-03-10
> **lengau said:**
> A nasty little secret Microsoft don't want you to know is that a clean install of Windows would probably be as working as your Ubuntu install (it's only thanks to the drivers Sony installed before you got your laptop that you have a properly functioning system on arrival).

I have written [some documentation]("https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Maverick") regarding the installation of the latest version of Ubuntu on the F series that may help you out (including the known problem with the Nvidia driver). You're also welcome to ask more questions here or on [IRC]("http://www.ubuntu.com/support/community/chat"). If the documentation I have written is unclear, please tell me so I can improve it.

Alternatively, you could wait until the release of Ubuntu 11.04 in April. I'm using a development version (REALLY not recommended, but I'm doing so anyway) and it seems to have taken care of the major issues (the only problem I have left is that the internal microphone is not working, but plugging in a microphone works like a charm and that's what I tend to do anyway).

If you would like help in person, you may want to look to see if there's an [Ubuntu Local Community]("http://loco.ubuntu.com/teams/") in your area and perhaps ask them for help. Often, one of them will be willing to meet you in a coffee shop (or similar location) one weekend to help you hammer out any issues.

Thanks for you documentation butI am having vpcf1 with nvidia   geforce 425m and the 260.19.29 does not work. Also any other latest versions from ubuntu repository does not seem to work. The only working driver for this model in 64 bit ubuntu is x86_64-256.53 nvidia driver. I am using this but there are visible lags in graphics specially when using compiz effects. If you have other solutions to this problem kindly post them.

---

### Post by lengau on 2011-03-10
If you followed the instructions linked recently, it should have installed the driver with version number 270.29-0ubuntu1~maverick~xup2 (you can see this using the command "aptitude show nvidia-current"). This appears to work with my VPCF1 which also has a 425M. I have a VPCF1390X (you can find this using the command "sudo lshw|grep 'product: VPCF1'").

Can you give me some more information about your laptop? The problem may still be fixable.

---

### Post by magnetpest2k7 on 2011-03-11
> **lengau said:**
> If you followed the instructions linked recently, it should have installed the driver with version number 270.29-0ubuntu1~maverick~xup2 (you can see this using the command "aptitude show nvidia-current"). This appears to work with my VPCF1 which also has a 425M. I have a VPCF1390X (you can find this using the command "sudo lshw|grep 'product: VPCF1'").

Can you give me some more information about your laptop? The problem may still be fixable.

Thanks,

Even my product is VPCF1390X 

I can see that even my driver is 270.29-0ubuntu1~maverick~xup2 after the current nvidia update in my new 2.65.27 kernel. But I am pretty sure that it did not work after I updated. I had to run my old 256.53 driver to enable the gui. In fact I tested the new driver in my old 2.65.35.25 kernel and it was not going inside the gui after the update. 

Additionally when I open the nvidia xserver setting from system menu the driver displayed is 256.53. Can you tell me what to do? I think  both the driver instances are installed but guess 256.53 is running I am not sure.

---

### Post by lengau on 2011-03-11
What's the output of "dpkg --get-selections|grep nvidia"?

---

### Post by magnetpest2k7 on 2011-03-11
> **lengau said:**
> What's the output of "dpkg --get-selections|grep nvidia"?

I get the following

nvidia-173-modaliases				install
nvidia-96-modaliases				install
nvidia-common					install
nvidia-current					install
nvidia-current-modaliases			install
nvidia-settings					install

---

### Post by lengau on 2011-03-11
I take it you installed the Nvidia drivers from their site, then, rather than the packaged version.

According to [NVnews]("http://www.nvnews.net/vbulletin/showthread.php?t=83294") you should be able to run "sudo nvidia-installer --uninstall" to remove that version of the driver.

I would suggest running the following (to make sure you don't mess up a different driver):

```
sudo apt-get remove nvidia-current nvidia-settings
sudo nvidia-installer --uninstall
sudo apt-get install nvidia-current nvidia-settings
```

Following this, you will need to reboot your computer.

---

### Post by Allen441 on 2011-03-16
Try checking out the info on this webpage.
[https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Maverick](https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Maverick)

They've managed to get most of the drivers working on the 1390x, even the internal microphone and graphics card. With the exception of the trackpad recognized as a wheel mouse, everything runs smoothly.

Edit: And yes, despite the page saying this was based on an install of Kubuntu, standard Ubuntu works as well with these steps.

---

### Post by lengau on 2011-03-17
> **Allen441 said:**
> Edit: And yes, despite the page saying this was based on an install of Kubuntu, standard Ubuntu works as well with these steps.

I'm glad to hear so. Whilst I used Kubuntu to make that page, I really tried to make all of the steps desktop-agnostic so people could use it with any Ubuntu variant.

Most of these bugs are fixed out of the box in 11.04, so when it comes out we should have even fewer problems. [This page]("https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Natty") has info about 11.04 (although the last edit seems to be my additions on 15 January, so the page is 2 months out of date). I'm hoping to have the time to install 11.04 Alpha 3 on my laptop this weekend in order to keep the documentation up-to-date on the aforementioned page.

---

### Post by revidnus on 2011-05-14
Sony vpcf133fx with 1G 425 graphics card i7-740qm processor.... Well I waited to upgrade from 10.04 to 11.04 on this laptop. It paid off. I was only getting 800x600 resolution in 10.04. I was unable to install the nvidia driver it recommended under hardware ...just a purple blank screen. HOWEVER the new upgrade to 11.04 did the trick!

Well Ok not completely at first. I just let it upgrade online. It did not install compiz or unity at first.I figured because I didn't have the additional driver installed before upgrading. It just defaulted to gnome or the classic desktop. It said I didn't have the hardware for the unity desktop.So after the upgrade I installed the additional recommended driver and activated it. Reboot and all is well Unity desktoop loaded ok and everything seemed to be working. So to install compiz I just opened up synaptic package manager and installed compiz... piece of cake!

:popcorn:

---

