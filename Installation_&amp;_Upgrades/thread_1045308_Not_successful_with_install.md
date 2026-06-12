---
title: "Not successful with install"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by crenshawdesignz on 2009-01-20
Greetings,

Newbie, CrenshawDesignz. I have installed the OS 10 times with the same results. Here is a more specific acccount of what happens.

The installation proceeds quite normally. My connection at home is via Cable Modem and I therefore assume that the connection is dynamic. I enter the standard 255.255.255.0 and my default gateway and initially did enter the IP that was stored in my laptop. By the way, I am installing the latest Ubuntu release onto a Dell Model GX280 machine.

After 2 (plus) hours the machine is ready for me to login. I am always successful up to that point. After that, even hours later the screen remains blank. This remains true even after I spent money on ethernet cables so I have a direct connection vs my initial card (netgear) and the newly installed D-Link card. As  you can see I am well invested in this and am determined not to give up.

Someone told me that the reason is because the install is not complete. I was told the install requires an Internet connection. Is this true? Today I am at work on a similar machine and if there is anything I can do to make the connection at home work, I would love to know.

---

### Post by meindian523 on 2009-01-20
More details:
Are you installing Ubuntu inside Windows?Have you downloaded a CD image(approx 700MB) or an installer?Did you use a CD to install?

---

### Post by crenshawdesignz on 2009-01-20
> **meindian523 said:**
> More details:
Are you installing Ubuntu inside Windows?Have you downloaded a CD image(approx 700MB) or an installer?Did you use a CD to install?
No. I went headlong into Linux. Actually, I got confused on how to setup the dual boot which was my intention. Here at work I am running from the DVD but at home I want to full LINUX experience.

Thanks for your response.

---

### Post by Pumalite on 2009-01-20
If using Vista you have to allocate space for Ubuntu with Vista partitioner first.

---

### Post by Jm_muirhead on 2009-01-20
When you are loading Linux, you should grab about 40 or 50gb of free  hard drive space using the partition software, gparted (part of the install process)This will set Linux up in it's own partitions sda1,swap,dev. 
Once installed, GRUB the boot loader will automatically give you the option to run WinDoZe or Linux. Linux should detect your internet connection when loading,and automatic update Icon will appear in the tool bar, click on this to receive all the latest updates for your system.;)

My machine is about 6 years old and only took 20 mins to install Ubuntu 8.10

---

### Post by crenshawdesignz on 2009-01-20
> **Jm_muirhead said:**
> When you are loading Linux, you should grab about 40 or 50gb of free  hard drive space using the partition software, gparted (part of the install process)This will set Linux up in it's own partitions sda1,swap,dev. 
Once installed, GRUB the boot loader will automatically give you the option to run WinDoZe or Linux. Linux should detect your internet connection when loading,and automatic update Icon will appear in the tool bar, click on this to receive all the latest updates for your system.;)

My machine is about 6 years old and only took 20 mins to install Ubuntu 8.10

Thanks for the feedback. I wonder if my install took longer because the machine could not connect to the internet? Thanks for all of the help.

---

### Post by crenshawdesignz on 2009-01-20
> **Jm_muirhead said:**
> When you are loading Linux, you should grab about 40 or 50gb of free  hard drive space using the partition software, gparted (part of the install process)This will set Linux up in it's own partitions sda1,swap,dev. 
Once installed, GRUB the boot loader will automatically give you the option to run WinDoZe or Linux. Linux should detect your internet connection when loading,and automatic update Icon will appear in the tool bar, click on this to receive all the latest updates for your system.;)

My machine is about 6 years old and only took 20 mins to install Ubuntu 8.10

I may have to reinstall WinDoze and begin again. Lot more work but I am convinced by the process I am using here at work that Linux is going to be worth the effort. Thanks.

---

### Post by Pumalite on 2009-01-20
Wire yourself to the Internet through a router providing you DHCP and a dynamic IP

---

### Post by chicenwing on 2009-01-21
> **Pumalite said:**
> Wire yourself to the Internet through a router providing you DHCP and a dynamic IP

You know, I did notice that when my computer starts up and shows the devices it (sees) the one failure is cannot connect router. I will have to get some help with this but I am going to do that.

Is there a place in the app to set the router settings?

---

### Post by caljohnsmith on 2009-01-21
> **crenshawdesignz said:**
> My connection at home is via Cable Modem and I therefore assume that the connection is dynamic. I enter the standard 255.255.255.0 and my default gateway and initially did enter the IP that was stored in my laptop. 
I just wanted to mention that using "255.255.255.0" for your gateway will cause problems, because that should be the netmask, not the gateway. Your gateway will be something like 192.168.0.1, 192.168.1.1, 192.168.1.254, etc. assuming you are using the 192.168.x.x subnet. You might be using a 10.x.x.x subnet or something like that though. The easiest way I think is to just use the Network Manager applet on your top panel to connect via DHCP as Pumalite all ready mentioned. How about trying that and let us know how it goes.

---

### Post by brahamoney on 2009-01-21
Hi,

I'm tryin to have multi boot on my on my system by the way i am trying to install ubuntu on a Compaq Presario V3631TU notebook to no avail...when i get to the partition manager..i have two options to either us eht entire disk or manual partition....

after i select the manual partition i go ahead and after selecting the partition i want to install ubuntu on i get the message.."No root file system is defined. Please correct this from the Partition Menu"...

I keep going back but i still end up with the same problem....someone please help...i don't wanna run the entire comp on Ubuntu...so what do i do?

---

### Post by meindian523 on 2009-01-21
brahamoney
Please create a new thread.

---

### Post by crenshawdesignz on 2009-01-22
> **caljohnsmith said:**
> I just wanted to mention that using "255.255.255.0" for your gateway will cause problems, because that should be the netmask, not the gateway. Your gateway will be something like 192.168.0.1, 192.168.1.1, 192.168.1.254, etc. assuming you are using the 192.168.x.x subnet. You might be using a 10.x.x.x subnet or something like that though. The easiest way I think is to just use the Network Manager applet on your top panel to connect via DHCP as Pumalite all ready mentioned. How about trying that and let us know how it goes.

You know, that is what I am doing wrong. I have been using 255.255.255.0. You know now how green I am.

---

