---
title: "Sidewinder Gamepad/Joystick issues"
date: 2006-09-27
forum: Hardware &amp; Laptops
---

### Post by Cyhawk on 2006-09-27
Hello. Ok I have a small, but frustrating problem. I have a MS Sidewinder pro Analog Gamepad which works. (Also a Gravis extreme which also works in windows) However I am unable to get it properly working under Ubuntu. Also under ubuntu, when the gamepad is plugged in, the light shows up ;)

My problem is identical to [http://www.ubuntuforums.org/showthread.php?t=8353&highlight=Sidewinder]("http://www.ubuntuforums.org/showthread.php?t=8353&highlight=Sidewinder")

I am using Ubuntu 6.06, SB 128 soundcard, Gamepads:
Microsoft Sidewinder (Ancient, analog, still works in windows)
Gravis Xtermimator (Also old, analog, still works in windows ;)


I have followed the directions in such threads as..

[http://www.ubuntuforums.org/showthread.php?t=55173&highlight=joystick]("http://www.ubuntuforums.org/showthread.php?t=55173&highlight=joystick")
and
[http://www.ubuntuforums.org/showthread.php?t=16089&highlight=Sidewinder]("http://www.ubuntuforums.org/showthread.php?t=16089&highlight=Sidewinder")

Modprobe gives no errors when i load the following..

sidewinder
gameport

and theyre listed under lsmod as loaded.

cyhawk@earth:~$ lsmod | grep side
sidewinder             12032  0
gameport               15496  3 sidewinder,analog,snd_ens1371

Unfortunaly, I am unable to get programs such as zsnes to detect the joypads (even as root)
ZSNES could not find any joysticks.

Also cating the device gives...
cyhawk@earth:~$ cat /dev/js0
cat: /dev/js0: No such device

Im at a loss, what am I doing wrong?

---

### Post by keithjr on 2007-02-10
Did you ever find a resolution to this problem?  I'm having the exact same issues here, as stated in the links in your post.  I'm using (or trying to use) a Sidewinder Force Feedback Pro joystick.

Devices aren't getting created and when manually generated, they do not function properly.

Anybody?

---

### Post by bobishd on 2007-12-10
cat: /dev/js0: No such device
Change that to read
/dev/input/js0

YOU NEED THE WORD INPUT IN THERE. 


also a helpful program is
jscalibrator
sudo apt-get install jscalibrator
run and you can set up your joystick/gamepad.


Got mine to work but i can't get the direction pad to work in GFCE Ultra (NES) emulator
ideas on that?

Bob

---

