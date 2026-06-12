---
title: "Touchpad not responding after Suspend/Hibernate"
date: 2008-12-21
forum: Hardware
---

### Post by squee-g on 2008-12-21
Hello,

I am semi-new to Linux (Ubuntu).  I installed Ubuntu 8.04 on my Gateway MX-6440, and it is working great so far.  I do have one problem and that is when I put the laptop into either Suspend or Hibernate, after waking the touchpad no longer responds (works fine when laptop boots normally).  The Synaptics Touchpad drivers are installed and configured.  I have also put the following in the xorg.conf file in the Synaptics Touchpad section:

"SHMConfig"    "on"


Has anybody else ran into this problem?  Does anybody know how to fix this?


I checked the xorg.0.log and here is the output:

(II) Configured Mouse: ps2EnabledDataReporting:  succeeded
Synaptics Touchpad no synaptics event device found (checked 18 nodes)
(EE) xf86OpenSerial:  Cannot open device /dev/input/event8
	No such file or directory

(WW) Synaptics Touchpad:  cannot open input device
couldn't enable device 4

The touchpad device number varies (sometimes it is event7, or event8).  After coming out of Suspend/Hibernate, "xinput list" returns the following:

"Synaptics Touchpad"	id=4	[XExtensionPointer]
Num_buttons is 12
Nux_axes is 2
Mode is Relative
Motion_Buffer is 256
Axis 0:
	Min_value is 0
	Max_value is -1
	Resolution is 3
Axis 1:
	Min_value is 0
	Max_value is -1
	Resolution is 0

---

### Post by boynoid on 2009-06-17
Hi, I'm having the same problem.  I just installed Ubuntu 9.04 (desktop/gnome/normal).  I'm using a Gateway MX6128.  Touchpad works fine until coming back from suspend, then nothing.

I'm a fairly advanced user/programmer, but I'm new to Linux.  I'd be happy to post any configs/logs/etc that might be helpful if you tell me how to get them.

Thanks.

---

### Post by goranex on 2009-07-14
I am new to Ubuntu and I am experiencing the same problem. Everything else works just fine.

---

### Post by trevjs on 2009-09-09
Having the same problem myself.  Also with a Gateway laptop.

---

### Post by whirl on 2009-09-29
Im having same problem running 9.10 on fs amilo si 1520. Suspends and wakes up beautifully except the touchpad just doesnt work when waking up.
Anyone posted bug reports or anything to get us going or have we missed something?

Cheers!

---

### Post by almightydugong on 2009-11-01
Hi, I had the same problem with my laptop Amilo PRO V3205. I solved it by downgrading my BIOS to version 1.10.
I think playing with your bios version might help :)

---

### Post by Alex Libman on 2009-11-26
I'm having the same problem with my old Gateway CX200X tablet / convertible.  None of the fix suggestions I've found so far have worked.

It did motivate me to learn vim / emacs though (and look into Firefox keyboard navigation plug-ins), so it's not all bad.  ;)

---

### Post by ServAce85 on 2009-11-26
Same problem with my Gateway Tablet (C-140X).  I updated to the latest version of Ubuntu and when my computer restarted, touchpad functionality was gone.  I have tried to repair the system through the additional startup options, but to no avail.  I will gladly to give more details of log data like @boynoid suggested if someone could tell me how to access them.

I just thought of attaching an auxiliary mouse.  I'll try that and let you know...

---

### Post by ServAce85 on 2009-11-27
Complete Success!  I have a working touchpad again...

Pluging in my auxiliary mouse worked.  I was then able to determine that my problems were due to a bug in the grub update as explained in the following links.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/442441]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/442441")
[URL="https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009"]https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009
[/URL]

Simply put, I backed up my menu.lst file to menu.lst-backup and performed sudo update-grub in the terminal.  After a restart, the touchpad was working again.

Tips for editing/backing up grub are at the following link:
[http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/ ]("http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/")

Good luck!  Let me know if this helps.

---

### Post by oooh on 2009-12-07
Same problem here !

Sony VAIO  FZ21M
Synaptics APLS

Touchpad does not recover from hibernation

I will try your solution.

If anybody elses tries as well, please do let us know the results !

---

### Post by oooh on 2010-02-07
Well actually even when i restart sometimes it does not work at all.

I have the feeling that these lines in my X log file are related :):

(**) Option "Device" "/dev/input/event9"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(**) Option "SHMConfig" "on"
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(WW) AlpsPS/2 ALPS GlidePoint can't grab event device, errno=16
(--) AlpsPS/2 ALPS GlidePoint: touchpad found

Added to the fact that the event number, or input number for the touchpad is not the same everytime I start the computer.

I will try the solution posted by ServAce85 and let you all know what I get

---

### Post by zitro on 2010-03-22
Same problem here. With a Compaq 2510p. Please help us

---

### Post by oooh on 2010-06-09
The solution related to updating the grub does not work

So then I tried 2 more things:

- Updating to 10.04. So now I get this error in the Xorg log file in /var:
(EE) AlpsPS/2 ALPS GlidePoint Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "AlpsPS/2 ALPS GlidePoint"
Again, I get this error randomly

- Forcing the synaptics to be linked to a certain event. I check the event connected to the touchpad in /proc/bus/input/devices:
```
I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input10
U: Uniq=
H: Handlers=mouse5 event10 
B: EV=f
B: KEY=420 70000 0 0 0 0
B: REL=3
B: ABS=1000003
```
And force the event this way in the xorg.conf file:
```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/input/event10"
    Option         "Protocol" "event"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "true"
EndSection
```

But did not work either. 

This random operative touchpad  is driving me crazy

Any idea??

---

### Post by cu_ on 2011-10-16
I am having the same problem.  It started after upgrading to 11.10.   If anyone solved this before, please post what worked for you.

---

### Post by chchandler on 2011-12-26
Gateway MX6184, fresh install of 11.10.

Synaptics touchpad does not work after suspend.  Have not yet plugged in mouse to test.

---

### Post by chchandler on 2011-12-26
> **chchandler said:**
> Gateway MX6184, fresh install of 11.10.

Synaptics touchpad does not work after suspend.  Have not yet plugged in mouse to test.

FIXED
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/59867](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/59867)

jmhenka wrote:

"Edit /etc/default/grub
and change the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset"

and run update-grub, reboot and when you press E in grub you will se the entry there."

Thanks!

---

### Post by vdaneshmand on 2012-07-13
> **chchandler said:**
> FIXED
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/59867](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/59867)

jmhenka wrote:

"Edit /etc/default/grub
and change the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset"

and run update-grub, reboot and when you press E in grub you will se the entry there."

Thanks!
Great! After 2 hours of searching, this worked for me on my Amilo Pro v3205 with Ubuntu 12.04 on it. Thanks a lot! :KS

---

