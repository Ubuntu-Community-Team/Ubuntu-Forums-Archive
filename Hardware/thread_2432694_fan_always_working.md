---
title: "fan always working"
date: 2019-12-06
forum: Hardware
---

### Post by idnael on 2019-12-06
I updated my Ubuntu to 19.10. Since then, every 40 seconds the fan starts working for 5 seconds and stops. This happens after I start a X session, even if I have no application started. Doesn't happen if I only login in the console.

I use Cinnamon. The top command shows the cinnamon process is using around 3% of CPU. Sometimes goes to 10% of the CPU. But doesn't seem to be related with the fan.

The sensors command shows that the temperature is always rising above 50°C immediatly before the fan starts working:

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +53.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +49.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +49.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +49.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +49.0°C  (high = +100.0°C, crit = +100.0°C)

Since then, I tried other window managers. The problem persists, but with different times. The given values are average, and not very precise, but the fan always starting working at regular intervals:
xfce: 90 seconds
Gnome and Unity: 180 seconds

I also tried a live usb installation to boot in Ubuntu 18.04, similar to what I had before the update. The fan problem didn't happen, and the sensors command shows that the temperatures never rises above 40°C.

This is very annoying because I always expect the computer to be quiet when it is not doing any intensive processing. Please tell if you need any more information to help diagnose and solve this problem.

---

### Post by Autodave on 2019-12-06
Some info on your system would probably be helpful.

Upgrading often causes odd problems like this.  Unless you need the newest and greatest release because you have newer hardware that isn't supported by the last long term release (LTS), it is always best to stay with the LTS releases.  18.04 was the last one, 20.04 will be the next.

---

### Post by mörgæs on 2019-12-07
Ubuntu 18.04 was heavyweight but 19.10 added many extra pounds. If it's getting too much for the hardware you could try a live boot of, say Xubuntu 19.10.

---

### Post by idnael on 2019-12-07
Please say if you need something more specific.

It is a CLEVO-N151ZU laptop.
```

$ hwinfo --short
cpu:                                                            
                       Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz, 3222 MHz
                       Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz, 3288 MHz
                       Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz, 3375 MHz
                       Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz, 3133 MHz
                       Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz, 3245 MHz
                       Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz, 3156 MHz
                       Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz, 3207 MHz
                       Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz, 3260 MHz
keyboard:
  /dev/input/event4    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      MSFT0001:01 06CB:CD64 Touchpad
monitor:
                       N156HCE-EN1 LCD Monitor
graphics card:
                       Intel UHD Graphics 620 (Whiskey Lake)
sound:
                       Intel Cannon Point-LP High Definition Audio Controller
storage:
                       Intel Cannon Point-LP SATA Controller [AHCI Mode]
network:
  wlp3s0               Intel Wireless-AC 9260
  enp2s0f1             Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
network interface:
  anbox0               Ethernet network interface
  wlp3s0               Ethernet network interface
  lo                   Loopback network interface
  enp2s0f1             Ethernet network interface
disk:
  /dev/sda             CT500MX500SSD4
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
usb controller:
                       Intel Cannon Point-LP USB 3.1 xHCI Controller
bios:
                       BIOS
bridge:
                       Intel Cannon Point-LP PCI Express Root Port #5
                       Intel Cannon Point-LP LPC Controller
                       Intel PCI bridge
                       Intel Host bridge
                       Intel Cannon Point-LP PCI Express Root Port #9
hub:
                       Linux Foundation 2.0 root hub
                       Linux Foundation 3.0 root hub
memory:
                       Main Memory
bluetooth:
                       Intel Bluetooth Device
unknown:
                       FPU
                       DMA controller
                       PIC
                       Keyboard controller
                       Realtek RTL8411B PCI Express Card Reader
                       Intel Cannon Point-LP MEI Controller #1
                       Intel Cannon Point-LP SPI Controller
                       Intel Cannon Point-LP Thermal Controller
                       Intel Cannon Point-LP Serial IO I2C Controller #0
                       Intel Cannon Point-LP Shared SRAM
                       Intel Cannon Point-LP SMBus Controller
                       Synaptics Unclassified device
  /dev/input/event7    Chicony Electronics Chicony USB2.0 Camera


```

---

### Post by mörgæs on 2019-12-07
Your hardware is certainly strong enough.

> **idnael said:**
> 
xfce: 90 seconds


Does this mean that you have added XFCE to an Ubuntu installation or did you install Xubuntu from scratch?

---

### Post by idnael on 2019-12-07
I installed the xfce packages, and also gnome3 to the existing Ubuntu installation.

It is difficult to find a rule about what happens. This afternoon I was using Cinnamon and the fan was working every 25 seconds. Then I switched to xfce. It was still happening but with larger intervals. Some hours later, the fan didn't work for several minutes, which can almost be considered normal. Then I switched again to Cinnamon. The fan was working now with interval of 68 seconds. Maybe the difference is because it is night and the environment is a bit colder. That makes me think that now it is winter here, I have no idea how this will work in the summer!

I also tried a live Ubuntu 19.10 installation, and didn't have the fan problem. But I only tested Unity. Couldn't run Cinnamon with the live ubuntu installation. Unity seems to be better with the fan (but I prefer classic style window manager as Cinnamon or xfce).

---

### Post by CatKiller on 2019-12-08
> **idnael said:**
> It is difficult to find a rule about what happens. 

It really isn't. 

> **idnael said:**
> The sensors command shows that **the temperature is always rising above 50°C** immediatly before the fan starts working:

Your fan is controlled by your BIOS. You can generally change the profile of when it comes on there. Otherwise, you can use fancontrol to create your own profile. You'll also likely find it useful to clear the dust out of your vents.

---

### Post by idnael on 2019-12-09
I did not find any fan related settings in the BIOS. And I don't want (yet?) to experiment with linux fancontrol because it seems the problem is not there.

I made this test:
I run a live usb pen with Xubuntu 18.04, that uses Xfce. There was no problem with the fan. The temperature was always below 40ºC. Once I ran a heavy program and the temperature went up above 50ºC, and the fan started working for a few seconds, and after the temperature went again stable around 40ºC. This means, the fan is operating exactly the same way, but after the update to 19.10 some process is making the temperature going to high and that is making the fan to be always working. Or maybe the sensors readings are wrong.

So what I could do next? I think I will have to make a new installation.
I don't want LTS because I like newer versions of several programs. So I could try a flesh install of Ubuntu 19.10. And if the fan problem continues, I can go to the LTS.

---

### Post by mörgæs on 2019-12-09
> **idnael said:**
> So I could try a flesh install of Ubuntu 19.10. And if the fan problem continues, I can go to the LTS.

I suggest a fresh install of a lighter Buntu like X/Lubuntu in version 19.10. Though it's clearly possible to run the heavy Ubuntu one of the light alternatives might be better at keeping the temperature below 50°.

---

### Post by #&amp;thj^% on 2019-12-09
> **idnael said:**
> I did not find any fan related settings in the BIOS. And I don't want (yet?) to experiment with linux fancontrol because it seems the problem is not there.



I installed the fan control on a friends Clevo laptop works well give it a go..
Fan control on Linux:

If you need fan control on Linux for supported Clevo based systems, install Tuxedo's fan control software here: [https://github.com/tuxedocomputers/tuxedo-fan-control/blob/master/docs/dev/dev_manual.md#building](https://github.com/tuxedocomputers/tuxedo-fan-control/blob/master/docs/dev/dev_manual.md#building)
```
sudo apt install curl
```

The curl package is most likely installed by default.
```
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
```
Next:
```
sudo apt install nodejs autoconf automake build-essential gcc g++ make rpm
```
Fetch the sources and build the software:

```
mkdir -p ~/project && cd ~/project
git clone https://github.com/tuxedocomputers/tuxedo-fan-control
cd tuxedo-fan-control
npm install && npm run build && npm run pack

```
Then install the package:

```
sudo dpkg -i output/build/*.deb
```

You can also use gdebi, provided by gdebi-core:

```
sudo apt install gdebi-core`
sudo gdebi output/build/*.deb
```

When done installing the software, create a systemd unit file for it:

```
sudoedit /etc/systemd/system/tuxedofancontrol.service

```
With the content:

```
[Unit]
Description=TUXEDO Fan Control

[Service]
Type=forking
ExecStart=/bin/bash -c "Xvfb :99 & export DISPLAY=:99 && <path>/tuxedofancontrol --novendorcheck --startdaemon"
ExecStop=/bin/bash -c "Xvfb :99 & export DISPLAY=:99 && <path>/tuxedofancontrol --novendorcheck --stopdaemon"
ExecReload=/bin/bash -c "Xvfb :99 & export DISPLAY=:99 && <path>/tuxedofancontrol --novendorcheck --restartdaemon"

Restart=always

[Install]
WantedBy=multi-user.target
```

Note that the path above can vary, based on the package you installed. Be it a snap package or the executable, self contained AppImage binary.

Then enable and start the service:

```
systemctl enable tuxedofancontrol && systemctl start tuxedofancontrol
```

Now when you start the binary (from wherever it was installed), you should see the fan duty status, etc. **_Warning: Do not use the systemd options from the GUI_**. The unit files created by that package point to the wrong path of the binary. This is a bug.
I have personally seen this software work good on 18.04 LTS...Enjoy

---

### Post by idnael on 2019-12-13
I did a flesh install of Ubuntu LTS 18.04 and installed all updates. I think the fan is still working too much compared as it was before.

I saw the tuxedocomputers source you posted, 1fallen, but did not tried it yet. You installed it in your friend's clevo because the original fancontrol was not well?
In my case, what difference can it make? I should configure it so the fan starts working only at 60°C? Now the fan starts at 50°C. They say it can destroy the cpu if misconfigured.

---

### Post by idnael on 2020-01-27
I found the problem started when switched from kernel 5.0.0-32 to kernel 5.3.0-26. 

If I boot with the older kernel, everything runs fine.

---

### Post by him610 on 2020-01-28
> Package id 0: +53.0°C (high = +100.0°C, crit = +100.0°C)
Core 0: +49.0°C (high = +100.0°C, crit = +100.0°C)....
What is the advantage of having both high and critical temps set to same value, +100.0°C? 
I would have thought it would be better to have high temp 15 to 20 °C less than critical, +100.0°C.
Maybe someone can explain it.

---

### Post by mörgæs on 2020-01-29
How does the kernel in 20.04 work?
 
You can try a live boot without installing.

---

### Post by idnael on 2020-02-02
20.04? If you mean Ubuntu 19.04, it worked fine. The problem started later.

I also tried a Live boot. The latest Ubuntu release, 19.10, comes with kernel 5.0.0 so it  works fine. Only after installation and the first update, it goes to kernel 5.3.0 which has the problem. 

I found later kernels also have the problem. I will try other kernel versions to find on which release, between 5.0.0 and 5.3.0 the problem started.

---

### Post by mörgæs on 2020-02-03
No, I meant the [daily build]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/") of 20.04. 

The question about when the error appeared comes second. What comes first is whether or not it's already fixed in 20.04.

---

### Post by idnael on 2020-02-05
Ok, I did a live boot with the daily build from 4 february.  It uses kernel 5.4.0-12. I just opened a terminal and the temperature was always at 48ºC, so very bad.

The good news is that I tried the latest kernel in my current installation, kernel 5.5.2-050502-generic (installed with Ukuu) and it seems good! I'm using this kernel now. 

It looks that the problem has been solved!! I will continue testing for some days...

---

### Post by mörgæs on 2020-02-05
Good, please keep us posted.

---

### Post by idnael on 2020-03-05
I'm using kernel 5.5.4 now, and it is fine. There are some problems, like Virtualbox can't run. But the problem with the fan is over. I think I will have to wait a lot of time until the oficial kernel in Ubuntu catchs up.

---

