---
title: "Slow/Poor performance after normal boot and after sleep"
date: 2018-03-04
forum: Hardware
---

### Post by robertojf2012 on 2018-03-04
Hello guys, I'm pretty new here. I have installed Ubuntu 16.04 LTS 64-bit edition... 
My computer is a Toshiba Satellite C855-S5108, this are my current specs:

```
System:    Host: robert-Satellite-C855 Kernel: 4.13.0-36-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.5 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Ubuntu 16.04 xenial
Machine:   System: TOSHIBA (portable) product: Satellite C855 v: PSCBLU-02M004
           Mobo: TOSHIBA model: Portable PC v: MP
           Bios: Insyde v: 6.70 date: 04/15/2013
CPU:       Dual core Intel Core i3-3120M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9977
           clock speeds: max: 2500 MHz 1: 2494 MHz 2: 2494 MHz 3: 2494 MHz
           4: 2494 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile
           GLX Version: 3.0 Mesa 17.2.8 Direct Rendering: Yes
Audio:     Card Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-36-generic
Network:   Card-1: Qualcomm Atheros AR8162 Fast Ethernet
           driver: alx port: 3000 bus-ID: 01:00.0
           IF: enp1s0 state: down mac: <filter>
           Card-2: Realtek RTL8188CE 802.11b/g/n WiFi Adapter
           driver: rtl8192ce port: 2000 bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (6.2% used)
           ID-1: /dev/sda model: Hitachi_HTS54505 size: 500.1GB
Partition: ID-1: / size: 28G used: 5.0G (20%) fs: ext4 dev: /dev/sda2
           ID-2: /boot size: 641M used: 69M (12%) fs: ext4 dev: /dev/sda1
           ID-3: /home size: 429G used: 22G (6%) fs: ext4 dev: /dev/sda4
           ID-4: swap-1 size: 2.05GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 56.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 225 Uptime: 1:28 Memory: 1278.8/3832.3MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35
```

The problem that I'm experiencing is that... after a normal boot, or  a normal 'turn on' of my PC, When I start using it, the performance is  bad, I experience sluggish everywhere, even switching tabs in Firefox is  slow. Basically the system runs very slow and laggy, despite I  have nice specs.
What I always need to do is to make a restart to fix this  problem, After a restart everything is fast and fluid,(as it should), 
Also when I put to sleep my PC, and then I  start using it again the performance problem starts again.
When I first noticed this problem I was running Linux Mint 18 xfce, but in Ubuntu happens too.
What could be the cause of this?, I have been looking for a solution without success, I do not know if it is related to the CPU or drivers..

Thank you for your time, I hope you guys can help me solve this.

---

### Post by tinylagarto on 2018-03-05
Maybe the Unity desktop is too heavy on your RAM. I see you have 4. It is enough usually but if you have tons of tabs open and a lot of other applications the system can be sluggish and you will also end up using the swap partition that slows down the system. 

Others might step in with other ideas but you could try a lighter desktop or another spin of Ubuntu. Personally I use the Xfce desktop though you tried it in Linux Mint and experienced similar problems.
In my opinion your hardware looks fine. 

Maybe something is running in the background.
You could open top from the terminal and see what is running and if it uses too much RAM or CPU. Or take a look into the system monitor and report back.

---

### Post by robertojf2012 on 2018-03-05
Hi ivanovnegro2, I have just checked the processes, but I do not see anything wrong. Except I have just notice that after sleep one of my CPUs is working a lot and the others are basically doing nothing. and when I fix that,all the cores are working all parallel.
Also I have noticed that when I simple Log Out and then I Log In again, the problem seems fixed. But I still do not understand why it happens. I do not want to log In and then Log Out everytime. it is quite annoying.
I have just take some screen shots to show everyone how the CPUs behave.

[B]This first 2 Images show the behave when I have just wake up my PC from sleep:
[https://ibb.co/ntw2tS](https://ibb.co/ntw2tS)
[IMG]https://ibb.co/ntw2tS[/IMG]
[https://ibb.co/dvpSSn](https://ibb.co/dvpSSn)
[IMG]https://ibb.co/dvpSSn[/IMG]

And this image show the behave when I Log Out and then I Login Again..
[https://ibb.co/gVBD07](https://ibb.co/gVBD07)
[IMG]https://ibb.co/gVBD07[/IMG]


((Just to tell you.. those screen shots were taken when I had nothing opened. just the system monitor))
[/B]

---

### Post by kerry_s on 2018-03-05
install unity tweak & disable the animations
everything should be much faster after that, unity never seemed to play nice with intel gpu's

all the other *ubuntu varients don't have issues.

in xfce, it's the compositor, simply disabling all the fancy stuff or the whole thing.
i like zooming in plank so i leave it on.
[ATTACH=CONFIG]278814[/ATTACH]

---

### Post by robertojf2012 on 2018-03-06
Hey, I have disabled some animations but the problem persists. As I said I can run Ubuntu normally when I simply log out and then I log in again. or I make a simple restart.

---

### Post by kerry_s on 2018-03-06
some animations? they all got to go & that blur background to.

i just installed a new system, so i don't have 16 in a vm to tell you exactly what to do.
i have an appointment so, i'll grab ubuntu 16 when i get back. just hang in there.

---

### Post by kerry_s on 2018-03-06
here's the settings i change to get it up to speed on my intel gpu.
[ATTACH=CONFIG]278825[/ATTACH][ATTACH=CONFIG]278826[/ATTACH][ATTACH=CONFIG]278827[/ATTACH]

---

### Post by monkeybrain20122 on 2018-03-06
> **robertojf2012 said:**
>  As I said I can run Ubuntu normally when I simply log out and then I log in again. or I make a simple restart.

4 Gs of ram are plenty. No way that unity or animations are "too heavy" for that. It is a myth that you need some super computer to run unity smoothly. Your problem lies elsewhere if the problem happens just when you wake from sleep or fresh boot and not at other times (one would think that if the desktop is too heavy then it would be too heavy regardless how you start your session, no?)

Check this out, maybe it'll help. [https://askubuntu.com/questions/792605/ubuntu-16-04-lts-too-slow-after-suspend-and-resume](https://askubuntu.com/questions/792605/ubuntu-16-04-lts-too-slow-after-suspend-and-resume)

---

### Post by kerry_s on 2018-03-06
it's the intel gpu drivers in that version, there just not as good.

for example: 
for me it can't properly identify the screen resolution of 1366x768, so it runs at 1280x720, which is fine it still works.
the animations, transparency, effects all combine to drag the gpu down, makes it stutter & lag, sometimes it looks like slow mo

---

### Post by robertojf2012 on 2018-03-06
Hey [**[COLOR=#000000]monkeybrain20122[/COLOR]**]("https://ubuntuforums.org/member.php?u=1843403"), Exactly, I can run Unity pretty well, I don't need to deactivate all of that because my PC can handle everything by default. My performance problem only happens after sleep and on fresh boot. Let me check that link. And I will response as soon as possible.Thank you.

---

### Post by monkeybrain20122 on 2018-03-06
> **kerry_s said:**
> it's the intel gpu drivers in that version, there just not as good.


I have had plenty of moderately spec intel machines (all second hand), run unity just fine with all the eye candies. If the default intel driver is too old (as often is the case with LTS) or too buggy maybe you should consider upgrading mesa? [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)

---

### Post by kerry_s on 2018-03-06
i'm not worried about it. i'm not using unity.
just sharing my knowledge, my current intel also does not have those issues. that was on a prior machine, which i've long got rid of.

---

### Post by tinylagarto on 2018-03-07
What about Intel Microcode? On one machine it fixed some Kodi crashes for me. 
OP could look into it.

---

### Post by robertojf2012 on 2018-03-08
Hello monkeybrain20122, I still have the problem, I tried to fix it with the link you gave me, but no success. A friend told me to downgrade my kernel to the version 4.4.116-0404116-generic
So I did it. And I see that the problem was reduced. On fresh boot the CPU works less, but still see high spikes. and also I noticed that the core that seems doing too much is another. 
But after suspend the problem persists.
What I also did was to disable intel_pstate. from the grub file. I followed this instructions: [https://askubuntu.com/questions/591594/enable-full-performance-on-sandy-bridge-laptop](https://askubuntu.com/questions/591594/enable-full-performance-on-sandy-bridge-laptop)
But nothing seems to change..
Any ideas? thank you.

---

### Post by robertojf2012 on 2018-03-08
> **monkeybrain20122 said:**
> I have had plenty of moderately spec intel machines (all second hand), run unity just fine with all the eye candies. If the default intel driver is too old (as often is the case with LTS) or too buggy maybe you should consider upgrading mesa? [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)

Let me try that. thank you!

---

### Post by monkeybrain20122 on 2018-03-08
If it is a kernel problem may be you can try other kernels. [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Find one say V4.1.14.24

create a folder say ker in Downloads
```
cd Downloads && mkdir ker
```

Then download the kernel packages into ~/Downloads/ker
There are three you need

linux-headers all.deb
linux-headers generic amd64.deb
linux image generic amd64.deb

I assume you have Ubuntu 64 bit. otherwise go to the i386 group and download the counterparts of those packages above

When download completes, start terminal and type
```
cd ~/Downloads/ker
sudo dpkg -i *.deb
```

When finishes, reboot.

---

### Post by robertojf2012 on 2018-03-08
> **monkeybrain20122 said:**
> If it is a kernel problem may be you can try other kernels. [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Find one say V4.1.14.24

create a folder say ker in Downloads
```
cd Downloads && mkdir ker
```

Then download the kernel packages into ~/Downloads/ker
There are three you need

linux-headers all.deb
linux-headers generic amd64.deb
linux image generic amd64.deb

I assume you have Ubuntu 64 bit. otherwise go to the i386 group and download the counterparts of those packages above

When download completes, start terminal and type
```
cd ~/Downloads/ker
sudo dpkg -i *.deb
```

When finishes, reboot.

Yesterday I installed this program:** Ukuu kernel update utility** to change the kernel, in safe way I think. because I do not want to mess things up. that's how I changed the kernel previously. Let me try that version. What version do you think it will work better for my PC?
greetings

---

### Post by monkeybrain20122 on 2018-03-08
Updating kernel is always fairly safe, if it doesn't work, usually you can fix it by just booting into an older kernel and from which uninstall the kernel packages you just installed (keep pressing esc or shift depending on the machine  when boot to see the menu where you can choose the kernel)

I don't know which kernel to recommend since it is just a guess. Probably the 4.13.x or 4.14.x

---

### Post by robertojf2012 on 2018-03-08
> **monkeybrain20122 said:**
> Updating kernel is always fairly safe, if it doesn't work, usually you can fix it by just booting into an older kernel and from which uninstall the kernel packages you just installed (keep pressing esc or shift depending on the machine  when boot to see the menu where you can choose the kernel)

I don't know which kernel to recommend since it is just a guess. Probably the 4.13.x or 4.14.x

Ok I have just installed this kernel version: [I][B]4.1.14-040114-generic
[/B][/I]And also I changed to the MESA drivers: [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)
I need to keep using my PC and see how it goes, I will reply as soon as possible.
Thank you Again.

---

### Post by robertojf2012 on 2018-03-10
And seems fixed. I have done multiple fresh boots and the CPU usage is quite normal, no more sluggish after fresh boot. After sleep the system works good now and no sluggish either.
The doubt that I have now, is what exactly improved my system.
This is what I have done...
I downgrade my kernel to version: ***4.1.14-040114-generic***
I installed the Mesa Graphics. from here [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa)
I disabled intel_pstate from the grub file. (intel_pstate=disable)

I'm gonna make some tests and see what of all this things actually fixed this problem.

One detail I'm noticing now is that with simply moving the mouse, the CPU goes up to 60% usage of one of my cores. I do not know if this is normal. But I think this is not related to this problem.

Thank you very much everyone to help me with this! :D I really appreciate.

This are my specs right now:
```

System:    Host: robert-Satellite-C855 Kernel: 4.1.14-040114-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Unity 7.4.5 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Ubuntu 16.04 xenial
Machine:   System: TOSHIBA (portable) product: Satellite C855 v: PSCBLU-02M004
           Mobo: TOSHIBA model: Portable PC v: MP
           Bios: Insyde v: 6.70 date: 04/15/2013
CPU:       Dual core Intel Core i3-3120M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9977
           clock speeds: max: 2500 MHz 1: 1200 MHz 2: 1300 MHz 3: 2500 MHz
           4: 2300 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile
           GLX Version: 3.0 Mesa 17.3.6 - padoka PPA Direct Rendering: Yes
Audio:     Card Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.1.14-040114-generic
Network:   Card-1: Qualcomm Atheros AR8162 Fast Ethernet
           driver: alx port: 3000 bus-ID: 01:00.0
           IF: enp1s0 state: down mac: <filter>
           Card-2: Realtek RTL8188CE 802.11b/g/n WiFi Adapter
           driver: rtl8192ce port: 2000 bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (6.7% used)
           ID-1: /dev/sda model: Hitachi_HTS54505 size: 500.1GB
Partition: ID-1: / size: 28G used: 7.4G (29%) fs: ext4 dev: /dev/sda2
           ID-2: /boot size: 641M used: 157M (27%) fs: ext4 dev: /dev/sda1
           ID-3: /home size: 429G used: 23G (6%) fs: ext4 dev: /dev/sda4
           ID-4: swap-1 size: 2.05GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 55.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 256 Uptime: 1:19 Memory: 2168.6/3839.2MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

```

---

