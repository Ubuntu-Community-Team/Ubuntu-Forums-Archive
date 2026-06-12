---
title: "Stupid error wrong driver sound."
date: 2020-04-22
forum: Hardware
---

### Post by Portaro on 2020-04-22
Yesterday I need to test a webcam on ubuntu and the webcam have much noisy sound cant understand nothing on MIC.
I think that the probem is the driver of sound **and install a wrong driver on the kernel** &#8594; [https://www.realtek.com/en/component/zoo/category/pc-audio-codecs-high-definition-audio-codecs-software](https://www.realtek.com/en/component/zoo/category/pc-audio-codecs-high-definition-audio-codecs-software)

```
lspci00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 **Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)**
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
01:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 710B] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
02:00.0 USB controller: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)



```

**Now I have aproblem only with one of my kernels**, He dont detect any sound card, but if I login with other kernel everithing is ok.

Anyone can help me to solve the problem on the kernel affected, with a help of the configuration module or file that I need to edit or copy to solve the poblem on the affected kernel?

---

### Post by Yellow Pasque on 2020-04-22
1. Boot into the kernel with no sound.
2. Remove the Realtek drivers by running make uninstall in the appropriate directory. For example, if you used your Downloads folder:
```
cd ~/Downloads/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa
sudo make uninstall
```
3. Reinstall the linux-modules packages:
```
sudo apt-get install --reinstall linux-modules-`uname -r` linux-modules-extra-`uname -r`
```
4. Reboot.

---

### Post by Portaro on 2020-04-22
Thanks for your help , unfornately I use a Liquorix Kernel and for some reason cant find linux modules.

```
$ sudo apt-get install --reinstall linux-modules-`uname -r` linux-modules-extra-`uname -r`[sudo] password for joao: 
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
Note, a seleccionar 'linux-image-4.10.0-14.1-liquorix-amd64' em vez de 'linux-modules-4.10.0-14.1-liquorix-amd64'
E: Não foi possível encontrar o pacote linux-modules-extra-4.10.0-14.1-liquorix-amd64 **&#8592; cant find the package**.
E: Não foi possível encontrar o pacote através da expressão regular 'linux-modules-extra-4.10.0-14.1-liquorix-amd64' **&#8592; cant find the package**

```

This kernel runs very well on Ubuntu in past I have serious problems with default kernels provided for ubuntu and I find this way to continue use Ubuntu, really no idea what to do now [B]maybe reinstall this kernel on synaptic method?

[/B]What you think?

```
$ apt-cache search liquorixliquorix-archive-keyring - GnuPG archive keys of the liquorix archive
liquorix-keyring - GnuPG keys of liquorix Developers
linux-image-4.10.0-14.1-liquorix-amd64 - Linux 4.10 for 64-bit PCs
linux-image-4.10.0-11.1-liquorix-amd64 - Linux 4.10 for 64-bit PCs
linux-headers-liquorix-amd64 - Linux headers for liquorix on 64-bit PCs
linux-image-liquorix-amd64 - Linux image for liquorix on 64-bit PCs
linux-headers-4.10.0-11.1-liquorix-amd64 - Header files for Linux 4.10.0-11.1-liquorix-amd64
liquorix-keyrings - Meta package to grab all useful GnuPG keys for liquorix
linux-headers-4.10.0-14.1-liquorix-amd64 - Header files for Linux 4.10.0-14.1-liquorix-amd64

```

Thanks.

---

### Post by slickymaster on 2020-04-22
@Portaro:

Please don't use quote tags when posting terminal output, use code tags instead.

---

### Post by Yellow Pasque on 2020-04-22
> **Portaro said:**
> This kernel runs very well on Ubuntu in past I have serious problems with default kernels provided for ubuntu and I find this way to continue use Ubuntu, really no idea what to do now [B]maybe reinstall this kernel on synaptic method?

It looks like liquorix doesn't split the modules to a separate package. So try reinstalling with this command:
```
sudo apt-get install --reinstall linux-image-4.10.0-14.1-liquorix-amd64 linux-headers-4.10.0-14.1-liquorix-amd64
```

---

### Post by Portaro on 2020-04-22
Thanks for the help.
Now I have other problems that arent connected to Ubuntu but with liquorix for some reason the repository that I use on Ubuntu is closed and my system is old &#8594; 14.04 so big problem here , no support so when I try to do what you suggest I have other errors.

```
dpkg: erro ao processar o pacote liquorix-keyring (--configure):
 subprocesso script post-installation instalado retornou erro do status de saída 2
Foram encontrados erros enquanto processava:
 liquorix-keyring
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



I will proceed to liquorix forum to see if anyone can help me. If not I stay with the other kernel that is provided by ubuntu but with poor performance. Thanks for your help.

---

### Post by Portaro on 2020-04-23
If you have this problem - old Ubuntu with a extra kernel like liquorix and you want to reinstall it in the case of Liquorix you need to follow this steps &#8594;

Update the source repository by Liquorix team page instructions for old kernels (not all of them but some are present)
```


https://software.opensuse.org/download.html?project=home%3Astevenpusser%3Acodelite&package=liquorix


```

```

sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/stevenpusser:/codelite/xUbuntu_14.04/ /' > /etc/apt/sources.list.d/home:stevenpusser:codelite.list"wget -nv https://download.opensuse.org/repositories/home:stevenpusser:codelite/xUbuntu_14.04/Release.key -O Release.key


sudo apt-key add - < Release.key


sudo apt-get update


sudo apt-get install liquorix

**(Or)**
sudo apt-get install linux-image-liquorix-amd64 linux-headers-liquorix-amd64 

[B](if in this step you have a error that return that the package
can't be installed because obs version isnt in the version neede like in my case - (= 5.0-19~obs), change the command) &#8594;
[/B]
sudo apt-get install linux-image-liquorix-amd64 **&&** linux-headers-liquorix-amd64



[B](In case of 32 bits)
[/B]sudo apt-get install linux-image-liquorix-i686 linux-headers-liquorix-i686

**(With pae enabled)**
sudo apt-get install linux-image-liquorix-i686-pae linux-headers-liquorix-i686-pae

[COLOR=#222222][FONT=Verdana]
```

[/FONT][/COLOR]Ok, with this option you can have a method to access Liquorix kernel option to maintain on your old Ubuntu release, in my case 14.04.

In this PC this Kernel is more stable and give more performance that the kernels realeased by Ubuntu officially.

Thanks for all people that help me.

---

### Post by CelticWarrior on 2020-04-23
> Ok, with this option you can have a method to access Liquorix kernel  option to maintain on your old Ubuntu release, in my case 14.04.

Maintaining an En of Life, unsupported release, SHOULD NOT be an option, period. Your system is missing an year worth of security updates already.

> In this PC this Kernel is more stable and give more performance that the kernels realeased by Ubuntu officially.

Really? How did you came to that conclusion? Have you tested latter releases, namely the current 20.04?

---

### Post by Portaro on 2020-04-23
If my system are or not outdated isnt important for the problem in my case works well and if work dont touch.
I antain a look on chkrootkit rkhunter and have a antivirus to use for windows usb etc.

**Kernel Liquorix is better for my hardware and you only need a minute to see this, the pc is much more fast**, and in task manager you can see differences of Ram up to 300 MB.

When I dont have Liquorix on 14 04 I think that this options dont represent big differences but when I try I see a system much more lithe. For example when I have this problem yesterday I pass to use other kernel a generic kernel by Ubuntu ad the system return with much more lag more seconds to open a window etc.

My hardware &#8594;
CPU: AMD A4-6210 APU with AMD Radeon R3 Graphics @ 4x 1.8GHz [49.0°C]
 GPU: GeForce GT 710
 RAM: 1932MiB / 3641MiB

I pass most of time of Lubuntu 14.04 with Liquorix and **when a user suggest me to use it **kernel **I dont have much assurance if this option are good and now I can't use this system with other kernel - big big difference.**

The pc is this &#8594;
[https://www.asus.com/Tower-PCs/K20DA/](https://www.asus.com/Tower-PCs/K20DA/)

Maybe is a interesting post to Ubuntu developers in this case in my hardware there are notorious differences, and with the tests that I do with new live ISO of Lubuntu there are not differences of performance with a live of 14.04 so probably in new releases if you use liquorix on some hardware you have also better performance.
Of Corse Ubuntu with gnome is much more slow compared with LXDE or Openbox on this type of machines of 2016.

---

### Post by CelticWarrior on 2020-04-23
> **Portaro said:**
> If my system are or not outdated isnt important for the problem in my case works well and if work dont touch.
I antain a look on chkrootkit rkhunter and have a antivirus to use for windows usb etc.

This is completely ignorant. Not having security updates in a computer connected to the internet IS A PROBLEM in itself. Only a very irresponsible user would think otherwise. There are known remote attack vectors for your system that haven't been patched and won't be ever patched, unless you have a payed support, which of course you don't have.

> 
My hardware &#8594;
CPU: AMD A4-6210 APU with AMD Radeon R3 Graphics @ 4x 1.8GHz [49.0°C]
 GPU: GeForce GT 710
 RAM: 1932MiB / 3641MiB



So this old(ish) hardware is the reason for keeping an unsupported OS with a Frankenstein kernel? This is even more ignorant with surreal on top... AMD APUs are very well supported by any 4.xx and even better since 5.xx for newer APUs and the current Ryzen crop. For the AMD A4-6210 the original 4.15 kernel of Ubuntu 18.04 already has perfect support which hasn't improved in later versions. So, the exact same performance you think you're getting from the non-standard kernel would have been available with the HWE kernels of 14.04, i.e., any except the original LTS - 14.04.1 and all point releases since. Ubuntu 16.04 would have kept the exact same performance and is still supported, ditto for 18.04 and the current 20.04. And the GT710 is still supported by the newest driver but that driver cannot be installed in 14.04. And funnily there's ZERO mention of Nvidia drivers in your ramblings which suggests you never installed it?? That being THE thing that really makes a difference for performance, not installing it and complain about performance takes this surreal thread to a whole new level.

---

### Post by Portaro on 2020-04-24
You have reason in general and most efficient use of any system is use it with enable updates and security updates.
But there are exceptions I think, is only my opinion.

In my case I have nvidia graphic card with non-free drivers, in effect you can install the drivers with some "cheats" on the system needs a choose of target verion of drivers to install, and is ossible install on a generic kernel also liquorix.

[COLOR=#000000][FONT=monospace][img=200x100][/FONT][/COLOR]https://framapic.org/ULrENu08yRb0/bfYMaPAPGhNd.png[COLOR=#000000][FONT=monospace][/img]

Cheers.[/FONT][/COLOR]

---

