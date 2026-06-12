---
title: "How do I get multiple joysticks to be detected in the same order"
date: 2009-05-03
forum: Hardware
---

### Post by vulcan500rider on 2009-05-03
Hi All!  I've found these forums immensely helpful, as I only tried my first Linux installation about a week ago.  I'm working on an emulator box, and have chosen to go with Ubuntu 8.04, having tried 8.10, but found that it didn't play nice with my Atom board and OpenGL.

I've got everything up and running (FINALLY!), but I've run into a bit of difficulty.  I have three separate gamepads plugged into the system (and will eventually have four)  Two are USB adapted NES gamepads, and the other one is a PS2 controller running through a different kind of USB adaptor. 

All three adaptors work, but everytime the system reboots, the joysticks detect in a different order, so while I've set each of my emulators to use a certain set of buttons (say from J0--the first joystick--that joystick may be J1 when I reboot, so everything gets screwed up.

Is there some way for me to set which joysticks will be assigned which spot on a more permanent basis?  It's a definite pain to have to recalibrate for the emulator I want to use EVERYTIME I reboot.

Thanks guys!

---

### Post by jords on 2009-05-03
Well, i know nothing about joysticks, but your solution is probably setting udev rules for each joystick and giving each one a static device node ie (/dev/leftjoystick or something).

This guide is quite good: [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221) , it's more dealing with usb drives but should apply to any usb device.

---

### Post by vulcan500rider on 2009-05-04
I think that may be exactly what I'm looking for!  THANKS!  I think I may even understand how to implement it <laugh>  I guess that will be the next question, should I need it...

Again, thanks.  I never would have thought to check under USB key mounting for this info...

---

### Post by vulcan500rider on 2009-05-10
OK.  I think I understand everything up to and including setting up the SYMLINK, and I've messed around a bit on the console to see what properties I might want to use to identify each joystick.  I think I also follow the idea of creating the "10 rules" file, but what I DON'T know is the command that I need to make my SYMLINK be assigned to the first joystick.  

Let's say that I have called my joystick SYMLINK "Saitek" and put it at /usbdevices/Saitek

Now, I know that I want it to go to /dev/input/js0   but I have NO IDEA how to do that.  The stupid thing is, I'm sure that this must be a common command, as all I'm really asking for is a pointer of some kind, but I'm still pretty new to Linux and don't really know the syntax yet.  If anyone could help me out, I think I could get things working.  I would certainly appreciate it.

Thanks again guys!  I love these forums!

---

### Post by vulcan500rider on 2009-05-11
Hmm...After some mroe reading, I think the answer is a soft link between the SYMLINK I create for each device, and the js? directory that I want it to occupy.  Hopefully there's not too much potential for disaster there...<laugh>

---

### Post by jords on 2009-05-13
Does your emulator software allow you to set what device node to use for each joystick? Then you could just point each one to the static symlink, which will point to the changing device node. 

Otherwise, you could use the NAME option but not sure what the advantage would be. I don't think you can change the actual device node assigned by the kernel (the /dev/input/js0 etc one).

Uh... Reading your posts again im not entirely sure what your problem is - is the symlink not being created? Or not being pointed to the right node (which will vary depending on the order they are detected)? 

Maybe it would help if you posted the udev rules your using.

---

### Post by vulcan500rider on 2009-05-14
Thanks for the reply!

As far as I know, the only way that I can set the buttons in my emulators is by pressing them, so that I end up with a button being assigned to "js0_b1" and the like.  What I was thinking was a udev rule like this:

   [SIZE=3]DRIVER==&#8220;USB&#8221;, ATTRS{manufacturer}==&#8221;Saitek PLC&#8221;, ATTRS{product}==&#8221;Saitek P3200 Rumble Pad&#8221;, NAME=&#8221;saitekjoystick&#8221;, SYMLINK=&#8221;dev/input/saitekjoystick&#8221;[/SIZE]
  
  [SIZE=3]After that I get stuck.  Can I use something like:[/SIZE]
   
  [SIZE=3]ln /dev/input/saitekjoystick /dev/input/js0    
[/SIZE]


[SIZE=3]I'm obviously a little new to this...but that's the closest I've been able to come up with on my own.[/SIZE]

I should note that I haven't actually tried any of this yet; I don't want to screw anything up, and then have to fix the screwup AND write a new set of rules...I just want to make sure the logic is sound.

---

### Post by jords on 2009-05-14
I don't think you need to be worried about screwing up - If it doesn't work, you can just remove the line from the udev rules file and reboot and it should all go back to how it was before.

Your udev rule looks right to me, but you don't need to run the ln command,  udev will run it automatically when you use the SYMLINK= setting.

The NAME= part of the rule sets the device node to be /dev/saitekjoystick, and the SYMLINK= part will create a link to that at /dev/input/saitekjoystick.

So, just try it i think and see what happens...

---

### Post by stobi on 2009-11-25
Hey guys, did you make any progress on this? 
I have the same problem (joystick, throttles and pedals) for a flight simulator. I am not very experienced in programming, so I would appreciate your help a lot!

Thanks!

---

