---
title: "Laptop monitor is black..."
date: 2016-05-05
forum: Hardware
---

### Post by ropa8942 on 2016-05-05
Hi all,

two weeks ago, I turned on my computer and it logged onto a black screen. 
I brought it to work, plugged a external monitor, run a software update and since went back to normal for a couple of days.
A week later, the issue arose again, but the quick fix does seem to work anymore.
To be exact, it seems that the back-light is off. The screen is very dark but I still can see some aspects of my desktop background with light under certain angle. Ubuntu works, I can enter blindly some commands and turn of the computer for instance.
The LCD works for sure, since I can enter the bios and GRUB bootloader without issues...
I am still able to work on the laptop using an external screen, but it tremendously reduces the portability of it.

Any tips about what to do is much welcome...

Thanks for your time!
Cheers !



What computer I have:
I have a Dell precision M4500 with, ubuntu Nvidia GPU "Quadro FX 1800M".
I use Ubuntu 14.04.

What I have tried so far:
- backed to the nouveau drivers
- reinstalled nvidia-current and nvidia-current-updates
- installed a more recent kernel 3.19
- tried to boot with options "nomodeset" and "acpi_backlight=vendor"
- entered a value > 0 in /sys/class/backlight/dell_backlight/bl_power
nothing has worked so far....

possible workaround:
I can boot to older kernels. 
For some of them, the monitor works, I will be able to see my desktop background,
bu I cannot login into my computer. I am brought back to the login screen everytime.

---

### Post by Portaro on 2016-05-05
Ok I think your problem is the graphic drivers, the better suggest to you is to use the system on a version of kernel without this issues and edit grub to boot to this kernel by default, also you have a program called grub customizer that can give to you a easy method to do this config to edit this grub parameter.

---

### Post by ropa8942 on 2016-05-05
Thanks Portaro!

As mentioned earlier in my questions, I am unable to login for any of the older kernel boots.
For all of them, including the one on which the problem originally appeared, 
I would see my desktop and be required to login (although, I normally have no lock on my session).
Entering my password makes the screen flash, and leads me back to the login screen again.

I tried your suggestion and set different older kernels as default boot, but it did not make any difference there...

Cheers

---

### Post by weatherman2 on 2016-05-06
Can you boot from a live disc or live USB with no issues?

---

### Post by ropa8942 on 2016-05-06
@Weatherman 

No, i tried booting from a usb-stick with an Ubuntu 16.04 image on it.
Again, I would need a external monitor to see anything at all....

I though I would try 14.04 later today,
but this made me reluctant to re-image the computer...

---

### Post by weatherman2 on 2016-05-06
I suspect the laptop is confused about choosing your laptop screen vs. the external display and is shutting off the laptop screen after you boot.  Some laptops have a function key combo you hit to toggle between monitor modes ("Laptop screen only," "External Only," "Mirror Laptop Screen + External.").   Look for icons on your row of function keys and find one that looks like a monitor.  Try hitting Fn + that function key once and see if that changes anything; then try hitting it again.  Loading BIOS defaults may also clear this setting.

Another remote possibility: could be you have a stuck "lid switch."  That is, the switch indicates your lid is still closed, so the computer is turning off the backlight.  Just a guess.  Obviously if you see the backlight on clearly in BIOS Setup and during the boot-up, the backlight itself must be OK.

---

### Post by ropa8942 on 2016-05-06
[[COLOR=#000000]@ weatherman2[/COLOR]]("http://ubuntuforums.org/member.php?u=1931279") Thanks for your answers!

Yes I suspect that confusion between screens is the source of all this. 
The only thing "unusual" I did when it first occured, was removing the vga cable before shutting down (I usually do the opposite).
 
The button to switch external monitors on/of is fn+F8 on Precision. I have already tried that many times now... 

I also already tried reseting BIOS default.

I tried booting with a USB key, Ubuntu 14.04 this time... as soon as the os starts, i.e. when I can see the dark purple ubuntu bkground, things go black... Its weird, the issue seems to come from settings in X/unity, since I can use the terminal mode normally, but yet booting onto 2 different start usb key does not make any difference. I am concerned that reimaging does not solve the problem

As for the switch idea, do you mean that some physical glitch inside the laptop would accidentally turn the monitor off? Maybe I should mentioned that I have changed the LCD myself a couple of month ago, so I may have touched something there... Any idea of what I should be looking for?

again many thanks, its cool to get support from the community!

---

### Post by weatherman2 on 2016-05-06
Hmm.  If you replaced the LCD yourself, on a lark, I would open it up again and re-seat the display cable connected to the back of the LCD.

A quick google shows that this model has an LED panel, so there should be no inverter.

Old laptops had a physical switch to trigger the backlight but newer ones maybe not.

---

### Post by weatherman2 on 2016-05-07
It might be that the display is going black when it goes into a high resolution mode, which it would do when you boot an operating system but not before.  There could really be a hardware problem with the panel itself or even with your graphics card.  Any chance you kept the old LED panel (cracked?)  If you still have it, I'd try plugging it in again, if it still works at all, and see if it has the same problem.

---

