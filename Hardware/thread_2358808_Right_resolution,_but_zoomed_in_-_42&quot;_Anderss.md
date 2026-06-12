---
title: "Right resolution, but zoomed in - 42&quot; Andersson TV"
date: 2017-04-17
forum: Hardware
---

### Post by Niklas_Andersson on 2017-04-17
Hi!

Using my old gaming computer as a Media Center on our LCD Andersson 42" TV (A421FD PVR) with Ubuntu 15.04.
The problem is that the display is kind of zoomed in so i don't see the menus and such. The resolution is 1920 x 1080 which the TV supports but it dosn't fit. I know if i go to the display menu on the TV and set Full Mode to 1:1 it fits but the picture flickers as soon as i close it down.
In Windows i could just use the Nvidia Control Panel to adjust the resolution by drag and drop the corners til it fits, But that control panel dosn't exist in Linux. I have tried xrandr but i dont know which resolution i should add ? Maybe i need to install Windows again and look up the resolution. I even tried to change display drivers from x-server to standard Nvidia, but it doesn't matter.

My specs:
OS: Ubuntu 15.04
RAM: 8 GB Samsung  (something ?) (2 x 4 GB)
HDD: 750 GB Seagate Barracuda
MOBO: ASUS M3A78 - T
CPU: AMD Phenom X4 9950 Black Editon 2.4 GHz
GPU: ASUS Nvidia Geforce GTX 650 Ti 

Somebody that know what i should do ?

EDIT: I use HDMI connection

---

### Post by Autodave on 2017-04-17
How is the PC connected to the TV? VGA? If so, you may want to try another cable or switch it over to DVI or HDMI.

Cheap VGA cables don't always have the extra wire that reports the screen resolution to the PC. Or, a good cable could have a broken wire internally.

My own setup refused to work on VGA: tried 3 known good cables. Grabbed an HDMI cable and went right to the proper display size.

---

### Post by Niklas_Andersson on 2017-04-18
Whoops forgot to mention that i use HDMI connection :)

---

### Post by Bucky Ball on 2017-04-18
Note well: 15.04 is long gone. Getting support for it here might be difficult if you run in to further issues. The forums don't officially support EOL releases. Enough to do dealing with supported releases!  

Install a supported release. 15.04 died ages ago. Redundant. Hasn't received updates/upgrades in months (over a year), and that includes security updates, so up to you having that on the net. I wouldn't. ;)

Look under the ['End of Life' releases here]("https://wiki.ubuntu.com/Releases"). If you don't want to be installing every six months (and it doesn't sound like you do) install an LTS release, 16.04 LTS for instance. LTS has five years support for Ubuntu. Everything else has nine months. LTS releases can also be upgraded directly to the next LTS (18.04 LTS), leapfrogging the interim releases in between. Neat.

(PS: you can use the NVidia controls to set resolution in Ubuntu, too. If you have it installed. If you have the correct driver installed for the card (from Additional Drivers), then that will be in your menus too.)

---

### Post by Autodave on 2017-04-18
Where did you get the Nvidia driver that you are currently using?

---

### Post by Niklas_Andersson on 2017-04-18
[IMG]http://i.imgur.com/TnZrxd0.png[/IMG]

In Software and Updates -> Additional Drivers :)

---

### Post by Bucky Ball on 2017-04-18
Don't think that's the right driver for your card. Try one of the 340.96 ones. Try the first one 'updates' first. 

The NVidia site recommends that one for your card. [See here]("http://www.nvidia.com/download/driverResults.aspx/77525/en-us").

---

### Post by Niklas_Andersson on 2017-04-18
> **Bucky Ball said:**
> Don't think that's the right driver for your card. Try one of the 340.96 ones. Try the first one 'updates' first. 

The NVidia site recommends that one for your card. [See here]("http://www.nvidia.com/download/driverResults.aspx/77525/en-us").
Well cant install the driver from the Nvidia Website beacuse i cant get lightdm and x server to stop so i ended up getting the 340.96 instead. But nothing changed, still same problem. And i also got an option to upgrade to Ubuntu 16 LTS version, which dont understand what it got to do with this problem ? But anyway if i want proper support as you said, then i upgrade.

---

