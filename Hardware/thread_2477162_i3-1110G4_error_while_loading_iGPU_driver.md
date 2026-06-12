---
title: "i3-1110G4 error while loading iGPU driver"
date: 2022-07-16
forum: Hardware
---

### Post by flamingi on 2022-07-16
I have installed Ubuntu 22.04 on my machine (Huawei Matebook E 2022, i3-1110G4, 8GB RAM, NVMe SSD), but I have trouble loading the Intel GPU drivers. When I select Ubuntu in GRUB, a couple lines show up and then the screen goes blank. If I use [FONT=courier new]nomodeset[/FONT] I can boot fine.

I ran ```
[COLOR=#2E8B57][FONT=monospace]journalctl -b -1 | nc termbin.com 9999[/FONT][/COLOR]
```, you can find the logs here: [https://termbin.com/zdxh](https://termbin.com/zdxh)
System info can be found here: [https://paste.ubuntu.com/p/Q8gb7x7WTQ/](https://paste.ubuntu.com/p/Q8gb7x7WTQ/)

There are 3 errors with i915 in the trace, which I think are the cause of the issue, but I don't know how to fix them. All help is appreciated.

---

### Post by #&amp;thj^% on 2022-07-16
Have a look at this: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)
In your system-info report you show no PPA's and that's a good thing, but sometimes different/newer drivers help.
You seem to be lacking a good video driver from my view.
EDIT: Before adding the PPA, if you was going to that, try adding this to your "/etc/default/grub"
```
intel_iommu=off
```
and don't forget to update grub after the change.

---

### Post by flamingi on 2022-07-16
I have tried that before, but just to be sure I did it again. I added the ppa and upgraded all available packages:
```

sudo add-apt-repository ppa:oibaf/graphics-drivers 
sudo apt update
sudo apt upgrade

```

Unfortunately, the issue is still persisting with the same error/stack trace: [https://termbin.com/9uxd](https://termbin.com/9uxd)

I don't have any dedicated GPU, just the onboard one. Shouldn't the Intel drivers be all in the kernel already? 11th gen isn't brand new, as far as I can tell from my research it should be fully supported since kernel 5.11.

---

### Post by #&amp;thj^% on 2022-07-16
Yep it should be, but bugs are plentiful with Jammy ATM. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1958004](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1958004)
Also did you add>>> "intel_iommu=off" to grub yet?
If you can, try kernel 5.17

---

### Post by flamingi on 2022-07-16
I have added intel_iommu=off to grub in kernel 5.15.
With the updated ppa driver: [https://termbin.com/xlea](https://termbin.com/xlea)
With the driver shipped with Ubuntu: [https://termbin.com/lgqv](https://termbin.com/lgqv)

I have updated the kernel to 5.17, still the same error :(
[https://termbin.com/gbv6](https://termbin.com/gbv6)

---

### Post by #&amp;thj^% on 2022-07-16
What shows from this command:
```
apt policy mesa-vdpau-drivers
```

---

### Post by flamingi on 2022-07-16
```

mesa-vdpau-drivers:
  Installed: 22.0.1-1ubuntu2.1
  Candidate: 22.0.1-1ubuntu2.1
  Version table:
 *** 22.0.1-1ubuntu2.1 500
        500 http://de.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     22.0.1-1ubuntu2 500
        500 http://de.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

---

### Post by #&amp;thj^% on 2022-07-16
Wow I'm running out of suggestions here.
What IGPU is it?
```
inxi -GC
```
EDIT Just for my peace of mind can you also show this please:
```
cat /etc/default/grub
```
And I don't like this from the last report>>"UBSAN: array-index-out-of-bounds in /home/kernel/COD/linux/drivers/gpu/drm/i915/display/intel_display.c:10086:20"
even though it claims it added?
This is another bug worthy issue.

---

### Post by flamingi on 2022-07-16
The GPU is an specced down version of the Xe Graphics found in the i5/i7, it's officially an Intel UHD GPU and not an Xe, but the architecture is the same. The error you mentioned is the main suspect from my side as well, it appears in all the logs I linked. The GRUB file is unmodified.

```

mingkwan@mingkwan-DRC-WXX:~$ inxi -GC
CPU:
  Info: dual core model: 11th Gen Intel Core i3-1110G4 bits: 64 type: MT MCP
    cache: L2: 2.5 MiB
  Speed (MHz): avg: 1200 min/max: 400/3900 cores: 1: 1189 2: 1199 3: 1196
    4: 1219
Graphics:
  Device-1: Intel driver: N/A
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: vesa
    unloaded: fbdev,modesetting gpu: N/A resolution: 2560x1600~93Hz
  OpenGL: renderer: llvmpipe (LLVM 13.0.1 256 bits) v: 4.5 Mesa 22.0.1
mingkwan@mingkwan-DRC-WXX:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by #&amp;thj^% on 2022-07-16
Yep the driver is not loaded>>>"Device-1: Intel driver: N/A"
Also grub is not correct
So use this for our efforts here:
```
sudo nano /etc/default/grub
```
and add "intel_iommu=off"to the line IE:
```
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=off quiet splash"
```
Save with key combo <Ctrl +o> and exit with <Ctrl +x>
now run:
```
sudo update-grub
```
Reboot to check our new parameters.

---

### Post by flamingi on 2022-07-16
Tried it out, still the same error. 

How would I solve this issue if I wanted to keep iommu on? I wanted to do some light VM stuff with GVT-g where this setting needs to be turned on. (Just a hypothetical question, I can live with it turned off as well, not quite sure if VM with a dual core i3 is a good idea in the first place)

Edit: It didn't boot, but looking at the logs, the error seems to be gone... [https://termbin.com/swix](https://termbin.com/swix)
Edit2: My bad, uploaded the wrong boot, still the same error as before :( [https://termbin.com/aztf](https://termbin.com/aztf)

---

### Post by #&amp;thj^% on 2022-07-16
That i3 should barely work with your  light VM stuff , but we do need a proper driver first.
I need to check with someone, before offering any more suggestions.
I'll be back if I have good news.
You can undo all we have done here though. (If you need help let me know)
Well here it is any way:
```
sudo apt-get install ppa-purge
```
then run:
```
sudo ppa-purge ppa:oibaf/graphics-drivers
```
And you know how to revert grub back now.
If you file a bug they will want you to disable all third party sources for the report.

---

### Post by flamingi on 2022-07-16
Hmm, I see. I'm not quite sure if it's an actual bug or just some misconfiguration. After all, the CPU was released in 2020 and I'm surely not the first one to install Linux with it.

Anyway, thanks for the help so far, please let me know if you come up with another possible solution.

---

### Post by #&amp;thj^% on 2022-07-16
Well I did not find this developer helpful at all.
I've done very little to change mine as you see here:
```
cat /etc/default/grub
# GRUB boot loader configuration

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="EndeavourOS"
GRUB_CMDLINE_LINUX_DEFAULT="quiet apparmor=1 security=apparmor lsm=landlock,lockdown,yama,apparmor,bpf ipv6.disable=1 loglevel=3 nowatchdog nvme_load=YES"
GRUB_CMDLINE_LINUX=""

```
and mine loads just fine:
```
inxi -CG
CPU:
  Info: quad core model: Intel Core i5-10210U bits: 64 type: MT MCP cache:
    L2: 1024 KiB
  Speed (MHz): avg: 3620 min/max: 400/4200 cores: 1: 3517 2: 3444 3: 3310
    4: 3441 5: 3895 6: 3874 7: 3797 8: 3682
Graphics:
  Device-1: Intel CometLake-U GT2 [UHD Graphics] driver: i915 v: kernel
  Device-2: IMC Networks Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 21.1.4 with: Xwayland v: 22.1.3 driver: X:
    loaded: intel unloaded: fbdev,modesetting,vesa gpu: i915
    resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics (CML GT2) v: 4.6 Mesa 22.1.3

```
For the record this system is not Ubuntu. But all was fine when Ubuntu was tested on it.

---

