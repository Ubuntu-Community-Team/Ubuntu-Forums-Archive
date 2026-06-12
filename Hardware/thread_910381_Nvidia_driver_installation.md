---
title: "Nvidia driver installation"
date: 2008-09-04
forum: Hardware
---

### Post by goodbadwolf on 2008-09-04
Hi,
I just bought a compaq presario cq50 106 AU and installed Ubuntu 8.04 on it. My screen resolution was limited to 800x600 so i installed nvidia-glx-new and nvidia packages from synaptic. When i run nvidia-settings , it asks me to run nvidia-xconfig as root. and restart X. when i run nvidia-xconfig as root , it gives me a message "VALIDATION ERROR Device does not have driver line". When i restart X by restarting the laptop, the screen blacks out. When i reboot it in recovery mode and do "Try to repair X" , the login screen comes up as usual. What do i do ?

Configuration : 
Compaq Presario CQ50-106AU, based 1.9 GHz of AMD Athlon X2 Dual-Core with NVIDIA MCP7MV Chipset (NVIDIA GeForce Go 8200M, Up to 128MB of shared video memory), 1GB of DDR2 RAM, 160GB of 5400RPM SATA, 15.4&#8243; Widescreen colour TFT, integrated webcam, LAN, WiFi, Card Reader.

---

### Post by Onyxblack on 2008-09-04
(go to comand prompt)

```
ctrl+alt + f3
```

(stop x server)

```
sudo /etc/init.d/gdm stop
```

(go to driver location)

```
cd <path to driver>
```

(install driver)
```

sudo sh NVIDIA-Linux<whatever>.run
```

(after installing the driver it should bring you back to the comand promp)
```

sudo /etc/init.d/gdm start
```

(this should bring you back to a WORKING desktop with drivers working, once there do)


```
sudo nano /etc/default/linux-restricted-modules-common

```
(edit the line to make it look like)

```
DISABLED_MODULES="nv nvidia_new"
```

Restart your comp - should all work after that

---

### Post by goodbadwolf on 2008-09-04
I do not have a .run file. I installed the nvidia driver from synaptic

---

### Post by goodbadwolf on 2008-09-05
I got it done. I manually installed the 173.* driver using envy. It works fine now.

---

### Post by vishal_karira on 2008-09-12
> **goodbadwolf said:**
> I got it done. I manually installed the 173.* driver using envy. It works fine now.

how have you done it manually. can you give me exact steps to do it as i am new to do it. mine display drivers are not working properly and also my lan is not working.

---

### Post by vishal_karira on 2008-09-12
> **goodbadwolf said:**
> Hi,
I just bought a compaq presario cq50 106 AU and installed Ubuntu 8.04 on it. My screen resolution was limited to 800x600 so i installed nvidia-glx-new and nvidia packages from synaptic. When i run nvidia-settings , it asks me to run nvidia-xconfig as root. and restart X. when i run nvidia-xconfig as root , it gives me a message "VALIDATION ERROR Device does not have driver line". When i restart X by restarting the laptop, the screen blacks out. When i reboot it in recovery mode and do "Try to repair X" , the login screen comes up as usual. What do i do ?

Configuration : 
Compaq Presario CQ50-106AU, based 1.9 GHz of AMD Athlon X2 Dual-Core with NVIDIA MCP7MV Chipset (NVIDIA GeForce Go 8200M, Up to 128MB of shared video memory), 1GB of DDR2 RAM, 160GB of 5400RPM SATA, 15.4&#8243; Widescreen colour TFT, integrated webcam, LAN, WiFi, Card Reader.

i tried to install the nvidia graphics but after restarting it is showing a blank screen but my windows display is working fine. whatshould i do and also i am not able to recover it from the recovery mode from the main menu. so what should i do and how should i recover.

---

### Post by sumeet_salvankar on 2009-02-06
i tried to install ubuntu 8.04 on my laptop but the audio output was not clear I hv compaq cq50-106-au laptop

---

