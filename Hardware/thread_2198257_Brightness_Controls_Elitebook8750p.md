---
title: "Brightness Controls Elitebook8750p"
date: 2014-01-07
forum: Hardware
---

### Post by Linux-sgt on 2014-01-07
Hello all. I have been using my laptop with Debian and OpenSUSE for some time, but I decided to switch things over to Ubuntu. Here is my dillema: the brightness controls - both function keys and system setting adjustment - does not allow for any brightness controls. The controls worked perfectly in Deb and OpS so it shouldn't be a hardware issue with Linux. I figured I would kindly ask for some pointers on getting this solved.    Here are some specifics of my computer:             
 
          **KERNEL**: vmlinuz-3.11.0-15-generic                     
 
 **HARDWARE**:    VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller]) 	     Subsystem: Hewlett-Packard Company Device [103c:17a7] 	   
   Flags: bus master, fast devsel, latency 0, IRQ 50 	  
   Memory at d4000000 (64-bit, non-prefetchable) [size=4M] 	   
 Memory at c0000000 (64-bit, prefetchable) [size=256M] 	
    I/O ports at 4000 [size=64] 	
  Expansion ROM at  [disabled] 	  
  Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit- 	Capabilities: [d0] Power Management version 2 	     
 Capabilities: [a4] PCI Advanced Features 	     
 Kernel driver in use: i915 00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])                
 
   **BACKLIGHT SETTINGS**:   $i/max_brightness; done /sys/class/backlight/acpi_video0 100 100 /sys/class/backlight/intel_backlight 3315            
 
  **DMESG LOGFILE**: [http://paste.ubuntu.com/6712573/](http://paste.ubuntu.com/6712573/)      
 
      Thanks in advance for any help, Jay

---

### Post by Toz on 2014-01-07
Lets try for the quick-fix first (before delving deeper).

With root privileges, create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...log out and in again to test.

The reason I'm thinking this might work is that you have two backlight interfaces (acpi_video0 and intel_backlight) and the system is confusing them. The above code (only valid for kernel versions 3.9 or higher), will direct the system to use the intel_backlight interface.

_Note:_ if for some reason the system doesn't return to a graphical screen afterwards, simply delete that file from a virtual console (Ctrl+Alt+F1) and reboot.


[I]
Another option to remove one of the interfaces is to use the **acpi_backlight=vendor** kernel parameter which will remove the acpi_video0 interface leaving only the intel_backlight one thus eliminating the confusion. 

But lets try the easier first version first.[/I]

---

### Post by Linux-sgt on 2014-01-08
Thank you very much! That did the trick wonderfully.  Jay

---

