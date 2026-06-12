---
title: "ThinkPad T41, machine still warm/hot during sleep/suspend"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by Abdi110 on 2007-03-11
Hi. I've got a ThinkPad T41. I've set the machine to suspend when the screen closes. I've noticed the battery gets depleted faster and the machine still runs warm while in suspend then compared to Windows XP. Any tips or tricks to get the machine to suspend like under Windows? Thanks!

---

### Post by retiman on 2007-03-23
I have a thinkpad t60 running xubuntu and it does this too :(

---

### Post by Abdi110 on 2007-04-04
A bit of an update. I didn't really give all that much info as far as what I'm running.

ThinkPad T41 with a ATI Radeon R250 Lf [FireGL 9000] (rev 02), Edgy.
FGLRX drivers, XGL, Beryl. I used this HOWTO with setting all of this up.

[http://ubuntuforums.org/showthread.php?t=291464&highlight=beryl+ati+howto](http://ubuntuforums.org/showthread.php?t=291464&highlight=beryl+ati+howto)

After doing a little trouble shooting, I think I've figured out that the GPU just isn't shutting off. The backlight shuts off, everything else does, and the warmth is coming from behind the GPU. I was pointed in the direction of this page...

[http://www.thinkwiki.org/wiki/Problem_with_high_power_drain_in_ACPI_sleep#Radeon_GPU_not_powered_off](http://www.thinkwiki.org/wiki/Problem_with_high_power_drain_in_ACPI_sleep#Radeon_GPU_not_powered_off)

Since I'm running FGLRX I figured this solution wasn't really an option.

I then found this.

[http://ubuntuforums.org/showthread.php?t=19719&highlight=radeonfb](http://ubuntuforums.org/showthread.php?t=19719&highlight=radeonfb)

Trying the command radeontool power off yielded no results. Seems like the copy on the repos doesn't have the power option. I got a build of the 1.5-mjg version.

So I still haven't checked to see if this work around even fixes my problem, as I'll only be able to tell over a span of time (like if the machine is still hot after being in suspend after an hour) and I still have work to do. What I have noticed is that is has major trouble coming back out of power off state.

When I issue the command sudo readontool power off the display shows a bunch of stripes, keyboard input through the machine dies, issuing readontool power on through another machine sshed in brings the device back out of that state but freezes up the window. If I do this during the gdm login, I can type some text into the login name field, and move the window around, but after a few seconds of "action" the screen locks up.

So this is sort of where I'm at now. I've gone through and tweaked with some settings that I added to /etc/default/acpi-support for FGLRX, but still no real results. 

I'm guessing, based off of what I read in the thinkwiki page that this issue will be resolved with Feisty as it'll have the newer kernel.

---

