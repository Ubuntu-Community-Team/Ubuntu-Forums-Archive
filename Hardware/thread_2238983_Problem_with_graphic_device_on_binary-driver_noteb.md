---
title: "Problem with graphic device on binary-driver notebook"
date: 2014-08-11
forum: Hardware
---

### Post by scholzvojta on 2014-08-11
Hi,
on my notebook I have two graphical device. AMD **HD6470M** and AMD M880G with ATI Mobility Radeon **HD 4250**. Ubuntu automatically select the second graphical card, but it isn't so powerfull as I want.
```
ubuntu@ubuntu:~$ lspci -vnn | grep VGA
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] [1002:9712] (prog-if 00 [VGA controller])
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760] (rev ff) (prog-if ff)
```
I tryed to select HD6470M in Ubuntu 13.04, 13.10, 14.04, but result was the same: **System is running in low-graphic mode**. Recently I found out, that driver fglrx used in these version don't support Radeon HD 6400M/7400M Series.
My process:
```
sudo apt-get install linux-headers-generic
sudo apt-get install fglrx fglrx-amdcccle
```
but:
```
root@Vojta-PC:/home/vojta# sudo amdconfig --initial -f
amdconfig: No supported adapters detected
root@Vojta-PC:/home/vojta# sudo amdconfig --px-dgpu
amdconfig: No supported adapters detected
```
I got advice to try Unutnu 12.04.1. Driver fglrx used in this version allegedly support Radeon HD 6400M/7400M Series.
My process:
```
sudo apt-get install linux-headers-generic
sudo apt-get install fglrx fglrx-amdcccle
sudo amdconfig --initial -f
sudo amdconfig --px-dgpu
```
But result was that screen of Ubuntu stayed purpure. It was all. I have heart login sound even, but nothing to seen.
[X.org log here.]("https://drive.google.com/file/d/0BzO1nkmWvksgUVVPZTdlSko0TVU/edit?usp=sharing") (So big for attachement :D)
Do you know, how to solve it. Thanks.

---

### Post by Mark Phelps on 2014-08-11
You have two very different problems.  First, you have an HD 4x-series video chipset, and the last Ubuntu version to support the fglrx drivers was 1204.1.  Second, you have dual AMD graphics -- and as far as I know, none of the downloadable fglrx drivers support dual AMD graphics.

Sorry, but the only option you might have is to remove all the fglrx drivers and go with the default open-source Radeon drivers.

---

### Post by scholzvojta on 2014-08-11
It isn't problem, use open-source radeon drivers. I only wont to select HD6470M, because AMD M880G with ATI Mobility Radeon **HD 4250**, for example, don't be eble to play FullHD video. I need to use that powerful graphic card.

---

### Post by Mark Phelps on 2014-08-11
Unless there is a way to disable the HD 4250 in the BIOS, you're stuck with the on-demand video situation.

---

### Post by scholzvojta on 2014-08-11
I don't have these options in BIOS :( I have Insyde H2O F.52 and i can's see ADVANCED options.

---

### Post by scholzvojta on 2014-08-12
I can't disable HD4250 because HDMI output using it.

---

