---
title: "Acer C110 Tablet Buttons not Working"
date: 2010-01-16
forum: Hardware
---

### Post by korokinopio on 2010-01-16
I have an Acer TravelMate C110 series Tablet PC. I love it, it runs about as fast as most UMPCs and netbooks, and has the proper tablet functionality. How ever, there are a few bugs in the system that I would like to work out. Primarily, the tablet buttons on the edge of the screen do not work. I am running it with Ubuntu 9.10, and most everything works as desired, except these tablet buttons.

*NOTE* these are the five buttons that are located around the bottom right corner of the screen (when open in clamshell mode) not the five located above the keyboard.

These five buttons provided much functionality in Windows (ie, rotating the screen, page up, page down, lock screen, etc) and it would be nice to have some functionality back (I would be content with just pg up and pg dn).

Some of the research that I did online said that these buttons just acted as keyboard events, however, they don't show anything when i run 
```
xev
```
so I don't believe that they are keyboard events.

The only other information I can find suggests that they are ACPI controlled events.

Most of the research that I've done makes me think that people are just ignoring these buttons all together. Nobody ever seems to mention them at all.

I've installed 
```
acerhk
```
but that only appears to run the buttons above the keyboard.

My
```
acpitools -e
```
output is as follows

```
  Kernel version : 2.6.31-18-gener20090521   -    ACPI version : 20090521
  -----------------------------------------------------------
  Battery #1     : present
    Remaining capacity : 0 mAh, 0.00%, 03:30:07
    Design capacity    : 1800 mAh
    Last full capacity : 1800 mAh
    Present rate       : 514 mA
    Charging state     : charging
    Battery type       : rechargeable, LION
    Model number       : ANA
    Serial number      : 110

  AC adapter     : on-line 
  Fan            : <not available>

  CPU type               : Intel(R) Pentium(R) III Mobile CPU       800MHz 
  Min/Max frequency      : 400/800 MHz
  Current frequency      : 800 MHz
  Frequency governor     : performance 
  Freq. scaling driver   : speedstep-smi 
  Cache size             : 512 KB
  Bogomips               : 1596.66 
  Processor ID           : 0
  Bus mastering control  : yes
  Power management       : yes
  Throttling control     : no
  Limit interface        : no
  Active C-state         : C0
  C-states (incl. C0)    : 3
  Usage of state C1      : 42933253 (99.2 %)
  Usage of state C2      : 337944 (0.8 %)

  Thermal zone 1 : ok, 45 C
  Trip points : 
  ------------- 
  critical (S5):           97 C

  Thermal zone 2 : ok, 44 C
  Trip points : 
  ------------- 
  critical (S5):           82 C


   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. OBLN	  S5	 disabled  pci:0000:00:04.0
  2. OZ68	  S3	 disabled  pci:0000:00:03.0
  3. OBMO	  S3	 disabled  pci:0000:00:00.2
  4. LID	  S3	*enabled   
```

I wonder if those three devices at the bottom that appear to be disabled have anything to do with this.

Any help with this would be greatly appreciated.

Thanks

---

### Post by bpb_21 on 2010-03-05
Hey - I've got the same C110 laptop; same great reviews of it, and same problems with the buttons at the side of the screen.  I haven't found any answers just yet, and I hate to mess with the native functionality in 9.10, but I'm also looking at this issue.  Let me know if you find anything.

---

### Post by korokinopio on 2010-03-05
Is your ```
acpitools -e
``` output the same as mine? is there anything else you've been able to try?

---

### Post by bpb_21 on 2010-03-05
My output is a little different (slightly) from yours; I take it you've got the C100 model.  (If you've got a PIII processor you do; I had one of those and recently got the C110 model).

```

 Kernel version : 2.6.31-20-gener20090521   -    ACPI version : 20090521
  -----------------------------------------------------------
  Battery #1     : present
    Remaining capacity : 1638 mAh, 91.00%
    Design capacity    : 1800 mAh
    Last full capacity : 1800 mAh
    Present rate       : unknown
    Charging state     : charging
    Battery type       : rechargeable, Lion
    Model number       : Bat 4Cell
    Serial number      : 236

  AC adapter     : on-line 
  Fan            : <not available>

  CPU type               : Intel(R) Pentium(R) M processor  900MHz 
  Min/Max frequency      : 600/900 MHz
  Current frequency      : 600 MHz
  Frequency governor     : ondemand 
  Freq. scaling driver   : acpi-cpufreq 
  Cache size             : 1024 KB
  Bogomips               : 1200.11 
  Processor ID           : 0
  Bus mastering control  : yes
  Power management       : yes
  Throttling control     : yes
  Limit interface        : yes
  Active C-state         : C0
  C-states (incl. C0)    : 4
  Usage of state C1      : 81368 (17.9 %)
  Usage of state C2      : 343415 (75.5 %)
  Usage of state C3      : 29982 (6.6 %)
  T-state count          : 8
  Active T-state         : T0


  Thermal zone 1 : ok, 36 C
  Trip points : 
  ------------- 
  critical (S5):           98 C
  passive:                 65 C: tc1=2 tc2=5 tsp=300 devices=CPU0 

  Thermal zone 2 : ok, 41 C
  Trip points : 
  ------------- 
  critical (S5):           83 C
  passive:                 58 C: tc1=2 tc2=5 tsp=300 devices=CPU0 


   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID	  S3	*enabled   
  2. LANC	  S5	 disabled  pci:0000:02:08.0
  3. MODM	  S3	 disabled  pci:0000:00:1f.6

```

I'm thinking of looking around on the Acer site for info on various similar models (the C100 and C110 look almost exactly the same, and function about the same as well) and see if there are any drivers for other models' screen buttons.  I didn't see any for the C100 or C110.

There may be some info for this setup searching for the wacom (I think) packages, but I didn't delve into that too much due to the overall good out-of-the-box support with 9.10.

---

### Post by bpb_21 on 2010-03-05
One reason I haven't done anything just yet is that 9.10 supports the stylus and touchscreen out-of-the-box.  But, as you posted earlier, those buttons on the side of the screen do seem to be mapped/mappable to keyboard events.  I came across this post at [http://stefan.dnsalias.net/howto/c110.html](http://stefan.dnsalias.net/howto/c110.html)

> 
Now we have to setup the serial port information during boot. While we are at it we will make some of those little buttons at the bottom-right of the display useful. The up and down arrow keys will be mapped to, guess what, up and down arrow. We'll also map the display Fn button to Scroll Lock; Yes, it's odd but there is a method to my madness.

Use your favorite text editor and sudo to append the following to /etc/init.d/rc.local.

Code:
setserial /dev/ttyS0 port 0x06f8 irq 6 autoconfigure
# Screen Fn to Scroll Lock
setkeycodes 6b 78
# Arrow 1 = Scroll up
setkeycodes 68 108
# Arrow 2 = Scroll down
setkeycodes 69 103
On my install I had some weirdness in my /etc/X11/xorg.conf. There are three InputDevice sections dealing with wacom tablets. All of them pointed to /dev/wacom, which didn't exist. I'm lazy, to work around this I just pointed them directly to the serial port. If you have this issue just replace the three lines that contain /dev/wacom with the following:

Code:
Option "Device" "/dev/ttyS0"
At this point we should tweak the stylus settings a bit. A regular button numbering on a three button mouse goes 1 2 3 from left to right. The wacom stylus has two "buttons" tap (left click,) and button-tap (middle click.) I don't know about you, but not having right click ability with the stylus is akin to having to having a car with only two wheels. We can fix this by changing the sylus button ordering using xinput and putting it into the XFCE autostarted application list. Click Applications, Settings, Autostarted Applications. Click the add button. Enter a name and description (StylusFix/Stylus Button Remapping) and enter the following into the command box:

Code:
xinput set-button-map stylus 1 3 2 4
After this I would reboot to do a sanity check. When you hit the GDM login screen move mouse around with the trackpad, then the stylus. Hopefully both should work and we can continue.


Then again, this was considering an install of xubuntu 6.06 along with the wacom utilities directly before this quote.  I don't know how "enabling" screen rotation (from the laptop's point of view) would affect keyboard mapping of those screen keys but I don't really mind/need the screen rotation thing so I'm not worried about it.

Where he speaks of the serial port, I've got an option in my BIOS (most up to date version) to enable/disable/auto the serial port and set it in either FIR or External COM mode.  I'm not sure how this works with the instructions above.

Anyway, something to think about/experiment with if you haven't already seen it.

---

### Post by bpb_21 on 2010-03-05
I just got the buttons on the side of the screen working!  From my post above, taking the directions from [http://stefan.dnsalias.net/howto/c110.html](http://stefan.dnsalias.net/howto/c110.html)
I was able to follow these directions and now the scroll buttons on the side of the screen work perfectly!
> 
Now we have to setup the serial port information during boot. While we are at it we will make some of those little buttons at the bottom-right of the display useful. The up and down arrow keys will be mapped to, guess what, up and down arrow. We'll also map the display Fn button to Scroll Lock; Yes, it's odd but there is a method to my madness.

Use your favorite text editor and sudo to append the following to /etc/init.d/rc.local.

Code:
setserial /dev/ttyS0 port 0x06f8 irq 6 autoconfigure
# Screen Fn to Scroll Lock
setkeycodes 6b 78
# Arrow 1 = Scroll up
setkeycodes 68 108
# Arrow 2 = Scroll down
setkeycodes 69 103

I just did a copy & paste of his Code directly into the bottom of my /etc/init.d/rc.local file and saved it.  So I can confirm that works in 9.10 and not just 6.10 as that post was written for.
Give it a try; I'm really glad to have those scroll buttons working - even if the screen isn't swapped around!

---

### Post by korokinopio on 2010-03-06
WOW!

I've looked all over the place for something like that. I'll give it a good solid try sometime when I have a chance (a little busy right now) and Once I get the system working properly, I'll make a post about how to get it working properly with 9.10 (or 10.04 depending on when i get a chance to do it). if there was anything you wanted to add, once it's done, let me know.

---

### Post by bpb_21 on 2010-03-06
I'd like to get a list of the codes for the various buttons that can be mapped to the screen buttons.  In the code quoted that article has:
```

# Screen Fn to Scroll Lock
setkeycodes 6b 78
# Arrow 1 = Scroll up
setkeycodes 68 108
# Arrow 2 = Scroll down
setkeycodes 69 103

```
I wonder where a reference is for the "6b", "78", "68", etc. that corresponds to the keys.  If I could map one of the screen buttons to a "right click" event, that would take care of everything I need for the tablet mode.

---

### Post by korokinopio on 2010-03-07
you don't have right click on the stylus button either then? I was actually about to ask you if you did.

---

### Post by horstho on 2010-09-11
Found the other codes by trial and error...

just added:
#the key-symbol is 6c where 103 is just once again cursor down
setkeycodes 6c 103
#the circle with the point in the center is 67 where 28 = Return
setkeycodes 67 28

---

