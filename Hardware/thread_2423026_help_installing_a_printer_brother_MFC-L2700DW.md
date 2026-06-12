---
title: "help installing a printer brother MFC-L2700DW"
date: 2019-07-16
forum: Hardware
---

### Post by Germamon on 2019-07-16
I tried downloading and installing following the instructions in this thread and I couldn't.
[https://askubuntu.com/questions/549840/brother-mfc-l2700dw-printer-does-not-work](https://askubuntu.com/questions/549840/brother-mfc-l2700dw-printer-does-not-work)
When I try to install the files that I download, they don't install. It gets stuck in the process and doesn't end the installation.

---

### Post by brian_p on 2019-07-16
You do not need the Brother drivers for printing. Put the device on the network and get a URI for it with the command

```
driverless
```

Then execute the command (without angle brackets)

```
lpadmin -p 2700 -v <the_URI> -E -m everywhere
```

How does that suit you?

---

### Post by Germamon on 2019-07-17
> **brian_p said:**
> You do not need the Brother drivers for printing. Put the device on the network and get a URI for it with the command

```
driverless
```

Then execute the command (without angle brackets)

```
lpadmin -p 2700 -v <the_URI> -E -m everywhere
```

How does that suit you?

this is what i got:
```
ulex@ulex-SATELLITE-L750:~/Downloads$ driverless
driverless: command not found
ulex@ulex-SATELLITE-L750:~/Downloads$ lpadmin -p 2700 -v <the_URI> -E -m everywhere
bash: the_URI: No such file or directory
ulex@ulex-SATELLITE-L750:~/Downloads$ 


```

---

### Post by brian_p on 2019-07-17
> **Germamon said:**
> this is what i got:
[CODE]ulex@ulex-SATELLITE-L750:~/Downloads$ driverless
driverless: command not found

Which version of Ubuntu are you using?

---

### Post by Germamon on 2019-07-17
> **brian_p said:**
> Which version of Ubuntu are you using?


```
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


```

---

### Post by him610 on 2019-07-17
Brother does a good job of supporting Linux on its multifunction devices. I own a Brother MFC-7360N that has always had the drivers installed from the applicable Brother pages. I know of no other way to get your MFC device working. Installation requires some work using the command line.
> When I try to install the files that I download, they don't install Don't give up, just figure you may have done something wrong - keep trying. We all make mistakes. Remember Linux is case sensitive.

[COLOR="#FF0000"]Note[/COLOR]: Before you begin, recommend you assign a static IP address to your MFC device. If you don't know how, refer to your user manual.

Go to this Brother webpage, [https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=mfcl2700dw_us_eu_as&os=128]("https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=mfcl2700dw_us_eu_as&os=128")
Download (click on it) the *Driver Install Tool*. Choose the correct English version. Be sure you read and understand the notes before downloading, and the **How to Install** instructions.
The file you will be downloading is, linux-brprinter-installer-2.2.1-1.gz
In step 6, How to Install Instructions, substitute your model, MFC-L2700DW, for the one in the script.
In step 7, DeviceURI is the static IP address you should have entered as recommended in the Note above.
Follow the prompts, respond as necessary.

Good luck.

---

### Post by Germamon on 2019-07-18
> **Germamon said:**
> ```
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


```

> 
[COLOR=#FF0000]Note[/COLOR]: Before you begin, recommend you assign a static IP address to your MFC device. If you don't know how, refer to your user manual.



I don't know how. Have done a internet research and haven't found anything that suits my undertanding.
thanks

---

### Post by him610 on 2019-07-18
Using your browser, type in the current IP address of your Brother device in browser's address box. It should open up a page similar to the attachment. Click on Network Configuration, when the next page(second attachment) opens click on Configure TCP/IP.
Verify/Set
Enable TCP/IP
IP Address  (Assign an address with your router's range)
Subnet Mask 255.255.255.0
Gateway  (IP Address of your router)
Boot Method Static
Enable APIPA

Submit (click on it)

---

### Post by Germamon on 2019-07-19
> Using your browser, type in the current IP address of your Brother device in browser's address box.

Sorry for being so newbie, but how can I get the printer IP?

The printer is connected via USB.

This is what I get from the terminal:
```
SATELLITE-L750:/home/ulex/Downloads# ifconfig
enp10s0   Link encap:Ethernet  HWaddr 04:7d:7b:09:55:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:22398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1718291 (1.7 MB)  TX bytes:1718291 (1.7 MB)

wlp9s0    Link encap:Ethernet  HWaddr e0:ca:94:8b:11:aa  
          inet addr:192.168.8.145  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::7eb1:face:231a:6655/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:378879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:472707021 (472.7 MB)  TX bytes:22781410 (22.7 MB)


```

---

### Post by him610 on 2019-07-19
> The printer is connected via USB.
None of my printers are all connected using USB. They are both connected via network to several computers.
Regret that I can not help you; you are on your on. Good luck.

---

### Post by kurt18947 on 2019-07-20
Geramon, have you found this page?

[https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=mfcl2700dw_us_eu_as&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=mfcl2700dw_us_eu_as&os=128)

I've had excellent luck using the driver install tool. Download it into an account with SUDO privileges, extract it and run it from a terminal. I also make sure I have the package "system-config-printer". I find this much more useful than what's included than what's installed by default. Some distros do include it by default.

---

### Post by Germamon on 2019-07-20
> **kurt18947 said:**
> Geramon, have you found this page?

[https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=mfcl2700dw_us_eu_as&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=mfcl2700dw_us_eu_as&os=128)

I've had excellent luck using the driver install tool. Download it into an account with SUDO privileges, extract it and run it from a terminal. I also make sure I have the package "system-config-printer". I find this much more useful than what's included than what's installed by default. Some distros do include it by default.

Do u think you could give me more detailed instructions, please?

---

### Post by Germamon on 2019-07-20
This is what I got: ```
root@ulex-SATELLITE-L750:/home/ulex# linux-brprinter-installer-2.2.1-1 MFC-L2700DW
linux-brprinter-installer-2.2.1-1: command not found
root@ulex-SATELLITE-L750:/home/ulex# gunzip linux-brprinter-installer-2.2.1-1.gzgzip: linux-brprinter-installer-2.2.1-1.gz: No such file or directory


```

---

### Post by kurt18947 on 2019-07-20
> **Germamon said:**
> This is what I got: ```
root@ulex-SATELLITE-L750:/home/ulex# linux-brprinter-installer-2.2.1-1 MFC-L2700DW
linux-brprinter-installer-2.2.1-1: command not found
root@ulex-SATELLITE-L750:/home/ulex# gunzip linux-brprinter-installer-2.2.1-1.gzgzip: linux-brprinter-installer-2.2.1-1.gz: No such file or directory


```

You have to do 
```
sudo bash linux-brprinter-installer-2.2.1-1
```

I typically create a Brother folder someplace I can find it again :) then put the extracted file in that folder, change to the Brother folder and run the installer from there. It will download and save the appropriate .deb files and will create uninstall scripts in the Brother folder as well which is why I like to keep all Brother related stuff in one place. The installer will work for any Brother printer that has linux support. You just specify the printer model (I use capital letters, not sure it matters) when prompted by the script. You'll also specify if you're setting up a USB or network connection. If the printer is not found after the installation process, you might launch the printer management app I mentioned earlier and make sure things look right. I'll check this thread again later today to see how you get along.

---

### Post by brian_p on 2019-07-21
> **Germamon said:**
> this is what i got:
```
ulex@ulex-SATELLITE-L750:~/Downloads$ driverless
```
driverless: command not found

I had assumed you were using something less ancient than Ubuntu 16.04.3 LTS. I should not have assumed anything, but asked. This command is not available on that OS.

> ulex@ulex-SATELLITE-L750:~/Downloads$ lpadmin -p 2700 -v <the_URI> -E -m everywhere
bash: the_URI: No such file or directory
ulex@ulex-SATELLITE-L750:~/Downloads$

<the_URI> is a placeholder for the URI you cannot get.

---

### Post by brian_p on 2019-07-21
> **Germamon said:**
> ```
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


```

Is there some overwhelming reason for you to use an outdated OS such as Ubuntu 16.04.3 LTS?

---

### Post by kurt18947 on 2019-07-21
> **brian_p said:**
> Is there some overwhelming reason for you to use an outdated OS such as Ubuntu 16.04.3 LTS?

Ubuntu 16.04 is hardly outdated, being an LTS it's supported until April 2021. Some people like the Unity desktop of 16.04, they don't like the Gnome desktop of 18.04. That would be one reason to stick with 16.04. I'm sure there are others.

---

### Post by brian_p on 2019-07-22
> **Germamon said:**
> This is what I got: ```
root@ulex-SATELLITE-L750:/home/ulex# linux-brprinter-installer-2.2.1-1 MFC-L2700DW
linux-brprinter-installer-2.2.1-1: command not found
```

You will have downloaded the file *linux-brprinter-installer-2.2.1-1.gz.* Complete instructions as to what to do with it are given on the download page. Do Step 4. Then do Step 6 as the superuser. You have omitted the word *bash* in your command.

---

### Post by brian_p on 2019-07-22
> **kurt18947 said:**
> Ubuntu 16.04 is hardly outdated, being an LTS it's supported until April 2021. Some people like the Unity desktop of 16.04, they don't like the Gnome desktop of 18.04. That would be one reason to stick with 16.04. I'm sure there are others.

16.04 is truly a *supported* OS. It's printing system is also outdated compared with 18.04 in a number of ways. The two terms are not mutually exclusive.

---

### Post by kurt18947 on 2019-07-28
> **brian_p said:**
> 16.04 is truly a *supported* OS. It's printing system is also outdated compared with 18.04 in a number of ways. The two terms are not mutually exclusive.

Ah, that may well be. I don't regard the addition of driverless printing as necessarily an advance for me. The Samsung driver prints one line of gibberish per page and will continue to do so until its paper supply is exhausted. The Brother printer works but not as well as the driver from Brother. The scanners on both machines  require drivers from the manufacturers.

---

### Post by brian_p on 2019-07-28
> **kurt18947 said:**
> Ah, that may well be. I don't regard the addition of driverless printing as necessarily an advance for me. The Samsung driver prints one line of gibberish per page and will continue to do so until its paper supply is exhausted. The Brother printer works but not as well as the driver from Brother.

PPDs are going away in upstream CUPS. Driverless printing is the future. Improvements in it can only come about by reporting bugs against CUPS and/or cups-filters.

>  The scanners on both machines  require drivers from the manufacturers.

Indeed they do. But both vendors provide a way to install these seperately from printing packages. So I am not sure what your point is.

---

