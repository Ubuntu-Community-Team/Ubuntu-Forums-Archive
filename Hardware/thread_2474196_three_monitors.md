---
title: "three monitors"
date: 2022-04-23
forum: Hardware
---

### Post by devdlp on 2022-04-23
I have three monitors.
What happen was i switch back to kubuntu, then all three monitors worked.
Until i added the nvidia drivers now just my main thats connected to the gpu is working the two
connected to the onboard arent working anymore.
also the main monitor wont correctly apply 1920x1080 anymore its slightly off.
Cant see much of the taskbar. Any ideas?

---

### Post by devdlp on 2022-04-23
I saw something online that says try to change settings on the tv which mines is a vizio but it didnt help.
my gpu is a nvidia 1060 6gb

---

### Post by TheFu on 2022-04-23
Which nvidia driver release?
Have you played with the nvidia-settings and nvidia-xsettings applications?
Definitely ensure that the resolutions and refresh rates for each monitor connection are standard, supported.

I haven't played with multiple monitors in years and never had 3, so consider me a clueless sounding board only.
Last time I did, I had to manually add 
```
Option         "DPMS"
```
to each of the monitor sections of the xorg.conf file.  I had 2 monitors, so monitor0 and monitor1 needed that line added.

---

### Post by devdlp on 2022-04-23
their connected to the on-board the other two. and  im using nvidia driver 450 im playing around with it now and 
i havent been able to mess with it much because ive been at work so sorry
for the late response

---

### Post by devdlp on 2022-04-23
i fixed the monitors and the resolution both by switching to the open source nvidia driver.
But a pop-up showed at login saying: It was not possible to find the NVIDI NV-CONTROL X extension on the current Display device.
Please make sure that the NVIDIA proprietary display drivers are installed and they support your current GPU. What can be done to fix this issue now?

---

### Post by TheFu on 2022-04-24
A saw that for 22.04, Canonical had backed out the Wayland default for nvidia GPUs.  Don't know if that matters or not.

For older releases, **sudo ubuntu-drivers autoinstall** would get the correct driver for the release and the kernel.  I vaguely remember reading somewhere that 22.04 had removed the *autoinstall* option, so that a specific release was necessary. Canonical has made the kernels on each release too complex, it appears.

I know that yesterday, as part of my patch cycle, I tried to update the nvidia driver to 510 from 470 and ended up stuck at 1024x768 resolution. The 510 driver was from the Ubuntu repos for my release, BTW.  sudo ubuntu-drivers autoinstall removed the 510 versions and reinstalled the 470 nvidia code. Reboot and I'm back to 1920x1200.  Losing 50% resolution is unacceptable to me. That's what I get for being greedy.

There is a GUI for these things too. "Additional Drivers" ... have you run that?

Found this a few minutes later ... nvidia, vms, wayland.
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-22.04-OSInfo-3D-VMs](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-22.04-OSInfo-3D-VMs)

---

### Post by devdlp on 2022-04-24
i tried **sudo ubuntu-drivers autoinstall the control panel additional drivers switching between almost all of them nothing helps**

---

### Post by devdlp on 2022-04-24
so i found an adapter that turned one of the other monitors to dvi and connected it to the gpu along with the third now two monitors show but still cant get 1920x1080 with 60hz.

---

### Post by devdlp on 2022-04-25
i still need help with the tird monitor somehow i got two monitors to work all three are in the gpu but one still wont come on what can i do i can live without the 1920x1080 on the main monitor i just need all three on plz

---

### Post by devdlp on 2022-04-27
i upgraded to 22.04 and switch my second monitor to my main so its 1080p now but the third one wont recognize in display thats the only issue now everything else is fine please help me get this third monitor on

---

### Post by devdlp on 2022-11-29
so im back to this im on Ubuntu 22.04.1 and i have 3 monitors coming back from windows 10 and one monitor is blank but on so idk whats that about anybody know how to get 
all three working two in the gpu the one thats not on is connected to onboard hdmi

---

### Post by mIk3_08 on 2022-11-29
> **devdlp said:**
> so im back to this im on Ubuntu 22.04.1 and i have 3 monitors coming back from windows 10 and one monitor is blank but on so idk whats that about anybody know how to get 
all three working two in the gpu the one thats not on is connected to onboard hdmi Just use the DP port (Display Port) only and add DP hub to be able to display all monitor simultaneously. Regards and cheers

---

### Post by QIII on 2022-11-29
Using a DP hub does not solve the problem, it simply skirts it.  Besides, we don't need to be spending the OP's money.


> **devdlp said:**
> I have three monitors.
What happen was i switch back to kubuntu, then all three monitors worked.
Until i added the nvidia drivers now just my main thats connected to the gpu is working the two

This time, did you start with a fresh installation of Kubuntu and later add the NVidia driver?  Is the GPU on the mobo NVidia?  That that the one that you are getting no output from?

---

### Post by devdlp on 2022-11-29
i have a display port adapter that i could connect to the gpu then all three will be connected to the gpu but that doesnt work anyway.
same outcome. this is a two day old ubujntu 22.04.1 install not kubuntu. im currently using the 515 nvidia driver right now and i have no clue what mobo is

---

### Post by QIII on 2022-11-29
It would be helpful if you would find out some information about your mobo.  If the GPU is NVidia and the onboard graphics are Intel, you may have problems.

It matters.

---

### Post by devdlp on 2022-11-29
its a msi motherboard intel i7 processor 1060 gtx 6gb gpuim sorry i dont know the full model of the motherboard but im thinking thats what a mobo is

---

### Post by devdlp on 2022-11-29
sudo dmidecode -t 2
[sudo] password for chewy: 
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: MSI
	Product Name: Z97 PC Mate(MS-7850)
	Version: 1.0
	Serial Number: To be filled by O.E.M.
	Asset Tag: To be filled by O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To be filled by O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

---

### Post by mIk3_08 on 2022-11-29
I agree with QIII as it will need a additional proprietary video driver. NVIDIA needs proprietary driver when you use Linux Ubuntu Operating System. Regards and cheers.

---

### Post by devdlp on 2022-11-29
so what can i do?

---

### Post by mIk3_08 on 2022-11-30
Go to software & updates then in the tab -> Additional Drivers. Try to see if any video proprietary driver is available to use for your system. Regards and cheers.

---

### Post by devdlp on 2022-11-30
i moved back to wayland all three monitors work now but my laffte dock dont work ill lived with that. thanks you guys ima say this is solved

---

