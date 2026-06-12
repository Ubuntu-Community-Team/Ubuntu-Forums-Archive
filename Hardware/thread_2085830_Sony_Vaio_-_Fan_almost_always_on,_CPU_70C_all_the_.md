---
title: "Sony Vaio - Fan almost always on, CPU 70C all the time, how to fix it?"
date: 2012-11-19
forum: Hardware
---

### Post by deckoff on 2012-11-19
I have Sony Vaio pcG-392M. The video is  "GeForce 8400M GT". I use XBMC on it most of the time. 
**The problem:**
Fan is on most of the time. CPU stays 70C, gets that hot minutes after the PC is turned on, the temp never goes down, even if the machine is idling. 
I updated Nvidia drivers,  installed sensors and powertop, but cannont figure out what is causing the instant load. Here is the output of both:
sensors:
(The machine was playing music for 20 minutes before getting the output, it is ususally 70 after reboot)
> acpitz-virtual-0
Adapter: Virtual device
temp1:        +94.0°C  (crit = +127.0°C)
temp2:        +94.0°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +92.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:       +92.0°C  (high = +100.0°C, crit = +100.0°C)

powertop - Overview:

> 
 Usage       Events/s    Category       Description
            100.0%                      Device         Audio codec hwC0D0: SigmaTel
              1.9 ms/s      87.1        Interrupt      [6] tasklet(softirq)
             60.2 µs/s      27.4        kWork          ieee80211_iface_work
            160.9 µs/s      15.7        Timer          tick_sched_timer
            258.7 µs/s       9.8        Interrupt      [23] ehci_hcd:usb2
            168.6 µs/s       9.8        Process        syndaemon -i 2.0 -K -R -t
             67.1 µs/s       8.8        Timer          hrtimer_wakeup
             43.4 µs/s       8.8        Process        [RTKTHREAD]
             12.9 ms/s       2.9        Process        powertop
            361.2 µs/s       4.9        Process        /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background no
              0.0 µs/s       3.9        kWork          BlinkWorkItemCallback
              2.0 ms/s       2.0        Process        unity-2d-shell
            140.0 µs/s       2.0        Process        /usr/lib/gnome-settings-daemon/gnome-settings-daemon
            370.0 µs/s       1.0        Process        NetworkManager
            318.4 µs/s       1.0        Process        dbus-daemon --system --fork --activation=upstart
            149.5 µs/s       1.0        Process        /usr/lib/ubuntu-geoip/ubuntu-geoip-provider
            137.9 µs/s       1.0        Process        /usr/lib/telepathy/mission-control-5
            123.2 µs/s       1.0        Process        sshd: deckoff@pts/0
             81.2 µs/s       1.0        Process        /usr/lib/accountsservice/accounts-daemon
             74.6 µs/s       1.0        Process        /usr/lib/unity-lens-applications/unity-applications-daemon
             66.1 µs/s       1.0        Process        /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0
             61.0 µs/s       1.0        Process        zeitgeist-datahub
             58.2 µs/s       1.0        Process        nautilus -n
             30.2 µs/s       1.0        Process        /usr/lib/gvfs/gvfs-afc-volume-monitor
             12.5 µs/s       1.0        kWork          flush_to_ldisc
             12.1 µs/s       1.0        Timer          watchdog_timer_fn
              4.9 µs/s       1.0        Process        [watchdog/1]
              4.5 µs/s       1.0        Process        [watchdog/0]
              1.5 ms/s       0.0        Interrupt      [16] nvidia
              0.9 ms/s       0.0        Interrupt      [47] iwl3945
            382.9 µs/s       0.0        Process        [migration/1]
            269.4 µs/s       0.0        Interrupt      [16] yenta
            263.9 µs/s       0.0        Process        nm-applet
            249.1 µs/s       0.0        Interrupt      [0] timer/0



Idle stats:

> 

          Package   |             CPU 0
POLL        0.0%    | POLL        0.0%    0.0 ms
C1          0.0%    | C1          0.0%    0.0 ms
C2          0.0%    | C2          0.0%    0.0 ms
C3         99.3%    | C3         99.2%    6.7 ms

                    |             CPU 1
                    | POLL        0.0%    0.0 ms
                    | C1          0.0%    0.0 ms
                    | C2          0.0%    0.3 ms
                    | C3         99.5%    6.6 ms



Frequency stats:

> 
            Package |            CPU 0
Turbo Mode   0.3%   | Turbo Mode   0.3%
2.00 Ghz     0.0%   | 2.00 Ghz     0.0%
1.60 Ghz     0.0%   | 1.60 Ghz     0.0%
1200 Mhz     0.0%   | 1200 Mhz     0.0%
 800 Mhz     0.0%   |  800 Mhz     0.0%
Idle        99.7%   | Idle        99.7%

                    |            CPU 1
                    | Turbo Mode   0.0%
                    | 2.00 Ghz     0.0%
                    | 1.60 Ghz     0.0%
                    | 1200 Mhz     0.0%
                    |  800 Mhz     0.0%
                    | Idle       100.0%

 

Device Stats
> 
              Usage     Device name
              0.9%        CPU use
            100.0%        Audio codec hwC0D0: SigmaTel
            513.4 pkts/s  Network interface: wlan0 (iwl3945)
            132.3 pkts/s  Network interface: wlan1 (rtl8192cu)
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1
            100.0%        PCI Device: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection
            100.0%        PCI Device: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3
            100.0%        Radio device: iwl3945
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2
            100.0%        PCI Device: Texas Instruments PCIxx12 Cardbus Controller
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1
            100.0%        PCI Device: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
            100.0%        PCI Device: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode]
            100.0%        PCI Device: NVIDIA Corporation G86 [GeForce 8400M GT]
            100.0%        USB device: UHCI Host Controller
            100.0%        USB device: UHCI Host Controller
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5
            100.0%        USB Device: usb-device-05ca-183b
            100.0%        USB device: 802.11n WLAN Adapter (Realtek)
            100.0%        USB device: EHCI Host Controller
            100.0%        USB device: EHCI Host Controller
            100.0%        USB device: UHCI Host Controller
            100.0%        USB device: UHCI Host Controller
            100.0%        PCI Device: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port
            100.0%        PCI Device: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller
            100.0%        USB device: UHCI Host Controller
            100.0%        PCI Device: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
            100.0%        PCI Device: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2



Please, help me fix it :):)

---

### Post by deckoff on 2012-11-21
Bump?

---

### Post by ahallubuntu on 2012-11-21
What version of Ubuntu are you using?  Does it get hot even if not in Ubuntu (is Windows still an option)?  What about if just sitting in BIOS Setup?

This is an older laptop.  Have you cleaned out the CPU fan and heat sink?  These can get clogged with dust and dirt and prevent the CPU from being properly cooled.  On some laptops, it's pretty easy to get to the fan, remove it and clean the area out (I use a vacuum with an attachment, careful not to suck up the little screws!).  On others it's a pain to get to the CPU and fan - you have to remove the keyboard etc and that can be tedious and time consuming to avoid breaking something.  You can try a "hail mary" and try vacuuming from the outside of the laptop on the fan area that blows out or blowing in with a can of compressed air.

Are you sure the CPU fan is even running?  Can you hear it?

---

### Post by ahallubuntu on 2012-11-21
...and if you clean it out and get it running cooler, if you find out where the Intel internal wireless card is, consider replacing it in the future with an "N" card so you can get rid of that little USB wireless N dongle.  You can get an Intel 5100 wireless N card (full height not half height is what you need) for about $10 USD used on eBay.  Once you can get to the card, it's very easy to swap: pop off the two antenna wires, unscrew it, put the new card in. 

Get a full-height 5100 - any version will probably work EXCEPT an HP, IBM, or Lenovo version of the card.  A Sony, Toshiba, or Dell card should work fine.  Don't get a new one from Asia - get a used one.

---

### Post by Linuxisfast on 2012-11-21
Add the xswat ppa and get the latest nvidia driver. Also as the previous poster suggests, do a thorough cleaning of your laptop.

---

### Post by deckoff on 2012-11-22
Thanks for the answers. I use Ubuntu 12.04, the laptop is windows free ;) Only standard updates were applied, kernel is 3.2.0-32-generic-pae.
I use the PC mainly for XBMC player. 
Nvidia driver is nvidia_173_updates, installed via the Additional drivers dialog. Will the ppa provide "better drivers", or it is up to try and see. I have some experimental drivers listed in this window, but when i installed them, the pc was not able to log into GUI, had to uninstall everything nvidia via tty, and install these drivers again. 
What is wrong with new far Asia wireless cards, low quality?

---

### Post by ahallubuntu on 2012-11-22
> **deckoff said:**
> What is wrong with new far Asia wireless cards, low quality?

I have ordered several of the Intel wireless cards from China and Hong Kong that are advertised as "new."  But the cards that I got either were not the exact model advertised or did not work.  On eBay, sellers seem to give refunds quickly if you are persistent about problems with their products, but I just haven't found it worth the hassle.  Here in the US, it's easy to find used wireless cards cheaply.  Not sure about Bulgaria.  Maybe buying from China or Hong Kong is a better for you and hope your luck is better than mine!

---

### Post by deckoff on 2012-11-24
Hm, I found a Toshiba version for 10$ with shipping to Bulgaria, so no problems with finding one. :) I couldn't find where the actual card of the PC is located now, is it between the keyboard and the motherboard? I removed the lower cover but could not locate it there:)

---

