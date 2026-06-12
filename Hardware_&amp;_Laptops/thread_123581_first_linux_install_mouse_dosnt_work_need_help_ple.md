---
title: "first linux install mouse dosnt work need help please"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by drifter0000 on 2006-01-30
I have a generic PS2 optical mouse, and my bios is set to ps2
When I boot up and the modules are loading my mouse appears to be working, when I move the mouse it lights up, when the modules get to setting the system clock the mouse stops lighting up and in the desktop it just sits in the middle although the left and right buttons seem to work because when I press them the mouse jumps to the calendar and the 2 buttons work but i cant move the mouse around.

I am new to the command line and have tried the following

sudo dpkg-reconfigure xserver-xorg  (when I try xfree86 it says its not installed)

I keep hitting return until I get to the mouse settings.  I expected to find choices for PS2 mouse and which port to use (i am using the normal ps2 plug in not usb) but the only options it gives me is 3 button mouse or not.

I have tried 3 button setting and I have tried the not selection.  After that selection it brings up the video section and goes to amount of color depth and then exits back to the command line.

The rest of the program seems to be working.  Can anyone help me please?

---

### Post by encompass on 2006-01-30
is it plugged into the keyboard plug?  That happened to me... and if not... heck try it in the keyboard plug.  Do you have a laptop or Desktop.

---

### Post by drifter0000 on 2006-01-31
No it is pluged into the normal ps2 mouse port.  It is a direct plug not a ps2 adapter on a usb plug.
Desktop
System:   300 mhz AMD K7 
              156mb memory
               some sort of generic hewlett packard mainboard
               sis onboard video 4mb mem
               installed on wd800 western digital 80gb
               
OS breezy 5.10 32bit from free cd

have since tried      sudo apt-get update    and   sudo apt-get upgrade with no change.


The OS seems to be working fine.  Drives mount without trouble.  At the desktop I recieve upgrade notification so i no that I am online.  I can move around inside the calendar in the upper righthand corner of the desktop so I know the keyboard and 2 mouse buttons are working.  The only problem seems to be the pointer itself and not being able to move the mouse around the desktop.
Thanks in advance for any help

---

### Post by mips on 2006-01-31
You problem sounds weird. Do you have access to another mouse you can test with maybe ?

---

### Post by encompass on 2006-01-31
I second that... try another mouse in the ps2 port... you could also try disabling the powersave features... it can cause weird problems too... apci=off at grub... if you don't know how... it's
esc (at the count down)
e
the line with the kernel image... can remember what line... think the second...
press e and at the end of the line type apci=off
enter
b
it's worth a try.

---

