---
title: "Disable Bluetooth Howto Needed"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by perun on 2007-04-24
I have a Sony SZ330 and I want to maximize my battery life. I'm trying to figure out the best way to disable the bluetooth hardware temporarily (bash script would be ideal) similar to how windows turns it off by disabling the hardware (I believe...) and be able to restart on demand with a similar script. Any ideas?

---

### Post by mikej_96 on 2007-04-24
it would be really sweet to be able to do this. I have a Sony Z520a and was wonding the exact same thing.

---

### Post by deeproot on 2007-04-24
I dont use bluetooth but I think you can disable it in System > Administration > Services 
Just uncheck bluetooth.

On my laptop my fucntion keys still work just as they do in windows and i can turn my wireless off with a keystroke.  But i'm guessing that is not working with yours as it doesnt with  my other laptop.

Deep

---

### Post by perun on 2007-04-24
I have a switch for Wifi that turns that off, which works fine, but basically I want to turn off the bluetooth hardware (which is still on according to my bluetooth notification light when I disable the service). It sounds like I need to make linux forget about what the hardware is.

---

### Post by mikej_96 on 2007-04-27
On my Dell Insprion 6400 laptop you can disable bluetooth in the bios, or there is also an option in the bios to make the wireless switch only work for bluetooth. This way you can keep wireless on but toggle buletooth off and on. The only problem with this is that the switch can no longer toggle off the wireless. 
Also, I unchecked bluetooth in the System > Administration > Services before I did this. Im not sure if it will hang on boot up if you leave it checked. 

This is my solution to save on battery life, but I do wish there was a way to enable and disable it like in Windows.

---

### Post by jvpgomes on 2007-05-29
This is a problem. Specially if your computer has a button that enables or disables both the wireless card and the bluetooth. The problem is how to enable, for example, the wireless card and disable the bluetooth.

To stop the bluetooth process is not enough. The bluetooth deviced will still works. It can be detected by other else bluetooth device... so obviously, physically it's still working.

My suggestion is:

$ hciconfig 
hci0:   Type: USB
        BD Address: 00:10:C6:98:C6:24 ACL MTU: 377:10 SCO MTU: 16:0
        UP RUNNING PSCAN ISCAN 
        RX bytes:650 acl:0 sco:0 events:17 errors:0
        TX bytes:316 acl:0 sco:0 commands:17 errors:0

$ sudo hciconfig -a hci0 down
$ 

I hope it helps...

---

### Post by dreadlocks1221 on 2007-09-17
I have an HP laptop and through all the trouble I had installing Ubuntu I installed it with the alternate CD, no when I try to boot it up it stalls when it tries to start blue tooth. Is there a way to turn it off with a boot command?

---

### Post by wieman01 on 2007-09-17
Would that help?

You need to install a tool called "spictrl". 
> sudo apt-get install spicctrl
> sudo modprobe sonypi
> gksudo gedit /etc/modules
Now add this at the bottom of the file:
> [COLOR="Red"]sonypi[/COLOR]
Now turn off the Bluetooth device:
> sudo spicctrl -l 0
If you need a startup script for turning it off at boot, let me know. I set on up for you.

---

### Post by dreadlocks1221 on 2007-09-17
Yes I would like a boot time one because without it I cant boot into Ubuntu to add those commands

Thanks in Advance

---

### Post by Nuafite on 2007-12-03
> **dreadlocks1221 said:**
> Yes I would like a boot time one because without it I cant boot into Ubuntu to add those commands

Thanks in Advance

I managed to install Gutsy by inserting fb=false into the menu (hit F6). 

However, when I try to boot, the splash screen starts and gets to the last bar, when it goes to a black screen which ends *Starting Bluetooth services. 

I've tried all the solutions
> noapic nolapic noapci noirqpoll noirqdebug nosmp

and even 
> “noapic” or acpi_os_name=”Windows 2006&#8243; which a kind commenter left on my Ubuntu Learner blog. 

And I know I've tried 31 times to boot, as a system check was forced!

[Ubuntu Tutorials ]("http://ubuntu-tutorials.com/2007/11/24/disable-bluetooth-on-ubuntu-710/") has a how-to disable Bluetooth, but as I need to get to the desktop first (?)
it's a catch-22.
I'm trying to dual-boot with Windows Vista Ultimate at the moment. 
My notebook  is a 

HP Pavillion dv6558ea
Intel Dual Core
120Gb hdd
2Gb Ram
Intel PRO/Wireless 3945a/b/g 802.11 a/b/g WLAN & Bluetooth
Intel Graphics Media Accelerator X3100 with shared graphics Memory

Any help greatly appreciated.

---

