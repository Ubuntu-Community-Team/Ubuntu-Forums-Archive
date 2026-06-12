---
title: "Computer Keeps Freezing"
date: 2008-08-26
forum: General Help
---

### Post by Dodge Meadows on 2008-08-26
Ubuntu 8.04
For a while now, my computer keeps freezing up and I have to manually reset it to get it to work again.   
When it does freeze, the CAPS button and the Scroll lock button lights start flashing. It seems to be at random times, sometimes even before I can log in.

---

### Post by Crafty Kisses on 2008-08-26
> **Dodge Meadows said:**
> For a while now, my computer keeps freezing up and I have to manually reset it to get it to work again.   
When it does freeze, the CAPS button and the Scroll lock button lights start flashing. It seems to be at random times, sometimes even before I can log in.

Post the output of > top

---

### Post by Dodge Meadows on 2008-08-26
> **Codename said:**
> Post the output of > top

What?  I'm kind of new at this, did I do something wrong?

---

### Post by phidia on 2008-08-26
Open a terminal from Applications >Accessories >Terminal and enter > top maybe > ps too.

---

### Post by Dodge Meadows on 2008-08-26
So once I do that, post all the stuff that comes up?  Lots of it keeps changing.
Well in case it helps, this is what it was. 

top - 16:54:04 up 13 min,  2 users,  load average: 1.06, 0.45, 0.27
Tasks: 119 total,   2 running, 117 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  0.3%sy,  0.0%ni, 98.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2066420k total,   635848k used,  1430572k free,    25152k buffers
Swap:  4803392k total,        0k used,  4803392k free,   258448k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2516 root      15  -5     0    0    0 S    1  0.0   0:00.02 kjournald          
 5386 root      20   0  387m  38m 7992 S    1  1.9   0:50.61 Xorg               
 5716 dodge     20   0 28488 5740 3312 S    1  0.3   0:00.77 pulseaudio         
 5733 dodge     20   0 15208 2596 1728 S    1  0.1   0:00.56 gnome-screensav    
 6384 dodge     20   0  2308 1120  852 R    1  0.1   0:01.44 top                
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.40 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.02 kblockd/0

---

### Post by Borj2 on 2008-08-26
Bump. 

Exact same thing happens to me, (8.04, 2.6.24-19-generic) caps and scroll lock flash and the mouse is frozen. REISUB doesn't work either. Using an old Dimension 4700, Nvidia 6600 128mb using the generic restricted drivers, 2.5GB RAM. The lockups are fairly random.

I had this problem once before, I temporarily fixed it by re-installing the os. It has been approximately two weeks since then. The only program that has been running during every crash is Skype, which I highly doubt is the cause. I can provide a lot of speculative information, but to me it seems more coincidental that causal.

EDIT: Could it be temperature-related? The interval between crashes after the first crash seems to shorten after every reboot until the system is completely inaccessible, at which point I have to leave it alone for a while until i can use it again...

---

### Post by Dodge Meadows on 2008-08-27
I thought of that, but it sometimes will still freeze after being off for a while.  I don't think it is because of the temperature.  

My hard drive is missing both the screws that hold it in, but I don't think that is the problem.  Apparently I have been missing them for some time now, but I have never taken them out, so I don't know how they got lost in the first place.

---

### Post by Dodge Meadows on 2008-08-27
Aug 27 16:26:29 dodge-laptop dhcdbd: Started up.
Aug 27 16:26:30 dodge-laptop kernel: [   29.190179] Bluetooth: Core ver 2.11
Aug 27 16:26:30 dodge-laptop kernel: [   29.190332] NET: Registered protocol family 31
Aug 27 16:26:30 dodge-laptop kernel: [   29.190337] Bluetooth: HCI device and connection manager initialized
Aug 27 16:26:30 dodge-laptop kernel: [   29.190344] Bluetooth: HCI socket layer initialized
Aug 27 16:26:30 dodge-laptop kernel: [   29.265117] Bluetooth: L2CAP ver 2.9
Aug 27 16:26:30 dodge-laptop kernel: [   29.265126] Bluetooth: L2CAP socket layer initialized
Aug 27 16:26:30 dodge-laptop kernel: [   29.339150] Bluetooth: RFCOMM socket layer initialized
Aug 27 16:26:30 dodge-laptop kernel: [   29.339167] Bluetooth: RFCOMM TTY layer initialized
Aug 27 16:26:30 dodge-laptop kernel: [   29.339169] Bluetooth: RFCOMM ver 1.8
Aug 27 16:26:34 dodge-laptop kernel: [   32.958816] [drm] Initialized drm 1.1.0 20060810
Aug 27 16:26:34 dodge-laptop kernel: [   32.962209] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 27 16:26:34 dodge-laptop kernel: [   32.962312] [drm] Initialized i915 1.6.0 20060119 on minor 0
Aug 27 16:26:58 dodge-laptop kernel: [   57.454097] NET: Registered protocol family 10
Aug 27 16:26:58 dodge-laptop kernel: [   57.455126] lo: Disabled Privacy Extensions
Aug 27 16:26:58 dodge-laptop kernel: [   57.457316] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 27 16:26:58 dodge-laptop kernel: [   57.458819] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 27 16:27:08 dodge-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Aug 27 16:27:11 dodge-laptop kernel: [   69.788426] NET: Registered protocol family 17
Aug 27 16:27:19 dodge-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Aug 27 16:27:26 dodge-laptop kernel: [   84.660627] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 27 16:27:30 dodge-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Aug 27 16:27:30 dodge-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Aug 27 16:27:30 dodge-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Aug 27 16:27:30 dodge-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Aug 27 16:29:52 dodge-laptop syslogd 1.5.0#1ubuntu1: restart.

---

