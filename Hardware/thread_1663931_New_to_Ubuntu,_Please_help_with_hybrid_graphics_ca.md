---
title: "New to Ubuntu, Please help with hybrid graphics card problem"
date: 2011-01-10
forum: Hardware
---

### Post by Sohrab Kakakhel on 2011-01-10
Hi,
Just want to say right here that this is the first time im ever using the linux platform. So I don't understand anything about it, specially the codes and all that. I installed the new version 10.10 64 bit and am currently using a Sony Vaio VGN-Z620N.

As soon as I installed it, it was working fine till it told me I needed to install additional drivers for my NVIDIA graphics card. My laptop has a hybrid graphics card. A Geforce 9300M and Intel VGA graphics. Anyways when I start ubuntu, it doesnt load the graphic interface and I just get command line asking for login. When i log in nothing happens. I have no idea about commands. I searched the internet and tried many commands like startx etc. The only way I can access ubuntu is through recovery mode and then running it with failsafe graphics. I download the newest drivers but I have NO idea how to install them. Tried synaptic but i cant seem to drag the file into it or something of the sort. So I can't use my graphics card and I cant start Ubuntu unless its in recovery mode. 

Please help. I was looking forward to using linux. I've used windows my whole life, and have no idea how to get about this. Thankyou in advance

---

### Post by Marcelo Ruiz on 2011-01-10
I am not an expert either, but maybe this can help you:

1- Start your computer and go into recovery mode.
2- Select the last option of the menu to go into the root terminal.
3- Type the following command to remove all the Nvidia drivers (you need to press Enter after the last character):

```
sudo apt-get --purge remove nvidia-*
```

4- After the previous command completes, type the following to restart the computer:

```
reboot
```

Regarding the hybrid graphics card, there is some work going on in the kernel to support it, but Intel and Nvidia are not willing (so far) to work together to provide a driver to support those cards (maybe another complaint to Nvidia will help).

I hope it helps :)

---

### Post by Sohrab Kakakhel on 2011-01-11
Thank you marcelo, it worked!! Hahaha can't thank you enough.

---

### Post by riyasmp on 2011-01-12
hi guys

I recently baught a hp dv-6 3150sa laptop which uses ATI mobilty readon HD 5470 graphics9switchable with intel HD GMA). after partitioning i could install ubuntu 10.10 without any problems.

on first restart ubuntu recomnded ATM/AMD proprietary FGLRX graphics driver which i installed straight away. on my next reboot it showed grub and while on choosing ubuntu it went to the command mode. I had to reinstall ubuntu to get back the genome desktop.

I tried installing switcehroo. It identifies my intel graphics card but wheni switch to high perfomance the compiz disappears. i am not sure whats happning here. tried installing the latest dricer for ATI from the website.but no joy

thanks in advance

---

### Post by Marc128000 on 2011-01-18
@riyasmp You can't use hardware acceleration right now. The Linux ATI driver doesn't properly support hybrid graphics systems. Sadly the open source ATI driver doesn't support hardware acceleration either.

In my blog I cover these issues in detail, I also show how to install the scripts and stuff that are needed to turn off the discrete (higher powered) video card to save power.

Hopefully it will be useful.
[http://linuxenvy.blogspot.com/](http://linuxenvy.blogspot.com/)

---

### Post by riyasmp on 2011-01-22
[QUOTE=Marc128000;10371934]@riyasmp You can't use hardware acceleration right now. 

thanks for the reply.

Does it mean that the Compiz wouldnt work on ATI?

---

### Post by Yellow Pasque on 2011-01-22
> **riyasmp said:**
> [QUOTE=Marc128000;10371934]@riyasmp You can't use hardware acceleration right now.
Does it mean that the Compiz wouldnt work on ATI?[/QUOTE]

Yes, although newer open-source ATI drivers support 3D acceleration (not as good as proprietary drivers in 3D performance, but still enough to run desktop effects).

---

### Post by riyasmp on 2011-01-22
> **Temüjin said:**
> Yes, although newer open-source ATI drivers support 3D acceleration (not as good as proprietary drivers in 3D performance, but still enough to run desktop effects).

[PHP][/PHP]

sorry is that yes for "it works"? or "doesnt work" tx

---

### Post by Yellow Pasque on 2011-01-22
You can use Catalyst/fglrx and have Compiz, but only on one GPU.
> As of AMD Catalyst&#8482; 10.12, there is no support for switchable graphics chips in Linux. This means you cannot switch between the low power consumption of the integrated graphics chip and the high performance of the discrete graphics chip. Some manufactures allow the IGP to be turned off in the BIOS and use the discrete card only (but this is not good for battery life). Otherwise, you are stuck with both GPU's turned on and draining the battery while only being able to use the IGP. Carefully research before purchasing a laptop, or you may not be able to fully use the hardware you pay for.
[http://wiki.cchtml.com/index.php/Features](http://wiki.cchtml.com/index.php/Features)

In the case of open source drivers, you can get both GPU's working with vga_switcheroo, but you'll need newer drivers (and probably newer kernel) than what's found in Ubuntu 10.10 for 3D to work properly.

---

### Post by riyasmp on 2011-05-18
Hi temujin

I just want bothe cards, i am more than happy to use the open source driver. My laptop just roasts when i use ubuntu and i cant switch off th fan as well.

can you help please

---

### Post by Yellow Pasque on 2011-05-19
Are you still running Ubuntu 10.10 or have you upgraded to 11.04?

---

### Post by riyasmp on 2011-06-05
I have both 11.04 and 10.10 at the moment. issue that i mentioned earlier is simlar on both. i would be happy to fix one of them and erase off the other one.

regards

---

