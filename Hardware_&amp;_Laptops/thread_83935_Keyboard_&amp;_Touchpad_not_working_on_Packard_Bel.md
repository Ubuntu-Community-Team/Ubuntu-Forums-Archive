---
title: "Keyboard &amp; Touchpad not working on Packard Bell IGo 6000 laptop"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by dAMe on 2005-10-29
Hi all,

I'm using Packard Bell Igo 6000 series laptop. When I first enter the Ubuntu installation screen, my keyboard & touchpad not working. 
And I tried to plug in usb keyboard and usb mouse .. it is working, in hope that after setup, my internal keyboard and touchpad will work. 
But still, after done with the setup.. it won't detect my keyboard and touchpad. I also found out, when I exit the X environment, i saw alot of "too much work for IRQ11" messages

I tried to search the forum regarding any related issues, but can't find anything.  But I found out someone mention about turning off the acpi. 
So, I edit the /boot/grub/menu.lst and put acpi=off in order to turn off the acpi. But then, another problem occur when I booting into Ubuntu. I stuck at 

[I]
....
....
Starting hotplug subsystem
Setting up ALSA card 0[/I]

so I can't get in. And then I tried to press ctrl+c just after it enter the "setting up ALSA card 0" message, it skips the load and able to enter Ubuntu. and i'm happy that seems like keyboard and touchpad now working. but then once i enter linux, there's popup message regarding "failed to initialize HAL" and another message "..cannot start battstatApplet"  something like that. I know it something related due to turning off the ACPI. 
Anyone know what cause all those problem? I don't want to press ctrl+c everytime i want to enter linux :( and got all those messages:???: 

help nOOb here :razz:  many thanks

---

### Post by jorgem on 2006-08-10
Hey, i have the exact same problem on my packard bell laptop. I tried to set acpi=off but that does not work on my computer. Leaves no error messages or nothing. Let me know if you find a solution to the problem.

---

### Post by jymbob on 2006-10-30
+1, and indeed, bump

---

### Post by temp2264 on 2006-11-20
i also have the same problem here

---

### Post by ajdunlop on 2006-12-09
There must be somone who can get this to work.
I would really like to ditch Windows on my laptop and really like ubuntu but if I can't use the mouse and keyboard it isn't going to be much use.

---

### Post by adamJ5 on 2006-12-12
Try reconfiguring;
[B]
Back up everything first!![/B]


> sudo dpkg-reconfigure xserver-xorg

---

### Post by jcolloff on 2007-01-16
Hello fellow keypad sufferers.                  ](*,) 

I am surprised that this has not been picked up by an expert as this is effectively a fatal error as the possibility is not mentioned in any of the introductory information. 
Further ubuntu exploration is impossible without the use of a plugin keyboard  & mouse, or an alternative computer.

Having used another computer I think that the beginnings of a solution are hidden away in

  System> Preferences> Keyboard> Layouts      where four laptop\notebooks are listed.

The igo is not listed, but many other layouts are.
I have tried using Belarc Adviser to see if the proprietry name of the keyboard used in the igo is given, but it is not there.

Can anyone build on this lead, please?

Long term, of course, the solution needs to be available for newcomers from 'outside' ubuntu.

---

