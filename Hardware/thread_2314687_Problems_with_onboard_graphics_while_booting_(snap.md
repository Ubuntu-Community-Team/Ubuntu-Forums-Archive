---
title: "Problems with onboard graphics while booting (snapshots of screen)"
date: 2016-02-23
forum: Hardware
---

### Post by marosd on 2016-02-23
Hi guys,


[LIST=1]
[*]I have installed the minimal UBUNTU 15.04 - **NO GUI and I DO NOT want it**. 
[*]This Ubuntu has **3.19.0-49-generic** kernel. 
[*]When the system boots with this kernel at the beginning I can see  strange characters/letters/numbers - totally unreadable (see  attachement). But after few seconds my screen is going black and nice,  white, readable characters are displayed - so it works. Nevermind wrong  beginning (see attachement). 
[*]After login I ran this command for you, to help me to discover something:
[B]
sudo lspci | grep VGA[/B]

  00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 21)
  **sudo lshw -C display** 
[/LIST]

```
description: VGA compatible controller
   product: Intel Corporation
   vendor: Intel Corporation
   physical id: 2
   bus info: pci@0000:00:02.0
   version: 21
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi vga_controller bus_master cap_list rom
   configuration: driver=i915_bpo latency=0
   resources: irq:119 memory:80000000-80ffffff memory:90000000-9fffffff ioport:f000(size=64)
```

BUT


  
[LIST=1]
[*]I wanted a realtime kernel so I builded one - **3.18.25-rt23** 
[*]I successfuly builded a new realtime kernel BUT my graphics goes  wrong. While booting I can see unreadable characters/letters and later  is my screen totally black. Linux is running because I can access to it  thru serial console. Serial console is OK. 
[*]If in GRUB I choose recovery mode of this new kernel, graphics is ugly, but I can see letters. 
[/LIST]


 **I do not want HD picture**, I do not want the X server or similar. **I  want simple, stupid black window with white characters and VGA monitor  and I cannot have it.** I tried many options without success.
  This is my actual /etc/default/grub file:


```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX="console=tty0 console=ttyS0,115200n8"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

THANK YOU, THANK YOU, THANK YOU for any help. On another PC I do not  have strange characters/letters. But I need it on my Gigabyte N3050N-D2P  board!


  UPDATE: **I think that this is only kernel problem**. I tried to recompile kernel  again with some settings in Graphics menu and it is better - I still  have a black screen after booting but when it boots the display is  flashing and I can see for a moment boot messages clearly. But monitor  is flashing and then goes black again. 

**Could you tell me WHAT I have to set in menuconfig of the kernel?** What is difference between 3.18.xx and 3.19.xx kernel.

I alsa start a new question on Askubuntu:
[http://askubuntu.com/questions/737895/problems-with-graphics-while-booting-ubuntu](http://askubuntu.com/questions/737895/problems-with-graphics-while-booting-ubuntu)



  I attached a pictures from my booting screen. Check names for correct order (if this server mixed it).

1. Booting - Phase 1 - Generic kernel. This screen shows a few seconds od booting

2. Booting - Phase 2 - Generic kernel. This screen shows corrected screen with good resolution and no problems at all.

3. Booting - Phase 3 - Generic kernel. Correct

4. Booting of realtime kernel. This is all I can see, after a few seconds it is going to black :(

---

### Post by marosd on 2016-02-23
I tried again to build a new 3.18.25 kernel. I selected only Intel graphics but no, still black screen.

I also tried to install Intel driver from this location:
[https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.2.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.2.0)

```

wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg -O -; sudo apt-key add -
 wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg-2 -O -; sudo apt-key add -

wget -O intel32.deb https://download.01.org/gfx/ubuntu/15.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.2.0-0intel1_i386.deb

 sudo dpkg -i intel32.deb


```

This yelled on me for missing dependancies, so I run:

```

sudo apt-get -f install

```

And again:

```

sudo dpkg -i intel32.deb

```

And instalation was successful. Then I run sudo reboot but black screen remains......:(


Is there any possibility HOW to get I915_BPO driver back to my kernel? Because my 3.19.0 kernel has I915_BPO and this kernel not... Am I right? Please help

---

### Post by marosd on 2016-02-24
[SIZE=3][FONT=microsoft sans serif]When I changed:[/FONT][/SIZE]

> GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

[SIZE=3][FONT=microsoft sans serif]It works (of course) but graphics is not my cup of tea. Its readable, but it has errors when I want to repeat some command with UP/DOWN arrow - that line become unreadable.[/FONT][/SIZE]

---

### Post by marosd on 2016-02-24
Ok guys... I build a 4.4.1 RT kernel and **finally I have a nice, readable boot messages and console screen!** [COLOR=#ff0000]**BUT**[/COLOR] (why there is always BUT):

Graphics for example on alsamixer is really bad, could you tell me why?

uname -a

```
Linux ubuntu 4.4.1-rt6 #1 SMP PREEMPT RT Wed Feb 24 04:27:02 CET 2016 i686 i686 i686 GNU/Linux
```

sudo lshw -C display

```
       
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:115 memory:80000000-80ffffff memory:90000000-9fffffff ioport:f000(size=64)
```

sudo lspci|grep VGA

00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 21)

sudo fbset -i

```
mode "1280x1024"
    geometry 1280 1024 1280 1024 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode

Frame buffer device information:
    Name        : inteldrmfb
    Address     : 0x900c0000
    Size        : 5242880
    Type        : PACKED PIXELS
    Visual      : TRUECOLOR
    XPanStep    : 1
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 5120
    Accelerator : No

```

cat /etc/default/grub

```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX="console=tty1 console=ttyS0,115200n8"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024
GRUB_GFXPAYLOAD_LINUX=text

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```


ALSAMIXER looks like this:

---

### Post by marosd on 2016-03-07
Any idea?

---

### Post by Yellow Pasque on 2016-03-07
Ubuntu 15.04 is EOL. Do you have these issues with an Ubuntu 15.10 Live USB?

---

