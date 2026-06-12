---
title: "Lost my Radeon driver and now can't install it"
date: 2013-11-17
forum: Hardware
---

### Post by bachtobach on 2013-11-17
I installed the KXstudio repos and during all the updates it installed I somehow lost my proprietary drivers, both the AMD graphics driver and my Broadcom wifi driver. I've managed to get the wifi working (although I'm not convinced everything is ok there but I'll start a new thread for that) but I cannot get the AMD driver installed. 

I've tried to follow the steps [here.]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide") I perform the wget command to get the latest driver, it says it is saved but then when I do the next command to unzip it it says that it cannot be found. I tried downloading the driver manually and then replacing the file name in the command but that doesn't work either. I tried to manually unzip the driver and run it but I get a message saying I need to be a super user to run it. I tried sudo *filename* but that doesn't work, says it can't find the file. 

I am running xubuntu 12.04 with a Dell Inspiron 1545.  

lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RV710/M92 [Mobility Radeon HD 4330/4350/4550]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff ioport:de00(size=256) memory:f6df0000-f6dfffff memory:f6d00000-f6d1ffff

sudo lshw -c video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RV710/M92 [Mobility Radeon HD 4330/4350/4550]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff ioport:de00(size=256) memory:f6df0000-f6dfffff memory:f6d00000-f6d1ffff


I don't know what else to do, I've been searching the forums but I can only find directions for the above link.

---

### Post by heir4c on 2013-11-17
I think the HD 4xxx Series are no more supported.
Look via Systemsettings to Details. Next to "Graphics" there you see now: Gallium 0.4 on AMD PALM
That's the OpenSource driver for Linux.
Open via the Dash: "Software&Updates and choose the last Tab for the graphics drivers. After a while he search for drivers, what see you than?

---

### Post by bachtobach on 2013-11-17
[**[COLOR=#000000]heir4c[/COLOR]**]("http://ubuntuforums.org/member.php?u=739011") I don't understand your post. 

"Look via Systemsettings to Details" 
I don't know where this is, there isn't a systemsettings option as far as I can see, anywhere. 

"Open via the Dash"
I don't have a Dash, that's in Unity isn't it? If you mean the additional drivers section, I looked in there and it doesn't show any graphics driver. 

I previously didn't do anything to install the driver, it was automatically picked up and installed when I installed xubuntu and I just selected to use it. Now it seems to have gone and I can't seem to get it back.

---

### Post by heir4c on 2013-11-17
Sorry you use Xubuntu, I look it up on my Laptop with Xubuntu on. One moment please....

---

### Post by heir4c on 2013-11-17
Click on the menu-button on the left and go to Settings (or systemsettings or settings manager) (I run a Xubuntu in Dutch). There you see something like "additional drivers". The system now searching for drivers. What he say about drivers?
This is the icon next the app/program title that you looking for:

[IMG]http://i.imgur.com/TzYQNJn.png[/IMG]

---

### Post by bachtobach on 2013-11-17
That only shows the broadcom wireless driver (which is inactive and disables wifi if I try to enable it), no graphics driver shows in there.

---

### Post by heir4c on 2013-11-17
Than he is now running with the OpenSource Driver and it is no longer supported by the AMD driver. I had it here also with my old Laptop. Before I could use non-free drivers but now it's just the opensource I can use.

---

### Post by bachtobach on 2013-11-17
Oh that's not good news. Was it the kernel update that caused that?

---

### Post by bachtobach on 2013-11-17
The reason I was concerned about installing the AMD driver is that the fan on my laptop seems to be running high a lot of the time, I googled around a bit and I read that it could be fixed by installing the AMD driver. I had this problem when I tried 13.10 but I ended up going back to 12.04 and that solved the problem, I assumed it was just a bug in 13.10 but obviously not. Is there no fix for this problem them?

---

### Post by heir4c on 2013-11-17
You can always try to install the AMD driver and see what happens. I don't know else what you can do. I'm very sorry.

---

### Post by bachtobach on 2013-11-17
Well I was trying to install the driver, I have it downloaded and it is a .run file but when I run it it says I need to be a super user, I don't know how to run it as sudo/root.

---

### Post by heir4c on 2013-11-17
Here is a link with info about the drivers for ATI/AMD, there mentioned your card that this is supported yet, but maybe it is not updated. although they mentioned the kernel version 3.11 at the bottom under the Audio section:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by heir4c on 2013-11-17
Sorry, ... (I deleted a wrong answer...)

---

### Post by heir4c on 2013-11-17
Right click on the file and click on "Properties". Look for the permissions. Check the box next to the text at the bottom that say: "Allow this file to run as a program". Than close that window and doubleclick on the file. Now you must get a window with options to run it or run in terminal or to display the text with gedit. If that not happens, than open a terminal and drag the file from nautilus into the terminal (now you see the file name in the terminal) and click Enter.

---

### Post by bachtobach on 2013-11-17
The permission of the file is set to root and all the options are greyed out. I tried dragging it in to the terminal but it said permission denied.

---

### Post by heir4c on 2013-11-17
Strange but ok.
Type first in the terminal: sudo
and click on the space bar and drag than the file into the terminal and then Enter. If it not work than remove the ' that you see at the beginning and the end of the filename in the terminal.

---

### Post by Mark Phelps on 2013-11-17
>  I assumed it was just a bug in 13.10 but obviously not. Is there no fix for this problem them? 

Support for the AMD restricted driver for your card stops with Ubuntu 12.04.1.  If you installed or upgraded to a recent version of 12.04, the AMD driver will not work anymore.

Sorry, but Ubuntu versions newer than 12.04.1 will not work with the AMD drivers and your video card.  You are stuck using the default open-source Radeon drivers.

AMD has dropped support for the HD 2x/3x/4x-series cards.

---

### Post by bachtobach on 2013-11-17
> **heir4c said:**
> Strange but ok.
Type first in the terminal: sudo
and click on the space bar and drag than the file into the terminal and  then Enter. If it not work than remove the ' that you see at the  beginning and the end of the filename in the terminal.

Weird, I tried that using sudo with and without the ' at the  beginning and end but it says command not found for all combinations. 


> **Mark Phelps said:**
> Support for the AMD restricted driver for your card stops with Ubuntu 12.04.1.  If you installed or upgraded to a recent version of 12.04, the AMD driver will not work anymore.

Sorry, but Ubuntu versions newer than 12.04.1 will not work with the AMD drivers and your video card.  You are stuck using the default open-source Radeon drivers.

AMD has dropped support for the HD 2x/3x/4x-series cards.

Thanks for the information, not what I wanted to hear but good to know anyway. 

With regards to the issue of the fan running high all the time, I booted back in to the 3.2 kernel (had upgraded to 3.8) and it has fixed the issue. I'm not sure of the consequences of using the old kernel versus the new one though.

---

### Post by heir4c on 2013-11-17
> Weird, I tried that using sudo with and without the ' at the beginning and end but it says command not found for all combinations. 
There must a space left between the sudo and the filename:
```
sudo 'home/your-username/Downloads/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run'
```

---

### Post by bachtobach on 2013-11-17
> **heir4c said:**
> There must a space left between the sudo and the filename:
```
sudo 'home/your-username/Downloads/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run'
```


Yeah that's what I've done - sudo '/home/alex/Downloads/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run' - but still the same thing.

---

