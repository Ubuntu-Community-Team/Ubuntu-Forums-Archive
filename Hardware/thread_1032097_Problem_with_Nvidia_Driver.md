---
title: "Problem with Nvidia Driver"
date: 2009-01-06
forum: Hardware
---

### Post by shadow_dude on 2009-01-06
Hey all. Just got a new Asus laptop with an Nvidia GeForce 9300M GS W/ 512 MB VRAM graphics card. I installed Ubuntu with Wubi, and wanted to enable Compiz Fusion. However, I cannot even turn on Desktop effects, because the restricted driver program refuses to do anything. It opens, suggests 2 different Nvidia drivers(Versions 173 and 177). Click on either one, and it asks for S.U. password. Then, a little progress bar box shows up with a 0% in the middle, a little orange bar bounces around for a second, and then it closes, and the restricted drivers are unchanged:confused:. Is there any way to fix this? Could the driver servers be down? I am connecting with WiFi, would an Ethernet connection help anything? Is there a terminal command that would help? I appreciate any efforts to help. Thanks, Guys.:)

---

### Post by gettinoriginal on 2009-01-06
If you are running Intrepid, type these into terminal one at a time, if not Intrepid, edit for you distro:
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
Now try to install drivers via System > Admin > Hardware Drivers.:P

---

### Post by zeronothing on 2009-01-06
I would try installing the new beta driver available on the Nvidia website. I originally had the nvidia driver 177 verison from the repository and had windows manager problems. after I installed the newest nvidia 180 beta driver it really fixed alot of my issues. it also seem to make things flow much better in terms of the compiz effects. all you have to do is make sure you have the build-essentials package installed from the ubuntu repository. Then go to the nvidia website and download the beta driver. make sure you download it for the right architecture 32-bit or 64-bit. then its just a matter of opening up terminal and executing the install script. usually the drivers from nvidia website you had to manual specify prefixes and stuff but this newest beta driver you just have to execute the script and it will do everything for you.

---

### Post by zeronothing on 2009-01-06
here is the link to the Nvidia 180.17 beta driver for 32-bit:

[http://www.nvidia.com/object/linux_display_ia32_180.17.html](http://www.nvidia.com/object/linux_display_ia32_180.17.html)

here is the link to the Nvidia 180.17 beta driver for 64-bit:

[http://www.nvidia.com/object/linux_display_amd64_180.17.html](http://www.nvidia.com/object/linux_display_amd64_180.17.html)

---

