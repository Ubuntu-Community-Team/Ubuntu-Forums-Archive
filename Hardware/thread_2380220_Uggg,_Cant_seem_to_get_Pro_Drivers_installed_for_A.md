---
title: "Uggg, Cant seem to get Pro Drivers installed for AMD RX570 (I Need OpenCL)"
date: 2017-12-14
forum: Hardware
---

### Post by ridshack2 on 2017-12-14
Hi Guys,

Ive been trying like a son of a gun to get my AMD card working with Ubuntu. Ive been following AMDs guide at

[http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)

After I install the driver and reboot Im unable to get past the login prompt. It just keeps kicking me out back to logon. Ive tried 3 different versions of the driver and each says the card is supported. 

After monkeying around I was able to install the NON-pro drivers. The script was something like ./amdgpu-install vs the suggested ./amdgpu-pro-install. 

Ultimately Im trying to get OpenCL working. 

I have searched in vein like a mad man. Any direction would be appreciated. Thank you!

---

### Post by mörgæs on 2017-12-15
Hi, welcome to the fora.

I'm aware that the guide to which you linked mentions 16.04 but have you tried 17.10?

---

### Post by ridshack2 on 2017-12-15
I guess I could install 17.10 since its a fresh install. Ill give it a try. Thanks!

---

### Post by Yellow Pasque on 2017-12-15
The Pro driver does not officially support Ubuntu 17.10.
[https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx](https://support.amd.com/en-us/kb-articles/Pages/Radeon-Software-for-Linux-Release-Notes.aspx)

---

