---
title: "Ubuntu 15.04 Hardware acceleration with Nvidia graphics card not working"
date: 2015-07-12
forum: Hardware
---

### Post by c_xy on 2015-07-12
Hello, I recently installed Ubuntu 15.04 server for our new server.

Here are the specs:

Again it is dell poweredge r730 server
96 GB memory
25 TB storage
2 CPU 2.6 GHz, 10core.
The graphics card on the server is: NVIDIA Tesla K10 GPU

I've installed ubuntu-desktop as a gui.

However, we are running into an issue with recognizing the graphics card and driver for 3D acceleration. Right now, I can't log into unity, so I was forced into installing gnome-session-flashback. I can't login into Compiz either, but I can login to Metacity.

Here is some information:

```
~$  lspci | grep VGA
0c:00.0 VGA compatible controller: Matrox Electronics Systems Ltd. G200eR2 (rev 01)


```


```
~$   lspci | grep 3D
05:00.0 3D controller: NVIDIA Corporation GK104GL [Tesla K10] (rev a1)
06:00.0 3D controller: NVIDIA Corporation GK104GL [Tesla K10] (rev a1)


```



```
 ~$ sudo lshw -C video
  *-display               
       description: 3D controller
       product: GK104GL [Tesla K10]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:33f0-33ef iomemory:33f0-33ef irq:31 memory:92000000-92ffffff memory:33fe0000000-33fefffffff memory:33ff0000000-33ff1ffffff
  *-display
       description: 3D controller
       product: GK104GL [Tesla K10]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:33f0-33ef iomemory:33f0-33ef irq:31 memory:91000000-91ffffff memory:33fc0000000-33fcfffffff memory:33fd0000000-33fd1ffffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: G200eR2
       vendor: Matrox Electronics Systems Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=16
       resources: memory:90000000-90ffffff memory:93800000-93803fff memory:93000000-937fffff


```


When I try to type glx commands I get the following error messages:

```
 ~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


```


```
 ~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".



```


Here is some info from the Xorg.0 log file:

```
 ~$ egrep '\((EE|WW|NI)\)' /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.008] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.008] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.008] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.013] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.013] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.023] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    11.023] (WW) "xmir" is not to be loaded by default. Skipping.
[    11.563] (EE) [drm] KMS not enabled
[    11.563] (EE) [drm] KMS not enabled
[    11.563] (WW) Falling back to old probe method for modesetting
[    11.563] (WW) Falling back to old probe method for fbdev
[    11.572] (EE) open /dev/fb0: No such file or directory
[    11.572] (WW) Falling back to old probe method for vesa
[    12.561] (EE) MGA(0): [drm] Direct rendering only supported with G200/G400/G450/G550.
[    12.562] (WW) MGA(0): Direct rendering disabled
[    12.566] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)



```


Something is not quite right.Right now I have nvidia-346 (346.59) installed as the driver. I tried installing bumblebee in a previous install than the one I have currently. That was able to get glxinfo and glxgears command to work, but that was only through software rendering. It still was not picking up my Hardware GPU.

Uitimately, the goal is  configure my GPU so it is used by Ubuntu 15.04. Is this a simple process? Or a simple step I'm overlooking?  I have some experience using Ubuntu server, but I'm not too familiar with GPU and integrating it into Ubuntu server operations. I would appreciate any feedback, help, suggestions.

Thank you for your time.

c

---

### Post by TheFu on 2015-07-12
Support for 15.04 ends in January. Most people deploying a server will use an LTS - 14.04 LTS is the current release with 5 yrs of support. Felt it was important to say it.

The rest is really just a question ... You really want to have a GUI on a server with all that RAM and power?  I've just never met anyone that did. It is a stability question.  The proprietary GPU drivers tend to be terrible and buggy on Linux. That can bring a server down.  I can think of thousands of things to do with a machine like - NONE of them include a GUI on the server itself or a GPU. ;)  Guess that is just my sys admin side writing.

---

### Post by c_xy on 2015-07-12
> **TheFu said:**
> Support for 15.04 ends in January. Most people deploying a server will use an LTS - 14.04 LTS is the current release with 5 yrs of support. Felt it was important to say it.

The rest is really just a question ... You really want to have a GUI on a server with all that RAM and power?  I've just never met anyone that did. It is a stability question.  The proprietary GPU drivers tend to be terrible and buggy on Linux. That can bring a server down.  I can think of thousands of things to do with a machine like - NONE of them include a GUI on the server itself or a GPU. ;)  Guess that is just my sys admin side writing.

Yes, that was the original plan...14.04. We initially ran into several problems with 14.04 with our new system.  A few bugs, but also severe  lag/delay time in resizing windows using the gui. Also, the necessary Nvidia driver for our GPU (346) did not come with 14.04.2.


We had no choice but to go to 15.04. Not the most ideal scenario, but really no other choice. The gui is necessary because we have several people connecting to the server remotely using nomachine from windows clients. The work conducted on the server requires a gui interface. The work involves high-end computation, but also use of a gui. Thus, the need for a gui-desktop. Purchasing the video card was purchased to enhance computational power. 

The goal is to take advantage of this GPU, but right now Ubuntu is not recognizing it for 3D acceleration.

Just stuck on what is the next step to integrate our GPU with our Ubuntu OS.  We've tried just about everything.

Your help would greatly be appreciated.

Thank you.


c

---

### Post by TheFu on 2015-07-13
Thanks for taking the time to explain the situation. This is a perfect reason to run a non-LTS release. 

For remote access with a remote desktop, the GPU won't matter or be used. You can install the x2go-server package and people can remotely connect. Not good for visualization and Unity cannot be used, but LXDE, KDE, openbox all work reasonably well. x2go uses NX, which leverages ssh. It feels 2-3x faster than RDP or VNC.

I'm ignorant on GPU drivers for workloads. Do the desktop drivers have to be loaded to run hundreds of parallel compute problems against the GPU? I thought there was another library that was loaded ... but I'm completely ignorant. Sorry. The last video card I bought was $20 and I don't ever remember using it after the install was done.

Doubt my google-fu will be much help, but according to nVidia [https://devtalk.nvidia.com/default/board/53/gpu-computing/](https://devtalk.nvidia.com/default/board/53/gpu-computing/) is the forum to get help. That is one big GPU for processing data! Just under 5k processors! WOW!
[http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/index.html](http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/index.html) - which I assume you've seen for CUDA stuff. The instructions are all for 14.04 and 14.10(no support).

---

### Post by c_xy on 2015-07-13
> 
Thanks for taking the time to explain the situation. This is a perfect reason to run a non-LTS release. 



Thanks. Again, not the most ideal situation, but 15.04 works better with our system than 14.04.2 did.



> For remote access with a remote desktop, the GPU won't matter or be used. You can install the x2go-server package and people can remotely connect. Not good for visualization and Unity cannot be used, but LXDE, KDE, openbox all work reasonably well. x2go uses NX, which leverages ssh. It feels 2-3x faster than RDP or VNC.

I think we will try to stick with Nomachine. It has worked well for our purposes and line of work. Visualization is a must for us. And nomachine to this point has provided that for us.

> 

I'm ignorant on GPU drivers for workloads. Do the desktop drivers have to be loaded to run hundreds of parallel compute problems against the GPU? I thought there was another library that was loaded ... but I'm completely ignorant. Sorry. The last video card I bought was $20 and I don't ever remember using it after the install was done.



Using a GPU is new for us as well. But, all the computation is done on the server itself. We are just connecting remotely from windows desktop machines to the server itself. Although this is a new phase for us, right now our biggest hurdle just having the operating system recognize it. One thing I didn't mention in the original post is that the nvidia driver settings does not even recognize the graphics card. Which is odd. I'm tempted to manually install the driver from Nvidia's website:   [http://www.nvidia.com/download/driverResults.aspx/87235/en-us](http://www.nvidia.com/download/driverResults.aspx/87235/en-us)

That might help? I don't know.

> 

Doubt my google-fu will be much help, but according to nVidia [https://devtalk.nvidia.com/default/board/53/gpu-computing/](https://devtalk.nvidia.com/default/board/53/gpu-computing/) is the forum to get help. That is one big GPU for processing data! Just under 5k processors! WOW!
[http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/index.html](http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/index.html) - which I assume you've seen for CUDA stuff. The instructions are all for 14.04 and 14.10(no support).

[/QUOTE]

Yes, we really want to take advantage of the GPU.

Thank you for your suggestions. I will definitely check those links.

And if you or anybody else have any thing to add/suggest ,etc. please do.

Thanks again.

c

---

### Post by TheFu on 2015-07-13
NoMachine is the commercial NX implementation. x2go is also NX. I've never used NoMachine's server stuff. Never needed it.  I'm using x2go right now from a Windows laptop into a VM-desktop running in a private cloud. This is how I work daily. x2go is THAT good.

For remote desktop connections, the GPU hardware means absolutely NOTHING. I'm positive on that. It only matters if you sit inside the data center and type on a console.

Found this:
> The lack of ability to output images to a display was the main difference between Tesla products and the consumer level GeForce cards and the professional level Quadro cards  - looks like the card doesn't actually work as a normal GPU or am I reading that wrong?  Basically, it is a CUDA or OpenCL processor, not a video card.

Found this too: 
> Due to Tesla's non-output nature, fillrate and graphics API compatibility are not applicable.
and
> the goal of Tesla GPUs is to compute complex math as fast as possible. Even if you had one, you wouldn&#8217;t be able to game with it. There are no video outputs, and likely no logic at all on the board to drive them even if they were there. Tesla is a brand that means business, designed for those who have some of the most serious jobs on earth.

To get video out from that server, you'll be using the Matrox GPU - which I don't think works with nvidia drivers.

---

### Post by QIII on 2015-07-13
Some of the most recent Teslas do have a single DVI out, but it's not really meant to be much more than a functional display output.  It may simply be too new (or of little interest) for the Linux community to attempt to create an open source driver or Nvidia to create a Linux driver.

That hardware is targeted at GPGPU and stream processing, not graphics.  That is, it's intended to be used for parallel processing, not providing a desktop.  An inexpensive card would be more suitable for that.

As stated, the host NX server's GPU isn't going to be exercised by an NX client. NX just sends the client information on what the client GPU should render on screen.  It's a lot faster than sending bitmaps, but it's still not using the server's graphics.

---

### Post by c_xy on 2015-07-14
TheFu and QIII....thank you both for your helpful responses.

So, Tesla K10 is just to enhance and speed up computation/processes usually dedicated to a CPU. Not something dedicated to video like your typical graphics card.

That explains it.

So, with that said, this means I wouldn't be able to use Unity or Gnome 3 since they both require/use 3D acceleration and a "normal" graphics card. This would also explain why I couldn't use Compiz from the gnome-shell flashback, but I could use Metacity. Or why it wouldn't appear in Nvidia settings? Maybe Ubuntu was looking for video card instead of GPGPU card?

Not the end of the world. We are more than happy just to use a lightweight desktop environment. We don't need the bells and whistles of Unity. Our old server had 10.04 installed using GNOME and that suited our work needs just fine with a basic gui. We wanted to upgrade our system and getting something additional like the Tesla K10 fits our needs. Speeding up high-end computations is the priority, not not complex visual graphics. I was unaware of the distinction between GPU's. 

On side note, since there is no need to have unity installed, is it possible to install a lightweight desktop gui  on  Ubuntu server with the commands:



```
sudo apt-get install lubuntu-desktop
```

or

```
sudo apt-get install xbuntu-desktop
```

or

```
sudo apt-get install gnome-session-flashback
```

I ask this because during many re-installs of either Ubuntu server 14.04.2 or Ubuntu server 15.04 during troubleshooting, I could never install either of the those lightweight desktop environments with the above commands by themselves. I would always have to use this command first:

```
sudo apt-get install ubuntu-desktop
```

 Then I would have to install either gnome-flashback, xbuntu or  lubuntu. If I installed either of the 3 by themselves, the gui's would never appear after installation and then rebooting. The command line without the gui would always appear after reboot. Only when installing ubuntu-desktop first, and then either of the 3, a gui would appear with gui selection options after reboot. Why is this the case?

Thank you very much again.

c

---

### Post by oldfred on 2015-07-14
I thought Matrox video was only in very old systems.

But it is in a lot of servers.
[http://www.ubuntu.com/certification/catalog/component/pci/102b%3A0534/](http://www.ubuntu.com/certification/catalog/component/pci/102b%3A0534/)

Bug report on newer Ubuntu, but really xorg
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035)

---

### Post by TheFu on 2015-07-14
Could can install the entire "desktop" OR you could install just the DE without all those extra programs you'll never use.  Then YOU get to install the programs which will actually be needed and used.

For example - instead of xubuntu-desktop, use "xfce4" as the package.   Basically, just leave off the "-desktop" part. Also - if you do install multiple DEs that are based on Gnome, some of the settings written to HOME can collide, so it is best to test using different userids until you decide which desktop you want. There are some settings that collide between the gnome-based DEs and either strange things happen or it breaks.

---

### Post by Yellow Pasque on 2015-07-14
I think you'll be able to use the Tesla like you would on a laptop with Optimus/hybrid graphics (i.e. an Nvidia 3D Controller that runs through an Intel GPU for display). But first, you probably have to get the Matrox card to work with kernel modesetting:

[http://cateee.net/lkddb/web-lkddb/DRM_MGAG200.html](http://cateee.net/lkddb/web-lkddb/DRM_MGAG200.html)
According to ^that, if your Matrox chip has PCI ID 102b:0534 (check lspci -v), it should work the mgag200 kernel module/driver.
What happens when you manually load the kernel module for the Matrox chip?:
```
sudo modprobe -v mgag200
```

---

### Post by c_xy on 2015-07-16
Hello,

When I manually type

```
sudo modprobe -v mgag200
```[/QUOTE]

I get this:

> 

modprobe: FATAL: Module mgag200 not found.




Not sure what is going on here? Do I need to install a package(s)?


The output for lspci -v:

> 
lspci -v: |grep PCI
00:01.0 PCI bridge: Intel Corporation Xeon E5 v3/Core i7 PCI Express Root Port 1 (rev 02) (prog-if 00 [Normal decode])
00:02.0 PCI bridge: Intel Corporation Xeon E5 v3/Core i7 PCI Express Root Port 2 (rev 02) (prog-if 00 [Normal decode])
00:03.0 PCI bridge: Intel Corporation Xeon E5 v3/Core i7 PCI Express Root Port 3 (rev 02) (prog-if 00 [Normal decode])
00:03.2 PCI bridge: Intel Corporation Xeon E5 v3/Core i7 PCI Express Root Port 3 (rev 02) (prog-if 00 [Normal decode])
    Capabilities: [98] PCI Advanced Features
00:1c.0 PCI bridge: Intel Corporation C610/X99 series chipset PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
00:1c.7 PCI bridge: Intel Corporation C610/X99 series chipset PCI Express Root Port #8 (rev d5) (prog-if 00 [Normal decode])
    Capabilities: [98] PCI Advanced Features
03:00.0 PCI bridge: PLX Technology, Inc. PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch (rev ca) (prog-if 00 [Normal decode])
    Capabilities: [a4] Subsystem: PLX Technology, Inc. PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch
04:08.0 PCI bridge: PLX Technology, Inc. PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch (rev ca) (prog-if 00 [Normal decode])
    Capabilities: [a4] Subsystem: PLX Technology, Inc. PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch
04:10.0 PCI bridge: PLX Technology, Inc. PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch (rev ca) (prog-if 00 [Normal decode])
    Capabilities: [a4] Subsystem: PLX Technology, Inc. PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch
09:00.0 PCI bridge: Renesas Technology Corp. Device 001d (prog-if 00 [Normal decode])
0a:00.0 PCI bridge: Renesas Technology Corp. Device 001d (prog-if 00 [Normal decode])
0b:00.0 PCI bridge: Renesas Technology Corp. Device 001a (prog-if 00 [Normal decode])
    Capabilities: [70] Express PCI-Express to PCI/PCI-X Bridge, MSI 00
7f:10.0 System peripheral: Intel Corporation Xeon E5 v3/Core i7 PCIe Ring Interface (rev 02)
    Subsystem: Intel Corporation Xeon E5 v3/Core i7 PCIe Ring Interface
7f:10.1 Performance counters: Intel Corporation Xeon E5 v3/Core i7 PCIe Ring Interface (rev 02)
    Subsystem: Intel Corporation Xeon E5 v3/Core i7 PCIe Ring Interface
80:01.0 PCI bridge: Intel Corporation Xeon E5 v3/Core i7 PCI Express Root Port 1 (rev 02) (prog-if 00 [Normal decode])
80:02.0 PCI bridge: Intel Corporation Xeon E5 v3/Core i7 PCI Express Root Port 2 (rev 02) (prog-if 00 [Normal decode])
80:03.0 PCI bridge: Intel Corporation Xeon E5 v3/Core i7 PCI Express Root Port 3 (rev 02) (prog-if 00 [Normal decode])
80:03.2 PCI bridge: Intel Corporation Xeon E5 v3/Core i7 PCI Express Root Port 3 (rev 02) (prog-if 00 [Normal decode])
ff:10.0 System peripheral: Intel Corporation Xeon E5 v3/Core i7 PCIe Ring Interface (rev 02)
    Subsystem: Intel Corporation Xeon E5 v3/Core i7 PCIe Ring Interface
ff:10.1 Performance counters: Intel Corporation Xeon E5 v3/Core i7 PCIe Ring Interface (rev 02)
    Subsystem: Intel Corporation Xeon E5 v3/Core i7 PCIe Ring Interface








Another thing, just checking the output from our older dell T710 Poweredge server running 10.04.

Here is the output of lscpi

> 

lspci | grep VGA 
06:03.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200eW WPCM450 (rev 0a)
 
 



 and

>  

 sudo lshw -C video
  *-display UNCLAIMED     
        description: VGA compatible controller
        product: MGA G200eW WPCM450
        vendor: Matrox Graphics, Inc.
        physical id: 3
        bus info: pci@0000:06:03.0
        version: 0a
        width: 32 bits
        clock: 33MHz
        capabilities: pm bus_master cap_list
        configuration: latency=32 maxlatency=32 mingnt=16
        resources: memory:d5000000-d57fffff(prefetchable)  memory:de7fc000-de7fffff memory:de800000-deffffff  memory:de000000-de00ffff(prefetchable)



I see the same UNCLAIMED message in our older system as our current 15.04 install on the dell r730. We never ran into issues using a  gui on our 10.04 system. AGain, no reall high end graphics used or delay problems. So I'm wondering if is this problem solveable or really not that big of a deal (in our case).

---

### Post by Yellow Pasque on 2015-07-16
> I see the same UNCLAIMED message in our older system as our current 15.04 install on the dell r730. We never ran into issues using a gui on our 10.04 system.
The difference is that you have the nvidia driver installed on your r730, which breaks 3D functionality:
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```
I was thinking if you got KMS to work with the Matrox card, it would work (I could be wrong though).

> modprobe: FATAL: Module mgag200 not found.
That's odd. It's available here on my Debian system (using kernel 4.1.x). Maybe Ubuntu doesn't enable it for some reason?

---

### Post by c_xy on 2015-07-26
Decided to try using 14.04.2 again instead.

I'll mark this thread as solved.

---

