---
title: "touchpad has no double-finger scrolling"
date: 2015-01-12
forum: Hardware
---

### Post by eli_fabrikant on 2015-01-12
hi everyone,

I was searching online for quite  a while but couldn't find any answer that I could understand and use.

 I have a new lenovo z50 with ubuntu 14.04 freshly installed. Ican|t seem to find an option of scrolling with two fingers on the GUI interface 'mouse and touchpad'.

 I'm really bad with the terminal, so if I need to do something without a graphical interface, please explain as simple as you can :)

 I REALLY apreciate your help in advance, thanks!
eli

---

### Post by zombifier25 on 2015-01-12
You can't see it at all?

[img]https://i.imgur.com/Z2ioUhp.png[/img]


It might be a problem with your touchpad not being detected as a touchpad. Post the output of the following command here:

```
cat /proc/bus/input/devices
```

Open the terminal, run it and copy and paste the output here using the right mouse menu (Ctrl+C does not work in the terminal if you are not aware)

---

### Post by eli_fabrikant on 2015-01-13
Hi Zombifier25, 
thanks for your reply. i did what you suggested, and here is the output:


eli@eli-Lenovo-Z50-70:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Elantech Touchpad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Ideapad extra buttons"
P: Phys=ideapad/input0
S: Sysfs=/devices/platform/VPC2004:00/input/input6
U: Uniq=
H: Handlers=rfkill kbd event5 
B: PROP=0
B: EV=13
B: KEY=1400800100c03 400000000300000 0 0
B: MSC=10

I: Bus=0003 Vendor=174f Product=14b2 Version=1127
N: Name="Lenovo EasyCamera"
P: Phys=usb-0000:00:14.0-6/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb2/2-6/2-6:1.0/input/input7
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input11
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input14
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input13
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input12
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=140



What's next ?

Thanks so much,
e

---

### Post by zombifier25 on 2015-01-13
It seems that other people around the Internet also have problems with Elantech touchpad, and it will require some manual fixing. Blame the touchpad company.
The next few steps will require some more terminal commands.

1. First, download this file: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+attachment/3941591/+files/psmouse-elantech-x551c.tar.gz](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+attachment/3941591/+files/psmouse-elantech-x551c.tar.gz)
Put it in your Downloads folder in your home for convenience.

2. Copy and paste these commands one at a time into the terminal (provide your password when prompted):
```
cd ~/Downloads
sudo dkms ldtarball psmouse-elantech-x551c.tar.gz
sudo dkms install -m psmouse -v elantech-x551c
sudo rmmod psmouse
sudo modprobe psmouse

```
I have not tried this since I don't have the touchpad, but the website warns that the pointer will probably disappear, in which case carry on and type the commands.
Once done, check if the option is back. Other people have tried this and it works for them.

Source: [http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/](http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/)

---

### Post by eli_fabrikant on 2015-01-14
Zombifier25, you are the best!!!!
 thank you so much! it worked perfectly :)

---

### Post by Pilot6 on 2015-01-14
I would not suggest installing that dkms elantech driver, since it is a dirty hack to install psmouse as a dkms package.
Elantech touchpads are supported by offical Ubuntu kernels starting with 3.16.

---

### Post by zombifier25 on 2015-01-14
> **Pilot6 said:**
> I would not suggest installing that dkms elantech driver, since it is a dirty hack to install psmouse as a dkms package.
Elantech touchpads are supported by offical Ubuntu kernels starting with 3.16.

14.10 uses 3.16, while 14.04 uses 3.13. I don't know if 14.04 (the version OP uses) plans to upgrade to the newer kernel, but for now since I would not recommend a beginner to manually install a new kernel, that dirty hack is the only way.

---

### Post by Pilot6 on 2015-01-14
14.04.2 will use 3.16. Now it can be installed by

sudo apt-get install linux-generic-lts-utopic

But the dkms staff should be completely removed first.

---

### Post by eli_fabrikant on 2015-01-14
OK, guys, slower please :) I restarted my computer and the problem occurred again, so I would like to try the other option.

How can I uninstall the 'dkms' stuff ?

---

### Post by zombifier25 on 2015-01-14
```

sudo dkms remove psmouse/elantech-x551c --all

```

Then install the new kernel:
```
 sudo apt-get install linux-generic-lts-utopic

```

Then reboot the machine. This is a better, much more permanent solution, while the solution I originally gave you was back when the new kernel wasn't released.

---

### Post by eli_fabrikant on 2015-01-19
Great! Thanks again!

---

