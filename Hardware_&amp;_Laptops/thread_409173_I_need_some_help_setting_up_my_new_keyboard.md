---
title: "I need some help setting up my new keyboard"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by Aathos on 2007-04-14
I need some help setting up all the features of my new mouse and keyboard.  I just purchased a Logitech Cordless Desktop S510, and some of the extra buttons do not seem to work in Ubuntu Edgy.  When I tried to map functions to them in "Keyboard Shortcuts", but there was no response.  The buttons that are not working are: Rotate; Shuffle; Zoom (+ and -), and 100%.  

Also, there is a key that is used to access a second tier of operations on the function keys that Ubuntu does not seem to recognize.  It toggles on and off, and when it is toggled on there is no response when the function keys are pressed.  Again, this was tested it "Keyboard Shortcuts". 

In "Keyboard Preferences" I have tried changing the keyboard model on the layout tab, but without much effect.  My big issue with that is that I don't know which model to choose.  Does anyone know which one applies to my keyboard?  The model name on the back is: Y-RAK73, but other places it says 'S510 cordless keyboard'.  

I would prefer a solution that uses a GUI if possible, but am not afraid of the terminal.  

Thanks in advance

---

### Post by kidders on 2007-04-15
Hi there,

Before something like Gnome or KDE can do anything with extra keyboard buttons, you need to configure X to recognise them. Normally, I would do that with **xev** (to identify keycodes) and **xmodmap** (to assign them some basic functionality).

There's plenty of help on configuring **xmodmap** around. Basically, it's a matter of writing out a list of keymaps, and having them load when you log in. You can make any key/button on any input device do anything you want ...  as long as X sees you press it. Sometimes it doesn't (as is the case with one of the buttons on my mouse), but you won't know 'til you try. If you take a look around the web, you *might* find an **xmodmap** configuration (or perhaps something involving other utilities) for your keyboard, created by someone else ... but it's often quicker/easier to do it yourself.

---

### Post by Bohlio on 2007-05-17
I hate to dredge up an old topic, but how did this turn out? Aathos did you get it to work correctly? I have the same keyboard and Im wondering how to get it to work with all (or most) of the extra buttons. I see that in the keyboard options in Fiesty it has some pretty close models of the logitech chordless desktop, but not the right one. Is there any way to update those options or add a configuration to them??
Any help would be great.

---

### Post by Aathos on 2007-05-18
I really don't remember what I did to get the buttons to work.  I am using "Logitech Cordless Desktop Pro (alternate option2)" as the keyboard model, though another might be a better fit.  Most of the extra buttons work, the zoom buttons, rotate and shuffle don't work though, neither does the second level on the function keys.  Those buttons don't show any response in xev.  I remember reading that if xev doesn't give you the key codes then you can't do any thing with them, if I am wrong please, someone correct me.

I hope that helps, Bohlio.  Let me know if you find a better set up, or a way to get those other keys to work.

---

### Post by Bohlio on 2007-05-19
Ahhh yep, setting it to "Logitech Cordless Desktop" seems to work just fine and I got most of it working now. with system>preferances>keyboard shortcuts, I got the Music button and the Home button working. I dont think I'll be able to get the shuffle button to work, but the rest of the music buttons work well. The forward/back play/pause all work with rhythmbox, I dont know about other multimedia players though. How can i change the function of the sleep button though. right now, I think it sends it into Hibernation, but Id prefer to use it to "Suspend" ubuntu. If Im not mistaken, Hibernation saves your current desktop to the harddisk and shuts down, Suspend keeps the power on and doesnt write to the drive, right?? Im pretty sure thats how it worked in windows...

---

### Post by kidders on 2007-05-19
Hi guys,

> **Aathos said:**
> I remember reading that if xev doesn't give you the key codes then you can't do any thing with themThat's pretty accurate. Conventionally, keyboards interact with an OS by issuing scancodes when a user touches a key. For some hardware manufacturers (as you probably know), standards exist to be broken, which means their products require special drivers ... often for no good reason.

I may be wrong, but afaik the only ways to get such a keyboard to work are:
[LIST]
[*]Using a manufacturer-supplied driver
[*]Using a reverse-engineered driver
[/LIST]
The catch is that neither may be available. :-(

> **Bohlio said:**
> How can i change the function of the sleep button though. right now, I think it sends it into Hibernation, but Id prefer to use it to "Suspend" ubuntu.That depends on a few things:
[LIST]
[*]What scancode is being issued when you push the sleep key
[*]What ACPI call is being generated by Ubuntu
[*]What your BIOS is configured to do with the call
[/LIST]
All three are normally configurable, but it's not always obvious which one(s) to tweak. For example, it's conceivable that your BIOS may be configured to make it impossible to suspend your PC (ie only to hibernate it). FYI, BIOS configurators often refer to the kind of suspending you want as "STR" (Suspend to RAM); there are also various numerical codes (eg S1, S4, S5...) used to describe power states.

> **Bohlio said:**
> If Im not mistaken, Hibernation saves your current desktop to the harddisk and shuts down, Suspend keeps the power on and doesnt write to the drive, right?Yep, that's right. Hibernation writes the contents of RAM to swap space, allowing you to do things like move the PC to another location, or boot into another OS for a while, before restoring its original state. The downside is that adding or removing things like hard disks, USB or bluetooth devices while the computer is off can have odd results, because the hibernating OS doesn't see you do it, and might get upset.

Suspending a PC merely puts it into a more power-efficient state, until you're ready to use it again.

---

### Post by Bohlio on 2007-05-19
Wow thank you for taking the time to explain all of that to me :-)
> That depends on a few things:

    * What scancode is being issued when you push the sleep key
    * What ACPI call is being generated by Ubuntu
    * What your BIOS is configured to do with the call

All three are normally configurable, but it's not always obvious which one(s) to tweak. For example, it's conceivable that your BIOS may be configured to make it impossible to suspend your PC (ie only to hibernate it). FYI, BIOS configurators often refer to the kind of suspending you want as "STR" (Suspend to RAM); there are also various numerical codes (eg S1, S4, S5...) used to describe power states.

This sounds a little too complicated for me at the moment. Once I'm a litte more educated in how to work with  Ubuntu efficiantly I'll try to work this out. The sleep button Isn't a neccesity for me, so I'll just leave it for now :-)
Thank you for all your help!

---

