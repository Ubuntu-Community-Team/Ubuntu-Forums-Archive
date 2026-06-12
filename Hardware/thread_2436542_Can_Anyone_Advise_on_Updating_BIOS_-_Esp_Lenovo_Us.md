---
title: "Can Anyone Advise on Updating BIOS - Esp Lenovo Users?"
date: 2020-02-08
forum: Hardware
---

### Post by davepool on 2020-02-08
I'm a fairly new user to Ubuntu and still new to Linux (came to the OS last fall via MX Linux and Mint). In order to give myself a device to learn on and explore and not have to depend on it for anything, last month I bought a Lenovo ThinkPad X131e on eBay for $40. It had already been converted to Linux Mint (point being, the Windows environment was gone). The details you want to see about this device are at the bottom of this message. It's currently a dual-boot with Manjaro.

Recently, I have learned that the BCM4313 adapter this computer is cursed with is a cranky li'l bastard with a lot of users experiencing problems. Many attempts to get this adapter to work consistently have come to nothing.  A very knowledgeable person has advised me that a step I really need to take is to update the BIOS on the ThinkPad.  I am not opposed to this...but VERY reluctant to do it. I'm just not "there" yet in terms of confidence. So much of what I've read says that a BIOS very rarely needs updating, might solve an issue like heat or hardware compatibility, never "speeds up" a computer and can easily "brick" the whole thing.  Now, at $40, if I trashed the computer, I wouldn't be out that much...but I'm wary of the whole process...

ESPECIALLY since it appears that updating the BIOS when the ThinkPad ran Windows would have been reasonably easy...but doing it within Linux is another thing!  I've already downloaded the most recent file...it's an .iso and that led to my first incorrect assumption: like with distros, I thought I could download the .iso on my Windows PC, use Etcher to flash to a USB and voila! Not so. It's not bootable, there's no file table, etc (so Etcher tells me)

Long story short(er)...what I've found in searching is that this describes what I can look forward to: 
[https://www.cyberciti.biz/faq/update-lenovo-bios-from-linux-usb-stick-pen/](https://www.cyberciti.biz/faq/update-lenovo-bios-from-linux-usb-stick-pen/)

Yipes!

OTOH, my flag to Lenovo users is because I also found this: [https://support.lenovo.com/us/en/videos/vid100759](https://support.lenovo.com/us/en/videos/vid100759)

That middle paragraph under the video leads me to believe that the Lenovo OneKey Recovery tool -- though it looks into the recovery partition first -- might also allow the user to use a USB, selecting it from the pull-down menu it refers to.

Can anyone offer any thoughts about the info in either of the above links?

[dave@ThinkPad-X131e ~]$ inxi -Fx
System:    Host: ThinkPad-X131e Kernel: 4.19.101-1-MANJARO x86_64 bits: 64 compiler: gcc v: 9.2.0 Desktop: KDE Plasma 5.17.5 
           Distro: Manjaro Linux 
Machine:   Type: Laptop System: LENOVO product: 33722WU v: ThinkPad X131e serial: <root required> 
           Mobo: LENOVO model: 33722WU v: Win8 Pro DPK TPG serial: <root required> UEFI [Legacy]: LENOVO v: G9ETA0WW (2.60 ) 
           date: 03/13/2015 
Battery:   ID-1: BAT1 charge: 58.7 Wh condition: 64.6/62.6 Wh (103%) model: SANYO 45N1176 status: Discharging 
CPU:       Topology: Dual Core model: AMD E-300 APU with Radeon HD Graphics bits: 64 type: MCP arch: Bobcat L2 cache: 512 KiB 
           flags: lm nx pae sse sse2 sse3 sse4a ssse3 svm bogomips: 5190 
           Speed: 1298 MHz min/max: 780/1300 MHz Core speeds (MHz): 1: 1287 2: 779 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Wrestler [Radeon HD 6310] vendor: Lenovo driver: radeon v: kernel 
           bus ID: 00:01.0 
           Display: x11 server: X.Org 1.20.7 driver: radeon FAILED: ati unloaded: modesetting resolution: 1366x768~60Hz 
           OpenGL: renderer: AMD PALM (DRM 2.50.0 / 4.19.101-1-MANJARO LLVM 9.0.1) v: 3.3 Mesa 19.3.3 direct render: Yes 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Wrestler HDMI Audio vendor: Lenovo driver: snd_hda_intel v: kernel 
           bus ID: 00:01.1 
           Device-2: Advanced Micro Devices [AMD] FCH Azalia vendor: Lenovo driver: snd_hda_intel v: kernel bus ID: 00:14.2 
           Sound Server: ALSA v: k4.19.101-1-MANJARO 
Network:   Device-1: Broadcom and subsidiaries BCM4313 802.11bgn Wireless Network Adapter driver: bcma-pci-bridge v: N/A 
           port: 3100 bus ID: 02:00.0 
           Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Lenovo driver: r8169 v: kernel port: 2000 
           bus ID: 03:00.0 
           IF: enp3s0 state: down mac: 08:9e:01:71:bb:a7 
           IF-ID-1: wlp2s0b1 state: up mac: 2c:d0:5a:01:5d:aa 
Drives:    Local Storage: total: 316.73 GiB used: 11.80 GiB (3.7%) 
           ID-1: /dev/sda vendor: HGST (Hitachi) model: HTS725032A7E630 size: 298.09 GiB 
           ID-2: /dev/sdb model: SATA SSD size: 18.64 GiB 
Partition: ID-1: / size: 14.36 GiB used: 11.80 GiB (82.2%) fs: ext4 dev: /dev/sda3 
           ID-2: swap-1 size: 11.18 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 68.8 C mobo: 0.0 C gpu: radeon temp: 69 C 
           Fan Speeds (RPM): cpu: 493 
Info:      Processes: 151 Uptime: 18m Memory: 7.20 GiB used: 1.07 GiB (14.9%) Init: systemd Compilers: gcc: 9.2.0 Shell: bash 
           v: 5.0.11 inxi: 3.0.37 
[dave@ThinkPad-X131e ~]$

---

### Post by crip720 on 2020-02-08
To do it the easiest and safest way,I would recommend making a partition and installing windows.  Use woeusb to make a bootable windows installer.  There are work arounds to do it with Linux, but probably faster just to use windows.  Lenovo might even have a window's tool for bios updating that will make it even safer.  Windows allows you to use it without a paid license for a limited time.  Have a Ubuntu installer USB handy if windows wipes grub, less chance if UEFI install.  Google bios update lenovo to see what is required.  Linux is good, but use the best tool for the job.  In this case usually windows.  Just make sure to install windows in right partition.

---

### Post by davepool on 2020-02-08
Thanks! Much to digest there! I'll be checking out woeusb to see what that is all about.

One thing that just occurred to me: can I do the download of Windows and the creation of the WoeUSB on my Windows PC and then just move the USB to the Linux laptop?

---

### Post by crip720 on 2020-02-08
Do not need woeusb(if it even works on windows) if using windows to make installer usb, just one of very few tools that work on Linux for making bootable windows USB.  Other Linux USB tools don't make a windows installer bootable, but work well for Linux installers.

---

### Post by oldfred on 2020-02-08
Lenovo is just starting to add UEFI updates from Linux.
[https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/)

Most UEFI will update reading the update file directly from a FAT32 formatted partition. Either on flash drive or internal drive. I use my ESP.  I made ESP larger just for use like this, but I have motherboards for desktop systems, both Gigabyte & Asus are similar.

I would think if an ISO, it should be a bootable system. If you open it does it show /EFI/bootx64.efi. All external devices boot from that in UEFI boot mode. Or does it just contain an update file?
My Samsung firmware update was a tiny ISO, that just booted and had a DOS type screen that only offered to update.

---

### Post by davepool on 2020-02-09
So, guess what the solution turned out to be?

In another thread in the Networking section, forum volunteers had been helping me try to cure the problem with the Broadcom driver in my ThinkPad...and a day or so ago, I mentioned that just out of curiosity I had booted the ThinkPad live from a USB snapshot of an MX Linux install I have on an Acer Aspire One (thanks to the incredibly handy MX Linux Snapshot tool they include)...and magically, the wireless connection was made, the speeds were way up and no pages timed out.  Another member replied that he thought he'd read somewhere that the MX developers had some "assistance" from Broadcom or a "special relationship" with them.  I trotted over to the MX Forum, got replies from two of their developers and while I don't know about any assistance or the nature of the relationship (I didn't ask) they did tell me that MX ships with proprietary Broadcom drivers that allows MX to work with the BCM-4313 when it won't with other distros. Well, I can certainly vouch for that!  I hard installed my MX Linus snapshot on the ThinkPad and the problem appears to be solved!  No updating of the BIOS and not even a swap of the wireless card.  

So there it is.  Thanks to everyone for their replies above but, I gotta say, collectively they just convinced me more that I didn't have the confidence to "go there" with something that drastic and, with Linux at least, something that complicated and "user hostile."

---

### Post by mörgæs on 2020-02-09
According to the [Broadcom sticky thread]("https://ubuntuforums.org/showthread.php?t=2214110") the BCM4313 should be fairly easy to get working under Buntu but congratulations anyway. 
Please mark the thread solved.

---

### Post by davepool on 2020-02-09
> **mörgæs said:**
> According to the [Broadcom sticky thread]("https://ubuntuforums.org/showthread.php?t=2214110") the BCM4313 should be fairly easy to get working under Buntu but congratulations anyway. 
Please mark the thread solved.

chili555 certainly tried mightily with my situation...and I appreciated his efforts.

---

