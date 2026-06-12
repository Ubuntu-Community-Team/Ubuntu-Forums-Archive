---
title: "Proprietary drivers are not proposed since Ubuntu 14.04 64 bits installation"
date: 2014-10-06
forum: Hardware
---

### Post by ciryon03 on 2014-10-06
Hello people !

At the end of august I've decided to install the 64 bits version of Ubuntu 14.04, previously I was on the 32 bits version. I've made a clean install and after the install I saw that the nvidia proprietary driver were not proposed anymore unlike my previous run on the 32 bits, I've opened a [bug](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1363661) on launchpad :  but at this time, this is not yet solved so I use for now a [PPA](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa) which seems to have the latest version.

If anybody has the solution.

Thanks !

---

### Post by MartyBuntu on 2014-10-06
What NVIDIA card do you have?

---

### Post by ciryon03 on 2014-10-06
The Nvidia GT 740.

---

### Post by MartyBuntu on 2014-10-06
You've tried installing proprietary drivers from the Ubuntu Software Center?

---

### Post by ciryon03 on 2014-10-06
No. Since in the 32 bits I had them already on the sofwtare update manager, I assumed that in 64 bits it would be the same.

---

### Post by MartyBuntu on 2014-10-06
Normal Ubuntu releases do not have proprietary drivers already activated. You need to install them.

---

### Post by Vladlenin5000 on 2014-10-06
By "software update manager" you mean System settings > Software&Updates then the rightmost tab "Additional Drivers"? If so yes, it should appear there regardless of the CPU architecture.

---

### Post by ciryon03 on 2014-10-06
> **MartyBuntu said:**
> Normal Ubuntu releases do not have proprietary drivers already activated. You need to install them.Well the last times I have installed a normal Ubuntu release before the 14.04 64 bits (so if I remember well the 11.04, 11.09 en 12.04 in 32 bits), Ubuntu has always proposed me in "additional driver" tab of the update manager, the nvidia proprietary driver. Before having a GT740 I had a 8400 GS and it was recognized and the driver proposed. I had to activate it yes, but it was available. This is not the case with my 14.04 64 bits installation and I've done the installation twice.

---

### Post by ciryon03 on 2014-10-06
> **Vladlenin5000 said:**
> By "software update manager" you mean System settings > Software&Updates then the rightmost tab "Additional Drivers"? If so yes, it should appear there regardless of the CPU architecture.
Yes exactly whay I mean.

---

### Post by dave0109 on 2014-10-07
Looks like the GT740 wasn't supported until nvidia-337, and Ubuntu 14.04 only has nvidia-331.  Perhaps this is why it didn't offer any additional driver.

---

### Post by ciryon03 on 2014-10-07
> **dave0109 said:**
> Looks like the GT740 wasn't supported until nvidia-337, and Ubuntu 14.04 only has nvidia-331.  Perhaps this is why it didn't offer any additional driver.
Perhaps, where did you find this information ?

---

### Post by sns4rnr on 2014-10-07
Looks like I will be in the same boat.  I am currently awaiting a GT730 card for my 14.04 64-bit system (Still a few days away from receiving it).
If you work it out how, be sure to post how you did it.  Following are my "plans" for handling it based on my various searching.

I'm planning on using either the 340.46  or the 343.22 driver.  NVidia's site recommended the 340.46, but the 343.22 is also supposed to support it.
Do you see anything different when you try the following commands:

# list drivers available
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended


If the 337, 340, or 343 is available from above commands then I should be able to install it using:
sudo apt-get install nvidia-"whatever driver name I find in the list that I like"

If not on the above list, then my intention is to install it from the xorg-edgers ppa using the following:
sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update 
sudo apt-get install nvidia-graphics-drivers-340       *(or 343 if I feel lucky)*

Xorg-edgers also has 343, 334, 337, and 331 so you could choose 337 from there if you can't find it in Ubuntu's repositories.  If you add as above, I think the normal software update management will monitor that ppa for updates to the driver.  Xorg-edgers gets the updated drivers quicker than the Ubuntu repositories, often within a few days of Nvidia releasing updates.

I still don't know yet, if the procedure above actually activates the driver, or if you still have to go into "Additional Drivers" to activate it after you install it, or if you have to update the xorg.conf file to activate it.  All to be determined going forward.

Of course you can also download a *whateverdriveryouwant*.run installer file direct from Nvidia which I gather runs a script and dialog to help you set it up.  However I don't think there is any auto-update mechanism for keeping up with future updates included with it.  Adding the xorg-edgers ppa may still keep it updated it even if you get the driver direct from nvidia - not sure.

After installation above I expect that I will need to do the following:
CTRL-ALT-F1   to terminal and login if needed
[I]#stop the GUI/Desktop services
[/I]sudo service lightdm stop
[I]#update xorg.conf to use the new driver using the nvidia tool for that
[/I]nvidia-xconfig
[I]# burn incense, chant, pray, etc...
# reboot
[/I]

Check this link for some good background
[http://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](http://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)

Good luck to us both.

---

### Post by ciryon03 on 2014-10-07
> **sns4rnr said:**
> Looks like I will be in the same boat.  I am currently awaiting a GT730 card for my 14.04 64-bit system (Still a few days away from receiving it).
If you work it out how, be sure to post how you did it.  Following are my "plans" for handling it based on my various searching.at this time I use the 340.46 I found on the PPA I listed a few posts above.

> I'm planning on using either the 340.46  or the 343.22 driver.  NVidia's site recommended the 340.46, but the 343.22 is also supposed to support it.
Do you see anything different when you try the following commands:

# list drivers available
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended
```
yann@yann-desktop:~$  ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000FC8sv00000000sd00000000bc03sc00i00
vendor   : NVIDIA Corporation
driver   : nvidia-340 - third-party free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

yann@yann-desktop:~$ 

```

```
yann@yann-desktop:~$ ubuntu-drivers devices | grep recommended
driver   : nvidia-340 - third-party free recommended
yann@yann-desktop:~$ 
```

> Xorg-edgers also has 343, 334, 337, and 331 so you could choose 337 from there if you can't find it in Ubuntu's repositories.  If you add as above, I think the normal software update management will monitor that ppa for updates to the driver.  Xorg-edgers gets the updated drivers quicker than the Ubuntu repositories, often within a few days of Nvidia releasing updates.it is the PPA I use but it still has not proposed me any better than the 340.46.

> I still don't know yet, if the procedure above actually activates the driver, or if you still have to go into "Additional Drivers" to activate it after you install it, or if you have to update the xorg.conf file to activate it.  All to be determined going forward.you have still to activate it if I remember well.

---

### Post by sns4rnr on 2014-10-07
> **ciryon03 said:**
> Perhaps, where did you find this information ?

I was able to confirm the same browsing Nvidia download site.

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

Got there by selecting the "Beta and Older Drivers" link....   Note the "Find.aspx" vs the "Index.aspx" in the URL.

By searching on an older series card (say Ge Force 400 series), was presented with the full list of potential drivers.  By checking each driver's details, 337.25 indicates GT740 support was added there.  Also if you click each driver, there is a list available that indicates the different cards supported by each driver.

---

### Post by ciryon03 on 2014-10-07
> **sns4rnr said:**
> I was able to confirm the same browsing Nvidia download site.

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

Got there by selecting the "Beta and Older Drivers" link....   Note the "Find.aspx" vs the "Index.aspx" in the URL.

By searching on an older series card (say Ge Force 400 series), was presented with the full list of potential drivers.  By checking each driver's details, 337.25 indicates GT740 support was added there.  Also if you click each driver, there is a list available that indicates the different cards supported by each driver.thanks for the information, I have relayed this to launchpad.

---

### Post by dave0109 on 2014-10-07
> **ciryon03 said:**
> Perhaps, where did you find this information ?
On the nVidia web-site.

[QUOTE=sns4rnr]Xorg-edgers also has 343, 334, 337, and 331 so you could choose 337 from there if you can't find it in Ubuntu's repositories.[/QUOTE]
Actually xorg edgers dropped 337 from their PPA, as I found out when I thought 340 had broken my system (which it hadn't).

In terms of installing the driver, you need to simply add the PPA, refresh the package list, then look for Additional Drivers.  This should find (currently) nvidia-340.  The newer one doesn't get offered yet for reasons I've not bothered investigating.  Choose the driver, apply the changes and reboot.  Job done.

---

### Post by sns4rnr on 2014-10-10
Got my GT730 installed and used the xorg-edgers ppa to get the 340.46 driver...    Had an adventure regarding lack of EDID from my monitor, but not really the driver's fault and finally worked around that.  If not for that, it probably would have been just that simple.

My impression is that each driver package has associated with it a list of graphics cards that the driver supports, and so "Additional Drivers" will only list those driver packages that claim support for your specific card.  When I go to Xorg-Edgers website directly, I find more packages listed there, than the "Additional Drivers" utility bothered to offer me.  So the 337, 334, 340, 343 etc. I think may be there, but if they don't support your card, then you wont see them offered via the Additional Drivers utility.   That may also be why Additional Drivers offers no drivers for these newer cards unless you add this repository (or do some manual install from nvidia's .run files).   If that in fact is the way it works, it's a good thing... help keep people from installing drivers that are "known" not to support a given card.

The thread heading refers to 64-bit installs specifically... so maybe there is a 32/64 bit angle that impacts the drivers offered as well. Some of the older drivers may not support 64 bit OSs and so may not be offered if that's what you have.

---

### Post by grahammechanical on 2014-10-10
Double check that there is a tick in the box labelled Proprietary drivers for devices (restricted). Software and Updates>Ubuntu Software tab.  These two commands will give information about our video card and the drivers available for it.

```
ubuntu-drivers list
ubuntu-drivers devices
```

Regards.

---

