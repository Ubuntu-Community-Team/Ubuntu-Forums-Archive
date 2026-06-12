---
title: "vostro 2420 boots at full brightness"
date: 2013-09-21
forum: Hardware
---

### Post by handysmurf on 2013-09-21
Is there an equivelant to config.sys (or any method) where i can set the brightness level by default instead of having to manually set it each boot?:confused:

---

### Post by Toz on 2013-09-22
Hello and welcome to the forums.

Yes there is (/etc/rc.local), but knowing what to put in there is a little more difficult. 
Can you provide us with some more informtion:

1. What video card/driver are you using? Open a terminal window, type the following command and post back the results:
```
lspci -k | grep -A3 VGA
```

2. What backlight interfaces do you have?
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

### Post by handysmurf on 2014-01-19
lspci -k | grep -A3 VGA

 (no response.)

 

 for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
 /sys/class/backlight/acpi_video()
 ()
 cat: /actual_brightness; No such file or directory
 15

 /sys/class/backlight/intel_backlight
 306
 cat: /actual_brightness; No such file or directory

 4882

 
user@user bash > bash2.txt
(was unable to locate "bash2.txt")

I couldn't "cut and paste", had to type what i saw, hope this helps

---

### Post by Toz on 2014-01-19
> **4ysH7XQ said:**
> lspci -k | grep -A3 VGA

 (no response.)
??? No video card? This doesn't make sense. Can you post back the complete listing of:
```
lspci -k
``` 

>  for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
 /sys/class/backlight/acpi_video()
 ()
 cat: /actual_brightness; No such file or directory
 15

 /sys/class/backlight/intel_backlight
 306
 cat: /actual_brightness; No such file or directory

 4882
This doesn't make sense either. What flavour and version of ubuntu are you using?

 
> user@user bash > bash2.txt
(was unable to locate "bash2.txt")

I couldn't "cut and paste", had to type what i saw, hope this helps
Don't use this command - it won't work. Open a terminal window, click+drag to highlight the command that I've posted, then middle-button-click (or both-button-click) in the terminal window and it will copy/paste the command.

---

### Post by handysmurf on 2014-01-19
ubuntu 11.10 on a dell vostro 2420 laptop, am total newbie.

didn't have any luck with the (both) click paste either.

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Dell Device 0556
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Dell Device 0556
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
    Subsystem: Dell Device 0556
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
    Subsystem: Dell Device 0556
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
    Subsystem: Dell Device 0556
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 6 (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
    Subsystem: Dell Device 0556
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
    Subsystem: Dell Device 0556
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA AHCI Controller (rev 04)
    Subsystem: Dell Device 0556
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
    Subsystem: Dell Device 0556
    Kernel modules: i2c-i801
07:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
    Subsystem: Dell Device 0209
    Kernel driver in use: ath9k
    Kernel modules: ath9k
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)
    Subsystem: Dell Device 0556
    Kernel driver in use: r8169
    Kernel modules: r8169
```

---

### Post by Toz on 2014-01-19
Which of the following sets of commands adjust the brightness:
```
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...OR:
```
echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

And, for whichever set does change the brightness, try playing around with the value until you get the brightness that you would like at startup. Then post back the information.

BTW, 11.10 has reached EOL and is no longer being supported. You should consider upgrading.

---

### Post by handysmurf on 2014-01-20
echo X | sudo tee /sys/class/backlight/acpi_video0/brightness
when i use "0" i get full dim,
when i use "15" i get full bright,           "2" is where i'd like to boot.

echo 2441, or 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness...
Either one made the screen go black, and I had to use the keyboard function key to recover.


also... what i'm reading about upgrading, says: To upgrade from Ubuntu 11.10 on a desktop system, start "Update  Manager". It should display the following message: "New distribution  release '12.04' is available. Click Upgrade and follow the on-screen  instructions"...

        update manager shows "your system is up-to-date", and below the window it says "there are no updates to install"

"notify me of a new ubuntu version:" is set to: "for long-term support version"

also... i'm not using a mouse, only my laptop's touchpad...  can i "paste" in "terminal" with that?

---

### Post by Toz on 2014-01-20
> **4ysH7XQ said:**
> i don't understand, should i copy and enter each line seperately in terminal, and see what happens?
Yes. Copy/paste or type in directly. What you are looking for is to see which of those commands actually change your brightness level. When we figure that out and what brightness level you want, we can enter it into /etc/rc.local so that it is automatically set on each boot.

> also... what i'm reading about upgrading, says: To upgrade from Ubuntu 11.10 on a desktop system, start "Update  Manager". It should display the following message: "New distribution  release '12.04' is available. Click Upgrade and follow the on-screen  instructions"...

        update manager shows "your system is up-to-date", and below the window it says "there are no updates to install"

"notify me of a new ubuntu version:" is set to: "for long-term support version"
Probably best to create a new thread for upgrading your system.

> also... i'm not using a mouse, only my laptop's touchpad...  can i "paste" in "terminal" with that?
Does the touchpad have any buttons? If you select the text then both-button press at the same time in the terminal window, it should past the selected text.

---

### Post by handysmurf on 2014-01-21
Results are:
echo X | sudo tee /sys/class/backlight/acpi_video0/brightness
when i use "0" i get full dim,
when i use "15" i get full bright,           "2" is where i'd like to boot.

echo 2441, or 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness...
Either one made the screen go black, and I had to use the keyboard function key to recover.

---

### Post by Toz on 2014-01-21
> **4ysH7XQ said:**
> Results are:
echo X | sudo tee /sys/class/backlight/acpi_video0/brightness
when i use "0" i get full dim,
when i use "15" i get full bright,           "2" is where i'd like to boot.


Here is what you need to do to make it start at that brightness at startup:

1. Open the /etc/rc.local file for editing with root privileges:
```
sudo -i gedit /etc/rc.local
```

2. Enter the following line _above_ the *"exit 0"* line:
```
echo 2 > /sys/class/backlight/acpi_video0/brightness
```

3. Save the file and reboot to test.

---

### Post by handysmurf on 2014-01-22
Perfect!  Just what I wanted.  Thank you ever so much Toz.  I appreciate your patience, and time.

Now is there some way I can shorten this thread before I mark it as "solved", so the "meat" of the subject is promenent or what should I do next?

---

### Post by Toz on 2014-01-22
Best to just leave the thread as it is - no need to shorten the content. To mark it "Solved", use the Thread Tools link above.

---

