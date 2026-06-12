---
title: "Can't turn off LCD backlight..."
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by SFDD on 2006-07-02
I'm fairly new to both Ubuntu and Linux in general. I have a Dell Inspiron 8500 laptop that I have Dapper installed on. I have set the power options to turn off the LCD backlight after x minutes, but it's not working. What I get is a smeared ghost or cloud-like mess all over the screen. It's tough to describe. (The screensaver can "blank" the screen fine, but you still see that the backlight is on.)

Anyway, I have an nVidia GoForce Go 4200 with 64 MB of RAM. I have tried  the OpenSource 'nv' drivers and also the nVidia drivers.

What's odd is that I previously had SUSE 10 installed on this laptop and the LCD light switching did work. So this gives me hope that it's possible somehow.

Any suggestions are appreciated! 

Thanks.

---

### Post by forlau on 2006-07-04
The same for me, but on a normal desktop computer. Screen is getting a blank signal, but not standby. I think its a proplem with the nvidia driver and the powermanagment.

---

### Post by SFDD on 2006-07-05
Hey forlau:

Did it work for you using the nv driver instead?

---

### Post by Shay Stephens on 2006-07-05
I got the LCD to turn off by uninstalling the gnome screensaver installing xscreensaver and using it's options.

---

### Post by SFDD on 2006-07-05
Thanks, Shay. I think I actually attempted this, but if I recall correclty, I got the impression from the Software Installer than I was about to remove far more than just the screensaver so I aborted. Did you do a "complete" uninstall of it?

---

### Post by Shay Stephens on 2006-07-05
[QUOTE=SFDD]Thanks, Shay. I think I actually attempted this, but if I recall correclty, I got the impression from the Software Installer than I was about to remove far more than just the screensaver so I aborted. Did you do a "complete" uninstall of it?[/QUOTE]

Yes, it says something about removing the gnome desktop, sounds scary, but nothing bad happened ;-)

---

### Post by SFDD on 2006-07-05
Yeah, you were correct in that my Linux World didn't come to an end after uninstalling it, but I'm afraid xscreensaver didn't do the trick for me. :( The backlight continues to stay on, even after the screensaver has dimmed the screen.

Thanks anyway!

---

### Post by Shay Stephens on 2006-07-06
[QUOTE=SFDD]Yeah, you were correct in that my Linux World didn't come to an end after uninstalling it, but I'm afraid xscreensaver didn't do the trick for me. :( The backlight continues to stay on, even after the screensaver has dimmed the screen.

Thanks anyway![/QUOTE]
Don't know if this will help or not

My settings in xscreensaver:
Display mode, only one screen saver: flurry
blank after 5 minutes
cycle after 10 minutes

Advanced tab
power management enabled
standby after o minutes
suspend after 0 minutes
off after 15 minutes

---

### Post by redoscar3 on 2006-07-06
You might try to use the "vesa" driver for the display card instead of the "nv" driver.  Also, check the DPMS setting in your xorg.conf file.  This setting is in /etc/X11/xorg.conf and should look something like the following:

Section "Monitor"
[INDENT]Identifier        "Generic Monitor"
Option           "DPMS"
HorizSync      <use only proper range for your monitor>
VertSync       <use only proper range for your monitor>[/INDENT]
EndSection

In Mepis, I had to use:     Option    "DPMS"   "true"

Any changes to xorg.conf have to be done by root and requires restarting the X server <Ctrl-Alt-Backspace> to make them active.

Perhaps this might help.

Red

---

### Post by nocturn on 2006-07-06
Did you add the NV_reg mobile option to your Nvidia kernel module?  If so, remove it.

---

