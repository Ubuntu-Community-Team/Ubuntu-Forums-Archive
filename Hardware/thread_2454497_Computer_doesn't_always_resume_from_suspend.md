---
title: "Computer doesn't always resume from suspend"
date: 2020-11-30
forum: Hardware
---

### Post by ash22 on 2020-11-30
There is about a 30% chance that my computer won't wake up from sleep mode and I am greeted with just a black screen where nothing works rather than my login manager. I can't do anything but reboot the system. My computer I have this problem on is a desktop tower not a laptop which everyone else has this problem on. My CPU is Ryzen 5 2600 with an AMD Radeon Tonga card (the RX300 series) which uses the AMDGPU drivers. This computer is running Ubuntu 20.04 with the x86_64 Linux 4.8.10-040810-generic kernel. Is this bug alreddy known?

---

### Post by ajgreeny on 2020-11-30
I believe Ryzen CPUs are much better supported by a later kernel than you are using at the moment.

Give us more details of your hardware and software with terminal command ***inxi -Fzx***.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by kurt18947 on 2020-11-30
> This computer is running Ubuntu 20.04 with the x86_64 Linux 4.8.10-040810-generic kernel. Is this bug alredy known?

How would 20.04 be running a 4.8.10 kernel? I'm running 20.04.1 and my kernel is 5.4.0-54. And yes, in my experience newer kernels work much better on Ryzen machines.

---

### Post by ash22 on 2020-12-01
```
System:
  Kernel: 4.8.10-040810-generic x86_64 bits: 64 
  compiler: gcc v: 6.2.0 Desktop: Awesome 4.3 
  Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: ASUSTeK 
  model: ROG STRIX B450-F GAMING v: Rev 1.xx 
  serial: <filter> UEFI [Legacy]: American Megatrends 
  v: 2301 date: 04/19/2019 
CPU:
  Topology: 6-Core model: AMD Ryzen 5 2600 bits: 64 
  type: MT MCP arch: Zen+ rev: 2 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 
  sse4a ssse3 svm 
  bogomips: 91915 
  Speed: 1550 MHz min/max: 1550/3850 MHz 
  Core speeds (MHz): 1: 1550 2: 1550 3: 1550 4: 1550 
  5: 1550 6: 1550 7: 1550 8: 1550 9: 1550 10: 1550 
  11: 1550 12: 1550 
Graphics:
  Device-1: AMD Tonga PRO [Radeon R9 285/380] 
  vendor: Micro-Star MSI driver: amdgpu v: kernel 
  bus ID: 08:00.0 
  Display: x11 server: X.Org 1.20.8 driver: amdgpu 
  unloaded: modesetting resolution: 1920x1200~60Hz 
  OpenGL: renderer: AMD Radeon R9 380 Series (TONGA DRM 
  3.3.0 4.8.10-040810-generic LLVM 11.0.0) 
  v: 4.6 Mesa 20.2.1 - kisak-mesa PPA direct render: Yes 
Audio:
  Device-1: AMD Tonga HDMI Audio [Radeon R9 285/380] 
  vendor: Micro-Star MSI driver: snd_hda_intel v: kernel 
  bus ID: 08:00.1 
  Device-2: AMD Family 17h HD Audio vendor: ASUSTeK 
  driver: snd_hda_intel v: kernel bus ID: 0a:00.3 
  Sound Server: ALSA v: k4.8.10-040810-generic 
Network:
  Device-1: Intel I211 Gigabit Network vendor: ASUSTeK 
  driver: igb v: 5.3.0-k port: e000 bus ID: 03:00.0 
  IF: enp3s0 state: up speed: 100 Mbps duplex: full 
  mac: <filter> 
Drives:
  Local Storage: total: 3.41 TiB used: 1.37 TiB (40.2%) 
  ID-1: /dev/sda vendor: Western Digital 
  model: WDS500G2B0A size: 465.76 GiB 
  ID-2: /dev/sdb vendor: Samsung 
  model: SSD 850 EVO 250GB size: 232.89 GiB 
  ID-3: /dev/sdc vendor: Samsung model: HD103SI 
  size: 931.51 GiB 
  ID-4: /dev/sdd vendor: Seagate model: ST2000NM0033 
  size: 1.82 TiB 
Partition:
  ID-1: / size: 228.23 GiB used: 178.24 GiB (78.1%) 
  fs: ext4 dev: /dev/sdb1 
Sensors:
  Message: No sensors data was found. Is sensors 
  configured? 
Info:
  Processes: 3342 Uptime: 2m Memory: 15.66 GiB 
  used: 1.52 GiB (9.7%) Init: systemd runlevel: 5 
  Compilers: gcc: 9.3.0 Shell: fish v: 3.1.0 
  inxi: 3.0.38 

```

---

### Post by ash22 on 2020-12-01
> **kurt18947 said:**
> How would 20.04 be running a 4.8.10 kernel? I'm running 20.04.1 and my kernel is 5.4.0-54. And yes, in my experience newer kernels work much better on Ryzen machines.

I tried to upgrade to upgrade my kernel weeks ago and I looked up how to do upgrade and ran "sudo apt-get dist-upgrade" like it said. I assumed nothing happened becauz I was alreddy on the latest version supported and system updates will automatically upgrade the kernel when they're available.

---

### Post by CelticWarrior on 2020-12-01
First you need to run
```
sudo apt update
```
then follow by
```
sudo apt full-upgrade
```
('apt' used instead of 'apt-get' and 'full-upgrade' instead of 'dist-upgrade' - it has been the default usage for many years now)

Please post any error messages.

---

### Post by deadflowr on 2020-12-01
> **ash22 said:**
> I tried to upgrade to upgrade my kernel weeks ago and I looked up how to do upgrade and ran "sudo apt-get dist-upgrade" like it said. I assumed nothing happened becauz I was alreddy on the latest version supported and system updates will automatically upgrade the kernel when they're available.

Since you've got a non-standard (probably mainline) kernel you've probably removed the linux-generic meta-packages required to install the stable standard kernels.
I'd follow the above on running apt update/apt full-upgrade and if no issues doing that, then try running
```
sudo apt install linux-generic
```
This should pull in the current release's most recent stable kernel.

---

### Post by ping-wu on 2020-12-02
I have a Ryzen 7 2700 desktop running Ubuntu 20.04.1 (5.4.0.54 kernel).  Never had any suspend/wake-up problem since initial install.

---

### Post by P-I H on 2020-12-03
I add iommu=soft in /etc/default/grub and have no problem with suspend. Without I always get a black screen after restore from suspend.
acpi_enforce_resources=lax is added to get more sensors e.g. fan speed to work on this motherboard.

```
p-i@pi-TUF-B550M:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="iommu=soft acpi_enforce_resources=lax"

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
p-i@pi-TUF-B550M:~$ 

```

---

### Post by ash22 on 2020-12-03
Ok, I installed the newer kernel. Now I'll just keep using my computer for a few days to see if it still happens. How can I delete the older kernel I had?

---

### Post by ajgreeny on 2020-12-03
What kernels do you now have installed?
Show the output of ```
ls /boot | grep vmlinuz
``` which will show us installed kernels.  If you have only those two I would keep the old one but if you have more you can run ```
sudo apt autoremove
``` which should get rid of all except the two most recent versions.

---

### Post by ash22 on 2020-12-04
This is the output
```
vmlinuz
vmlinuz-4.8.10-040810-generic
vmlinuz-5.4.0-54-lowlatency
vmlinuz-5.4.0-56-generic
vmlinuz-5.4.0-56-lowlatency
vmlinuz.old

```

---

### Post by ajgreeny on 2020-12-04
You may find running command ```
sudo apt autoremove 
``` uninstalls that kernel for you but if not you could use synaptic.
You may not have synaptic installed as it is not a default application in most of the Ubuntu family any more but if you like a GUI it is so much more useful than Ubuntu-software or whatever it is now called.
You can use synaptic to search for specific packages that don't show in Ubuntu-software, and if you search for name only using **4.8.10-0** as the search term it should show you that kernel and any associated packages such as the ***linux-header*** packages that you can remove.

---

