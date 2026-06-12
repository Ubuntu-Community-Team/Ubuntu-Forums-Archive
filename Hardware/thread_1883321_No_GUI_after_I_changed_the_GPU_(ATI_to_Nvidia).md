---
title: "No GUI after I changed the GPU (ATI to Nvidia)"
date: 2011-11-18
forum: Hardware
---

### Post by The Big Head One on 2011-11-18
Hi guys

I've changed my GPU from an ATI Radeon HD 4770 to a GTX 560 Ti, but now I have no GUI in Ubuntu, only console mode. I found some (really old) topics with people complaining about the same thing and I tried the following steps:

sudo dpkg-reconfigure -phigh xserver-xorg
shutdown -r now

And nothing changed, also, I tried to install a Nvidia driver through the console using:

sudo apt-get install nvidia-current
(Then I restarded)
sudo nvidia-xconfig (Which didn't work)

And still there's no GUI. I don't know if its important, but I think the driver I was using in my ATI was fglrx. Also, I'm using Ubuntu 10.10 64-bit.

What can I do to fix this?

Thank you in advance :)

---

### Post by papibe on 2011-11-18
Could you post the X log? The file is located here:
```
/var/log/Xorg.0.log
```
Paste the content of the file here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post the link so we can take a look.

Regards.

---

### Post by The Big Head One on 2011-11-18
Here it is!
[http://paste.ubuntu.com/742918/](http://paste.ubuntu.com/742918/)

Thank you :)

---

### Post by papibe on 2011-11-18
It looks like Xorg is still trying to use the ATI card.

May be there is is still a reference to the Radeon driver on you Xorg config file. Can we take a look at it? It is this file:
```
/etc/X11/xorg.conf
```
Regards.

---

### Post by The Big Head One on 2011-11-19
Here it is:
[http://paste.ubuntu.com/742977/](http://paste.ubuntu.com/742977/)

:)

---

### Post by papibe on 2011-11-19
```
Driver	"fglrx"
```
Now it makes sense. You are trying to use the ATI driver over your Nvidia card.

I think running:
```
sudo nvidia-xconfig
```
should work, since it creates a new xorg.conf, but since that failed, let's take a safer route.

First delete (actually rename) the Xorg configuration file:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.ATI
```
Then, restart. Now the nouveau driver should kick in (open source Nvidia driver). You should be able to get a GUI and log in into the desktop.

Once inside, open 'Nvidia X Server Settings' as root:
```
gksudo nvidia-settings
```
(nvidia-settings is the actual program name of 'Nvidia X Server...')

Make any adjusted you may need (like resolution). Then select X Server Display Configuration (left). In the right press 'Save to X Configuration File'. Restart your machine.

Now you should be booting into the Nvidia proprietary driver.

I hope this helps, and let us know how it goes.
Regards.

---

### Post by The Big Head One on 2011-11-19
I think I did everything right, after the:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.ATI
```And the restart the GUI came back. Then I opened the:
```
gksudo nvidia-settings
```And I think I saved as you said (I think I clicked on the only save option).

But there was a message saying that I wasn't using the correct driver for my GPU and I went to System -> *Administration* -> [I]Additional Drivers and selected the Nvidia proprietary driver, it was installed and then I restarted. After that the GUI disappeared once again...

I don't know if it would help, but here's how the new xorg.conf is:
[http://paste.ubuntu.com/743336/](http://paste.ubuntu.com/743336/)

And the new Xorg.0.log:
[http://paste.ubuntu.com/743338/](http://paste.ubuntu.com/743338/)

Hope it helps, thank you and I'm sorry if I did something that I shouldn't :(
[/I]

---

### Post by papibe on 2011-11-19
Could you post the results of these commands?
```
lspci | grep -i vga

sudo lshw -C display

lsmod | grep nvidia

apt-cache policy nvidia-current
```
Please paste your results using the # tags (code tags).

Regards.

---

### Post by The Big Head One on 2011-11-19
Results:

lspci | grep -i vga
```
01 :00 .0 VGA compatible controller: nVidia Corporation Device 1200 (rev a1)
```sudo lshw -C display
```
*-display UNCLAIMED
    description: VGA compatible controller
    product: nVidia Corporation
    physical id: 0
    bus info: pci@0000 : 01 : 00 .0
    version: a1
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress vga-controller bus_master cap-list
    configuration: latency=0
    resources: memory: dc000000-fdffffff memory: d8000000-dfffffff memory: d4000000-d7ffffff ioport:b800 (size-128) memory: fe980000-fe9fffff
```lsmod | grep nvidia (no results)

apt-cache policy nvidia-current
```
nvidia-current:
    Installed: 260.19.06-0ubuntu1
    Candidate: 260.19.06-0ubuntu1
    Table of Version:
    *** 260.19.06-0ubuntu1 0
        500 http://br.archive,ubuntu.com/ubuntu maverick/restricted amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by papibe on 2011-11-19
That is very weird to me. The card is being recognized as Nvidia, but there's no detail information about its model. Then, the nvidia module is not being loaded at all.

I would suggest tracking the problem from the very beginning:
[LIST]
[*]Turn off your computer and open it.
[*]Make 100% sure that the card is plugged correctly into the PCI express slot.
[*]Then boot into your BIOS and check that the card is being recognized, and set as the default display.
[*]Try booting into Ubuntu again.
[/LIST]
If that doesn't work, try loading the Nvidia module manually:
```
sudo modprobe nvidia
```
Also, check if there any messages on the system log:
```
dmesg | grep -i nvidia
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by The Big Head One on 2011-11-19
> **papibe said:**
> That is very weird to me. The card is being recognized as Nvidia, but there's no detail information about its model. Then, the nvidia module is not being loaded at all.

I would suggest tracking the problem from the very beginning:
[LIST]
[*]Turn off your computer and open it.
[*]Make 100% sure that the card is plugged correctly into the PCI express slot.
[*]Then boot into your BIOS and check that the card is being recognized, and set as the default display.
[*]Try booting into Ubuntu again.
[/LIST]
If that doesn't work, try loading the Nvidia module manually:
```
sudo modprobe nvidia
```Also, check if there any messages on the system log:
```
dmesg | grep -i nvidia
```Hope it helps, and tell us how it goes.
Regards.
I opened the BIOS, but I didn't know how to check if the GPU was recognized or not, but I think it is, since it's running games perfectly under Windows 7 (I tested some games).

Should I try this:
```
sudo modprobe nvidia
```

or that:
```
dmesg | grep -i nvidia
```

first?

---

### Post by papibe on 2011-11-19
In that order is fine.

---

### Post by The Big Head One on 2011-11-19
Results:

sudo modprobe nvidia
```
FATAL: Module nvidia not found.
```dmesg | grep -i nvidia
```
[        14.279466] hda_intel: Disable MSI for Nvidia chipset
[        14.391672] nvidia: module license 'NVIDIA' taints kernel.
[        16.030408] nvidia 0000:01:00.0 PCI INT A -> GSI 18 (level, low) -> IRQ 18
[        16.030416] nvidia 0000:01:00.0 setting latency timer to 64
[        16.030515] NVRM: The NVIDIA GPU 0000:01:00.0 (PCI ID: 10de:1200) installed
[        16.030516] NVRM: in this system is not supported by the 260.19.06 NVIDIA Linux
[        16.030519] NVRM: Supported NVIDIA GPU Products' in this release's README,
[        16.030521] NVRM: www.nvidia.com.
[        16.030535] nvidia: probe of 0000:01:00.0 failed with error 01
[        16.030550] NVRM: The NVIDIA probe routine failed for 1 device(s).
[        16.030552] NVRM: None of the NVIDIA graphics adapters were initialized!
```

---

### Post by emilywind on 2011-11-19
According to dmesg your card is not supported by the version 260 driver, which is quite an old driver so it is likely that your card is too new. Since you are using 10.10, things like driver versions and such are going to be quite out of date.

To get this working in 10.10 you can either use the following ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get install nvidia-graphics-drivers
```

Or download and install them directly from nvidia. The ppa is probably the best option. Cheers.

---

### Post by papibe on 2011-11-19
> **emilywind said:**
> According to dmesg your card is not supported by the version 260 driver

+1

I would definitively try emilywind's suggestion.

The last resort would to install the driver directly from Nvidia, which it will probably support your card, but it would be harder to keep updates in sync with your Kernel.

Regards.

---

### Post by The Big Head One on 2011-11-19
I added the ppa, but when I tried the code
```
sudo apt-get install nvidia-graphics-drivers
```

I received the message:
```
E: Unable to find the package nvidia-graphics-drivers
```

---

### Post by papibe on 2011-11-19
You have to update before install:
```
sudo apt-get update
```
Regards.

---

### Post by The Big Head One on 2011-11-19
I added the ppa, updated and then tried to install, the same message appeared :(

---

### Post by papibe on 2011-11-19
Since you already have the relevant packages installed (but now older versions compared to the ppa), I think you should try just upgrading:
```
sudo apt-get upgrade
```
After that check that your nvidia driver is newer that the one you had (260.19.06):
```
apt-cache policy nvidia-current
```
If it is newer. Restart, and see if it works.
Regards.

---

### Post by The Big Head One on 2011-11-20
I used the "sudo apt-get upgrade" and now it's working! I checked now on NVIDIA X Server Settings and the driver version is 285.05.09, which is the newest driver according to nvidia's site.

[http://www.nvidia.com/object/linux-display-amd64-285.05.09-driver.html](http://www.nvidia.com/object/linux-display-amd64-285.05.09-driver.html)

Thank you again :)

---

### Post by papibe on 2011-11-20
:D Great! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance, so other people can learn about this.

Regards.

---

