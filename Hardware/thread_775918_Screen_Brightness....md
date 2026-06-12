---
title: "Screen Brightness..."
date: 2008-04-30
forum: Hardware
---

### Post by quackquack on 2008-04-30
Hi,

I cannot change my screen brightness at all in Ubuntu. i could not do it in gutsy and i have just upgraded to 8.04 and i still can't change my screen brightness. I have tried using the function keys which shows the bar which is supposed to control the brightness, and i can move it up and down with the function keys fine but it doesn't change the screen brightness at all. I have also tried clicking lower my screen brightness when on battery power in power manager and unplugging the laptop and the bar moves down but again the brightness does not change.

It is probably something i am doing wrong, but is there a way to fix this? 

Thanks in advance.

---

### Post by lecter255 on 2008-05-01
i don't think you are doing anything wrong. in 7.10, i could adjust my laptop's backlight. i can't in 8.04. i use a hp dv2000 with a nvidia graphics card. I can't adjust my screen's brightness at all. when it's plugged in it's bright, when it's not, it's dim. i have heard that there are settings in bios that ubuntu set permanently that caused this, but i don't know how to get into bios.

---

### Post by Danielkida on 2008-05-22
I have a toshiba satellite and report the same problem, the bar slides up and down when i press they keys to adjust the brightness but nothing happens. The display also shows that the brightness has changed when using battery power but nothing has happened. It didn't work in gutsy and still doesn't work now in hardy

---

### Post by pivot@pivpoint.no on 2008-05-22
Bump!

I have a HP Compaq 8710w og Hardy Heron. Bars are moving, but no effect

---

### Post by Morty007 on 2008-05-25
What if you have a desktop? How do you adjust the brightness then? Same thing?

---

### Post by konungursvia on 2008-05-25
You could try altering the desktop gamma in terminal.... [also, if you love linux, there are companies that try harder than HP to make it work].

---

### Post by quackquack on 2008-06-10
so its not just me that has this then?

isn't there some sort of magic thing i can do with the terminal to make it work?

lol :)

---

### Post by quackquack on 2008-06-10
oh and i should probably say

the laptop is a toshiba equium l40 - 10x

---

### Post by rlc2 on 2008-06-13
I have a Dell 1420N with the same dim screen issue.
It worked fine under gutsy, but after upgrading to hardy using the update manager app, the first time I resume the laptop after suspending it I lose the ability to change the display brightness.  With the Gnome brightness control running I can move the slider to any position to no effect, and the brightness control keys on the keyboard pop up the brightness meter but have no other effect.  The xgamma command didn't help either.

After editing various startup scripts in /etc/resume.d, I finally found a workaround, though it's not pretty.  It looks like the gnome resume code fails to run the 'vbetool post' command properly.  Disabling the Gnome resume scripts and using the system scripts instead resolved the brightness problem but that interferes with the Gnome power management controls.  So here's what I do about it (I only have this dell laptop, so this hasn't been tested on any other brand or model):

* Use the "Ctrl-Alt F1" key combination to get to a virtual console after the system starts up from a cold boot (on my system none of the virtual consoles are visible after waking up the laptop).

* Keep a root console running in this terminal by running the following:
```
$ sudo su -
```
and enter your user password.  Press "Alt F7" to get back to the window manager.

* whenever you wake the laptop, use the "Ctrl-Alt F1" key combination.  Your screen will turn black.  Carefully type:
```
vbetool post
```
and press ENTER.

* The "Alt F7" key combination should return you to the window manager, and at this point the brightness controls should work again.

* Alternatively, instead of using a virtual console, you can simply open up a terminal under Gnome and run:
```
sudo vbetool post
```
and enter your user password.
Warning: this can produce disturbing video artifacts.  "Ctrl-Alt F1" followed by "Alt F7" should clean up the screen afterwards.

Hopefully this work-around explanation will also be helpful for whomever maintains the gnome power manglement packages, so all of this will no longer be necessary ..

---

### Post by quackquack on 2008-07-16
thankyou for your post :)

i tried your solution and it caused my screen to flash different colours rapidly (almost causing me a seizure lol :P) and i tried all run modes including ctrl alt f1 and ctrl alt f7 and nothing happened. i had to restart my computer.i tried again and it went black and i used ctrl alt f1 then ctrl alt f7 and it went back to normal, however the brightness control still did the same (bar moves up and down but brightness doesnt change). I tried a third time and it did the flashy thing and i couldnt get it out of it again :(.

are there any other solutions? ill try anything lol.

---

### Post by hsu on 2008-09-05
I have an hp compaq 8710w with 64bit ubuntu gutsy installed.
To adjust screen brightness, I do the following:
1. ctrl-alt-f1, there I can use fn-f9 or fn-f10 to adjust screen brightness
2. ctrl-alt-f7 to get back to x windows.
don't dare trying the vbetool commands just yet...

---

### Post by rekado on 2008-09-19
> **hsu said:**
> I have an hp compaq 8710w with 64bit ubuntu gutsy installed.
To adjust screen brightness, I do the following:
1. ctrl-alt-f1, there I can use fn-f9 or fn-f10 to adjust screen brightness
2. ctrl-alt-f7 to get back to x windows.
don't dare trying the vbetool commands just yet...

That won't work for me. I'm also having this issue on a laptop with an Intel graphics chip. The OSD appears but the brightness just won't change. Tried the vbetool already but to no avail.
Is this a known and reported bug?

---

### Post by eeeandrew on 2008-09-22
I'm having the same issue. I'm on a Toshiba Equium L40-10X. I noticed using the "screens and graphics" under others in the applications menu that the display is set to a generic device. If it were possible to get it changed to the "dp566m Equium 15inch" monitor device it might solve this but so far no luck finding the driver.

---

### Post by dartrod on 2008-09-22
I changed my monitor to an Impression 7LSP and am having the same problems, way to bright and can't adjust the brightness.  Even the display buttons on the LCD Screen have no effect.

RSW

My system is:

AMD Athelon 64 LE 1640 2.6 GHZ 45 watt L2-1MB AM2
AMD Athelon 64 original Stock Fan and Heatsink
Kingston DDR2 PC2-5400 1GN/667 MHz
BIOSTAR MCP6P-M2 (NVIDIA GF6150, SATAII, RAID, DDR2-800
NVIDIA GeForce 6150 GPU Memory share upto 512MB
Onboard High Definition Audio
Onboard Network Card
450W ATX Power Supply
Western Digital CaviarSE 160GB 7200RPM SATA
LG DVD-RAM GSA-H55N

---

### Post by rekado on 2008-12-08
I have had the same problem until yesterday when I decided to boot with the kernel option "*acpi_osi=*" (without the quotes). This will clear the OS identifier string that is sent to the BIOS normally (I read that by default the BIOS is informed that Windows NT is the OS).

Please try this option by adding *acpi_osi*= to the kernel line in /boot/grub/menu.lst. It worked for me and solved the last big issue I had with linux on my laptop.

---

