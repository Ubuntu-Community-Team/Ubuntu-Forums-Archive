---
title: "White screen when I try to activate graphic effects"
date: 2008-10-30
forum: Hardware
---

### Post by zhongguohua88 on 2008-10-30
Hi everyone, I am totally new to Linux and installed Ubuntu 2 days ago on a brand new HP Elitebook 8530w with an NVIDIA Quadro graphic card. I used to get the 'desktop effect could not be enabled' error but after a lot of struggle, I managed to install the NVIDIA Linux driver. I am not getting the error message anymore but whenever I try to enable desktop effects, my screen turns completely white. If I press tab, it becomes normal again but the visual effect option goes back to 'None'. It does the same thing whether I try the 'Normal' or the 'Extra' feature.

How can I fix this? I have searched on these forums but nothing worked! Sorry if this is a stupid question, but I am still very unfamiliar with Linux.

---

### Post by phidia on 2008-10-30
Could you provide the video card model? If you don't know the model number open a terminal and copy and paste this > lspci | grep VGA

You didn't say how you eventually got the driver working-if it is fully working-but that's important information too.

---

### Post by zhongguohua88 on 2008-10-30
Here is what the terminal displays:
> philipp@philipp-laptop:~$ lspci | grep VGA 
01:00.0 VGA compatible controller: nVidia Corporation Device 065c (rev a1)

I got the driver NVIDIA-Linux-x86_64-177.80-pkg2.run from the official NVIDIA website and I saw the NVIDIA logo after restarting so I assumed the installation was successful. If I go into 'Hardware Drivers' it tells me 'No proprietary drivers are in use on this system'.

---

### Post by Sanix on 2008-10-31
Actually, Ubuntu offers you a restricted driver which works. Does it really run fine for you? Because I haven't heard of anyone, who has no problem with this notebook and Ubuntu. It only works without acpi support and hangs during login.

---

### Post by zhongguohua88 on 2008-10-31
> **Sanix said:**
> Actually, Ubuntu offers you a restricted driver which works. Does it really run fine for you? Because I haven't heard of anyone, who has no problem with this notebook and Ubuntu. It only works without acpi support and hangs during login.

When I try to install these the 'Downloading and installing driver' window stays at 0% and never downloads or installs anything.

As for Ubuntu, I usually have to start my computer 5-6 times in order to run the OS properly because Ubuntu won't start if my wireless light is off even though I have no wireless connection and just pressing on the wireless button dowsn't turns it on. I have to press the Mute button and turn the sound on and off very quickly when Ubuntu is loading and eventually it turns the wireless light on. Once the OS loaded, the wireless button works properly and pressing the Mute button doesn't change the wireless connection anymore.doesn't turns it on (there are no buttons for the wireless light, only a touch pad). I am quite dissapointed considering the price I paid for this laptop and the time I had to wait (it took HP 2 months to deliver the Laptop due to 'supply shortage'). Maybe this is because the hardware was designed to run Windows Vista.

---

### Post by falstaff on 2008-11-02
Do you use Ubuntu 8.04? The Wirelesscard is only supported in latest kernel, which is also in 8.10. Therefor I suggest to use 8.10. But with 8.10 you will have some ACPI troubles, which you can solve by change a BIOS option, see this thread: [http://ubuntuforums.org/showthread.php?t=957447&highlight=8530w]("http://ubuntuforums.org/showthread.php?t=957447&highlight=8530w")

Sound also didn't worked for me, but this is solved too, see here [http://ubuntuforums.org/showthread.php?t=958500&highlight=8530w]("http://ubuntuforums.org/showthread.php?t=958500&highlight=8530w")

bye
falstaff

---

### Post by lgcabarcas on 2008-11-02
Wait, just wait . I've also got the 0% progress indicator, but after a couple of minutes the thing jumped to a 69% and 5 seconds after everything it's setup ;)

---

### Post by zhongguohua88 on 2008-11-24
I have no more problems with the graphic effects, my only problem is now with booting. I do not want to restart my computer 5-10 times every times in order to boot Ubuntu. I do have the latest Ubuntu installed anmd it still isn't working. When I boot, I now have the choice between 2 Ubuntu (both have the wireless problem) and 2 Windows Vista (they both load the same thing).

---

