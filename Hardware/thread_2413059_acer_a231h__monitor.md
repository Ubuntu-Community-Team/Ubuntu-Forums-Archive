---
title: "acer a231h  monitor"
date: 2019-02-20
forum: Hardware
---

### Post by jgw on 2019-02-20
I have been using an acer a231h monitor for several years.  I just noticed that the picture doesn't fill the screen but leaves about an inch all the way around the edges.  I swear it used to fill the screen.  I am using a resolution of 1920x1080 (16:9).  I can move the picture around but only within the space and no further (about an inch all the way around).  I am wondering if anybody can tell me what is going on as, within the parameters I have stated the picture is just fine).  I have messed with the available resolutions to no avail.   I tried to goto acer on this one.  They do not recognize the serial number (probably too old) so I can't even chat with them.  Tried their community forum thing but failed there too.

Thoughts?

---

### Post by Autodave on 2019-02-20
Have you tried another monitor to see if it has the same problem?  It doesn't have to be the same manufacturer or size.

How about a different cable?  Have you checked the cables to make sure that they are secure?  What kind of cable: VGA, HDMI, etc?  VGA cables go bad often and *could* cause that.

---

### Post by CatKiller on 2019-02-20
1920×1080 is the native resolution of that monitor. It should be set to that in Ubuntu. You have additional controls on the monitor itself for other aspects of the picture. Acer say that you should adjust those if the picture is coming up small.

---

### Post by jgw on 2019-02-22
Thanks for the replies!

I should start this with saying that the monitor works, the picture is just about an inch from the screen edges all the way around.

I have messed with the settings.  When, for instance, when I move the picture horizonally (or vertically), it stops at the approximate 1 boundaries.

When I check what it thinks its doing I get: (I am assuming this is how its set.  The 1920x1080 agree with the system settings)

1920x1080
H:67KHZ V:60Hz  (I have no control over this one)
serial number

the setting are set to:
Wide full
ddc/ci on
acm off
input vga

Basically I have messed with all of this stuff, including the picture stuff (bright, move, etc) and it makes no difference. 
My cables are fine

This is, I think, one of them mysteries.   I think I will bring down my laptop tomorrow and see what it does.  

Thanks again!

---

### Post by jgw on 2019-03-01
This morning I was watching my machine, when it was booting.  About 2 minutes after the ubuntu with the dots below started, while the first dot was lit, my screen suddenly went from fully covering my screen to the inch wide frame appeared.  This makes me believe that this is an Ubuntu problem but I have no idea how to fix it.

---

### Post by Autodave on 2019-03-01
Try booting with an installation medium and see what happens.  When you get to the screen asking if you want to try or install, just choose to try.

I would also try another VGA cable.  A lot of those are very cheaply made and can fail or never work correctly.  Even a good cable can fail.  You may just want to disconnect the cable at both ends and then reconnect it or even flip the ends around. (put the PC end to the monitor and vice versa.)

---

### Post by jgw on 2019-03-01
Thank you for the reply

I don't understand "booting with an installation medium"

I swapped out the cable and there was no change.
After I swapped out the cable and then put it back the display was hard up against the left side of the screen and all the way to the bottom (2" on left, 1" on top)
when I tried to adjust it only moved .50" to the right and .25" up.  It seemed to reset the old boundaries.


The monitor display is 10 inches high (should be 11.25" high) and 18" wide (should be 20" wide)

Here are a couple command results:
greg@gregdown:~$ echo $DISPLAY
:0

greg@gregdown:~$ sudo lspci |grep -i vga
[sudo] password for greg: 
01:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1)

greg@gregdown:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+
   1280x1024     60.02  
   1440x900      59.89  
   1280x800      59.81  
   1152x864      75.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   640x480       66.67    59.94  
   720x400       70.08  


Here is my grub file from /etc/default/:
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

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

---

### Post by jgw on 2019-03-01
OK, I rebooted, got the boot menu and fixed a package and then updated grub.  I now have a resolution of 1024x768 and the option is 800x600  I suspect I somehow managed to dump my video driver.  I will check that.  On the other hand I now have a full screen.

I decided to reboot and now I am back to where I started.  I do, however, now have another problem.  I went to software & updates and checked for additional drivers.  I was told there was none available.  I then:
greg@gregdown:~$ lspci -vnn | grep VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G84 [GeForce 8600 GT] [10de:0402] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 0, IRQ 46, NUMA node 0
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau

02:00.0 USB controller [0c03]: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller [1912:0014] (rev 03) (prog-if 30 [XHCI])
	Flags: bus master, fast devsel, latency 0, IRQ 16, NUMA node 0

the second usb controller is a usb 3.0 board to give me some more usb connections.  I can remove it if you think its the problem.  It knows I am using a GeForce 8600 GT and should have told me about available nvidia drivers.  I am currently using nouveau as my video driver.

---

### Post by Autodave on 2019-03-01
"Install medium": what you used to install Ubuntu onto the PC: either a USB or DVD?

---

### Post by jgw on 2019-03-01
thanks for the reply!

I did that I just googled it and it told me what I should have known the entire time.  The reply I wrote, above your last explains where we are now (basically where we started)

I suspect grub but I am going to do nothing else unless I'm told to for fear of really screwing it up (something I seem to be really good at).  the only real changes is that it changed my display driver (nvidia to nouveau )

---

### Post by jgw on 2019-03-01
I did that and the results are just above your last post.  I suspect the problem is in grub.  Before I do anything else I need help or I fear I will really screw it up (I am very good at that one!)  The only change, as far as I can tell, is that my video driver got changed from nvidia to nouveau.  It also seems that this is a duplicate of what is just above.  I swear it wasn't there when I brought this up.

I just rebooted for the heck of it.  Now it no longer recognizes my keyboard.  I am typing this on another machine (using a kvm) but using the same keyboard.  I went through this about an hour ago.  I know the keyboard is good. I also plugged it directly into the back of my computer - still didn't work.   I checked all  my connections and they were fine.  I am going to reboot again just to see what happens next!  Now its just fine.  Yep, I think I got a booting problem?

---

### Post by jgw on 2019-03-01
I think I really have a problem.  My computer just shut itself down so I studied on it.  First I tested the power supply and it was working fine but nothing was spinning.  I wiggled and made sure everything was plugged in correctly.  There was a hint that the 4 hole 12v might be strange so I replaced it (power supply had 2 of them).  Then I tried again and things started spinning.  Then I watched it boot and its hanging on "end kernal panic - no syncing".  then I started to research on that and somebody suggested that the drive might be bad.  I have other drives and I also have everything backed up (the backup that comes with 18.04 is kindofa difficult one to deal with in these situations)  Anyway,  I have downloaded the latest and greatest ubuntu iso file and have created new system dvd's.  My thought is to go with the directions at [https://linuxconfig.org/ubuntu-boot-repair](https://linuxconfig.org/ubuntu-boot-repair)  and see what happens before I switch drives.  

I really don't want to do anything, however, without a bit of guidance.

Thank you.................

---

### Post by jgw on 2019-03-02
thank you all............

I decided to goto  [https://linuxconfig.org/ubuntu-boot-repair](https://linuxconfig.org/ubuntu-boot-repair), follow the directions and it seemed to work.  When it had apparently finished the screen went wonky so I manually rebooted the machine.  I have now rebooted 2 times with no problems.  I am considering doing the boot-repair again just to make sure I did it all.

---

