---
title: "Wireless mouse for laptop"
date: 2009-04-17
forum: Hardware
---

### Post by ufarmer on 2009-04-17
I am trying to get a wireless USB mouse (Logitech LX8 ) to work with Ubuntu 8.10 on my laptop.  I'll be happy just to get the right  and left buttons and the scroll wheel working.

Any advice is appreciated.

---

### Post by labinnsw on 2009-04-17
Did you plug it in after or before starting up? What have you tried so far.

---

### Post by ufarmer on 2009-04-18
I plugged it in, noticed that it wasn't fully functional, and rebooted.  This didn't improve the behaviour.  I edited the xorg.conf file according to a suggestion that I found googling the problem but this had no effect.  So far that's all I've done.

---

### Post by coffeeaddict22 on 2009-04-18
Hi,
Have you tried plugging it into another PC?  I've had a couple of Logitech mice, and they've always worked out of the box (I gave up a few months back and bought a Bluetooth mouse to stop me knocking the receiver).  If it's working on another PC (or even better on the same PC, another USB port), then there are a couple of things you can try.

lsusb may give you enough information to figure out the problem.  however, I suspect xinput is the command that is your friend here.  
Start with ```
xinput list --short
```
That should give you the name of the mouse; then type in ```
 xinput list-props "xxxxxxxx"
```
replacing the x's with the name that came up.  that'll provide you with some info on what the kernel thinks your mouse can do.

xinput can also be used to configure the mouse, but probably best to start at the beginning...

---

### Post by labinnsw on 2009-04-18
Was [this]("http://ubuntuforums.org/showthread.php?t=684843") the post you used? *In particular entry #18*

---

### Post by ufarmer on 2009-04-18
Here is the output from xinput list-props:

```
>> xinput list-props "Logitech USB Receiver"
Device 'Logitech USB Receiver':
	Device Enabled:		1
	Middle Button Emulation:		2
	Middle Button Timeout:		50
	Wheel Emulation Inertia:		10
	Wheel Emulation:		0
	Wheel Emulation X Axis:		0, 0
	Wheel Emulation Y Axis:		4, 5
	Wheel Emulation Timeout:		200
	Wheel Emulation Button:		4
	Drag Lock Buttons:		0
```

---

### Post by ufarmer on 2009-04-18
> **labinnsw said:**
> Was [this]("http://ubuntuforums.org/showthread.php?t=684843") the post you used? *In particular entry #18*

That was the first one I tried.  I have tried a few others since then.  In every case editing my xorg.conf file according to the "solution" causes X to crash.

---

### Post by coffeeaddict22 on 2009-04-18
OK, so that looks like most of it should work.  What exactly isn't working/ what's the abnormal behaviour?
And typing in ```
xinput list | grep Logitech -A15
``` should tell you a bit more- like how many buttons X thinks you've got available.  What does it output?

---

### Post by ufarmer on 2009-04-18
The output is:

```
>> xinput list | grep Logitech -A15
"Logitech USB Receiver"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Video Bus"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
```

The problems with the mouse are that it doesn't track well -- really disliking tracking to the right -- and that left clicking works only sporadically.  The scroll wheel and right clicking seem to work just fine.

---

### Post by coffeeaddict22 on 2009-04-18
I could be being cynical, but all your X settings look fine, and the behaviour is a bit unusual.  Have you tried it on a different computer?  The fact it's tracking abnormally  is ... odd.  Has it got something stuck on the bottom of it? Have you tried new batteries?
What does  ```
sudo cat /var/log/Xorg.0.log |grep Logitech
``` look like?  Is there any message that looks like the mouse has spat the dummy?

---

### Post by ufarmer on 2009-04-18
The output is:

```
>> cat /var/log/Xorg.0.log | grep Logitech
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event2"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 8 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(EE) Logitech USB Receiver: Read error: No such device
(II) config/hal: removing device Logitech USB Receiver
(II) Logitech USB Receiver: Close
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event2"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 8 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
```

The batteries are brand new.  There's nothing stuck to the bottom.  And it works like a charm when I plug it into my desktop computer -- which is only running kernel 2.6.18.  Is it possible that the touchpad on the laptop is interfering with the mouse?

---

### Post by coffeeaddict22 on 2009-04-19
Could be, but laptops all have touchpads so it seems unlikely.  Have you run ```
xinput test 'Logitech USB Receiver'
``` (those ticks are single quotes) and watched the output?  What happens when you click the buttons that aren't working?  And when you move the mouse to the right, what does xinput report to the terminal?

---

### Post by ufarmer on 2009-04-21
xinput test 'Logitech USB Receiver' basically confirms what I am seeing.  Tracking does not always register and neither does left clicking.  The other buttons all seem to register.  It's strange the the mouse works no problem with the 2.6.18 kernel and not with 2.6.27.  Well, it works as a two button mouse with a scroll wheel, the other buttons are inactive.  But it tracks and clicks properly.

With 2.6.27 the behaviour is completely inconsistent.  Sometimes it works perfectly for a few minutes and sometimes it won't track at all and none of the buttons work either.  It's very strange.  Not working is one thing, but working/not working sporadically seems to be another.

Where are the mouse drivers installed in 8.10?  There's nothing in my xorg.conf file about a mouse.  I would be happy if I could use another driver and get a working mouse with two buttons and a scroll wheel.

---

### Post by coffeeaddict22 on 2009-04-22
xorg.conf seems to be being gradually deprecated, and at least for input it's no longer useful- any settings in there are ignored.  They're now kept in files under /etc/hal/fdi/policy.  Have a look at [https://wiki.ubuntu.com/X/Config/Input]("https://wiki.ubuntu.com/X/Config/Input") for some good info.  You should be able to alter the fix you used to modify the xorg.conf file earlier to a format that will be recognised.

I remain suspicious it's a little more complicated than that though.  The mouse tracking being off only in one direction (and an intermittent but OS dependent button problem) suggests there's something interfering with the mouse.  It might be worth looking at ```
cat proc/interrupts
``` to see if you have an IRQ conflict.  Post it back if you want more help; you might get someone smarter than me...  there's a wiki page at [https://help.ubuntu.com/community/DebuggingIRQProblems]("https://help.ubuntu.com/community/DebuggingIRQProblems") that may help.

---

### Post by ufarmer on 2009-04-22
Here's the output, I'm not sure how to read it

:```
>> cat /proc/interrupts 
           CPU0       CPU1       
  0:   12735207   12783470   IO-APIC-edge      timer
  1:       2031       1912   IO-APIC-edge      i8042
  8:         27         15   IO-APIC-edge      rtc0
  9:      43522      43719   IO-APIC-fasteoi   acpi
 12:     273793     273375   IO-APIC-edge      i8042
 14:      27008      27034   IO-APIC-edge      ata_piix
 15:     173799     171006   IO-APIC-edge      ata_piix
 16:      12610      13095   IO-APIC-fasteoi   uhci_hcd:usb5, yenta
 17:    3069445    3030384   IO-APIC-fasteoi   uhci_hcd:usb6, ohci1394, HDA Intel
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb7, mmc0
 19:          1          2   IO-APIC-fasteoi   ehci_hcd:usb8
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb1
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 22:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 23:          0          0   IO-APIC-fasteoi   ehci_hcd:usb4
217:     603349     595524   PCI-MSI-edge      iwlagn
218:      19105      20093   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:   12360152   14622840   Local timer interrupts
RES:    2631935    2715625   Rescheduling interrupts
CAL:        230        170   function call interrupts
TLB:     160500     159578   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
```

I'll check out those other resources you mentioned.

---

### Post by ufarmer on 2009-04-22
So it turns out that I made a typo with the first thing I tried.  If I do [this]("http://ubuntuforums.org/showpost.php?p=4636059&postcount=9") the mouse works much better but still has occasional problems tracking and left clicking.

---

### Post by ufarmer on 2009-04-22
Correction: Now that I have been using the mouse for a while I would say it is only slightly better.

---

### Post by coffeeaddict22 on 2009-04-23
Did you create a HAL .fdi file or alter xorg.conf?

---

### Post by ufarmer on 2009-04-23
I edited xorg.conf.

---

### Post by ufarmer on 2009-04-24
It may be too soon to tell for sure, but I upgraded to 9.04 and it seems to have resolved my mouse issues.  The update manager actually commented out my change to xorg.conf. :-)

---

### Post by coffeeaddict22 on 2009-04-24
Excellent!
I suspect there's been some issues with the X input code.  X, the window manager in Linux, has moved all the input information from xorg.conf to separate files in /etc/hal/fdi/policy/, and it looks like it's ignoring xorg.conf except for display parameters.  There's a series of forum posts here and elsewhere with similiar problems; metacity has caused issues, incorrect mouse driver settings at others.

If it recurs, converting the xorg.conf settings to a fdi file format is probably the next thing to try, but lets hope that's not required!

---

### Post by ufarmer on 2009-04-24
Yes, I'll be happy if everything decides to just work now. :-)  Thanks for all your help coffeeaddict22.

---

