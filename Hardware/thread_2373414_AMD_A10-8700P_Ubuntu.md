---
title: "AMD A10-8700P Ubuntu"
date: 2017-10-05
forum: Hardware
---

### Post by jimenezhidtavo on 2017-10-05
I got a HP Laptop with AMD A10-8700P Carrizo APU, and I cant use any Ubuntu distro cause display goes black in instalation or however... I have listened that this problem is caused by driver, but i dont know how to solved it or which distribution should I use, i like Xubuntu. Thx.

---

### Post by Yellow Pasque on 2017-10-06
Any recent distro should work with Carrizo using the default open source "amdgpu" driver. In other words, you shouldn't need to install/modify any video drivers. It sounds more like you're experiencing a bug. I would probably try a Xubuntu 17.10 .iso (assuming your download bandwidth isn't capped) to see if the issue has been solved: [http://cdimage.ubuntu.com/xubuntu/releases/17.10/beta-2/xubuntu-17.10-beta2-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/17.10/beta-2/xubuntu-17.10-beta2-desktop-amd64.iso.torrent)

The proprietary "amdgpu pro" driver does not support Carrizo/Radeon R6.

---

### Post by gordintoronto on 2017-10-06
Try nomodeset. It's a boot option, see this doc.

This web page: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
in this section: Changing the CD Boot Option Configuration Line

---

### Post by jimenezhidtavo on 2017-10-06
I have tried with Ubuntu 14, 15, 16, 17 and none works, only in nomodeset mode, but graphics are so bad, my laptop: [https://support.hp.com/ve-es/document/c05194397](https://support.hp.com/ve-es/document/c05194397) and sometimes Wlam fails...

---

### Post by Vasu_Muppalla on 2017-10-06
I have a bristol ridge HP notebook and the GPU is also seen by linux as Carrizo. I was able to install kubuntu 17,04 and now 17,10 beta. Both run fine though the beta is better as it has newer amdgpu drivers. Only issue I had was with realtek 8723be wifi driver- it was slow as it wasn't selecting proper antenna. So I had to modprobe with ant_sel=2 and it is now working normally. I'd install with wired connection then tinker with wifi if you have a realtek card.

---

### Post by jimenezhidtavo on 2017-10-07
I will tray... How did you configure the BIOS?

---

### Post by Yellow Pasque on 2017-10-07
When you have a blank screen, can you press Ctrl+Alt+F1 and get to a terminal?

---

### Post by jimenezhidtavo on 2017-10-07
No

---

### Post by wildmanne39 on 2017-10-07
I have the exact same hardware and the same issue, have tried everything I can find on google, but nothing has helped. I will watch this thread and hope a solution is found.

---

### Post by jimenezhidtavo on 2017-10-07
I've heard that it's better to change the computer

---

### Post by jimenezhidtavo on 2017-10-07
> **Vasu_Muppalla said:**
> I have a bristol ridge HP notebook and the GPU is also seen by linux as Carrizo. I was able to install kubuntu 17,04 and now 17,10 beta. Both run fine though the beta is better as it has newer amdgpu drivers. Only issue I had was with realtek 8723be wifi driver- it was slow as it wasn't selecting proper antenna. So I had to modprobe with ant_sel=2 and it is now working normally. I'd install with wired connection then tinker with wifi if you have a realtek card.
It seems that Kubuntu works fine, at least the installation medium, but I dont like that distro, do you know of another distro that works?

---

### Post by wildmanne39 on 2017-10-07
I tried to install kubuntu and the screen went blank before I could even set up the partitions. So no it is not working, I did not think it would because it uses the same kernel and video card driver as Ubuntu but it was worth a try. Some how you just got lucky.

---

### Post by jimenezhidtavo on 2017-10-07
I gave up, tried everything and nothing worked.

---

### Post by wildmanne39 on 2017-10-07
I have several computers, on this laptop I run Ubuntu in virtualbox on windows 10 but every few days I try to resolve the issue, I thought I had it working a few days ago but then I updated 17.10 and it stopped working again.

---

### Post by jimenezhidtavo on 2017-10-07
> **wildmanne39 said:**
> I have several computers, on this laptop I run Ubuntu in virtualbox on windows 10 but every few days I try to resolve the issue, I thought I had it working a few days ago but then I updated 17.10 and it stopped working again.
I've read all kinds of post and solutions, I think it's something that gave support to these APUs...

---

### Post by wildmanne39 on 2017-10-07
My understanding it is a bug in the driver.

---

### Post by jimenezhidtavo on 2017-10-07
> **wildmanne39 said:**
> My understanding it is a bug in the driver.
Yes it is, i know there is in post where they explain the error, but it is in Spanish.

---

### Post by wildmanne39 on 2017-10-07
Will you please use google translate and post the information here?

---

### Post by jimenezhidtavo on 2017-10-07
> **wildmanne39 said:**
> Will you please use google translate and post the information here? I'll locking for it.

---

### Post by wildmanne39 on 2017-10-07
Thank You!

---

