---
title: "nVidia Gf 2 MX400 and MX440 - still trying for dual screens"
date: 2009-07-21
forum: Hardware
---

### Post by Nazaroo on 2009-07-21
I tried messing with the AGP/PCI option in the BIOS:

Ubuntu will now only show up and boot clean if PCI is selected as main video card.

This happens to be the MX440. (nVidia).

I couldn't get any action with the onboard card (non nVidia), so I gave up on that, and got a used GeForce 2 MX400 (AGP slot style) card.

I plop that in, but the nVidia drivers don't find it.

The nVidia Driver version is NVIDIA-Linux-x86-96.43-10.

The latest nVidia Driver for my card (?) is NVIDIA ....96.43.13.

I downloaded the 'run' file for installing the latest version, but can't get the computer to go into 'console' mode cleanly.

If I STOP the x-server, the computer hangs, with no prompt or visual msg and is unresponsive.

I tried searching for "How to Stop x-server" and found several ways, but they all seem to just shut off the screen with no prompt.

In this condition I have to reboot to get anything back (but end up in the GUI where I don't want to be).

(Running the nVidia 'run' file in a console just gives an error message instructing me to close the x-server...)

I tried just installing the 2nd nVidia card, but it doesn't seem to show up either.

Whenever I run "Display" from the System/Preferences menu,  I get a small error dialogbox that says: "It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use yoru graphics driver vendor's tool instead?"

Clicking "yes" runs the nVidia configuration/options program.

It tells me I'm running the X-Server version 11.0,
and NVIDIA Driver Version 96.43.10.
Clicking on the second item on their drop menu on left, "X Server Display Configuration" gives more display details and a few buttons.

It shows my Mistubishi TFW9105 monitor (CRT-0 on GPU-0)
but no other cards or monitors, onboard or in the AGP slot either, 
so they can't be selected.

The "Configuration: Separate X screen (CONFIGURE...) button gives a mini-dialog, but only the "Separate X Screen" option is available. the other two options, "Disabled / TwinView" are greyed out.

Lower down, the "Detect Displays" results in no activity or changes whatever, and seems like it is disabled.  "Advanced" just toggles the display mode of the info window, and "Reset" results in the same configuration I already have.

Save to X Configuration File" seems to work, but obviously creates a copy of .config identical to the one I have.

The only button that works predictably and effectively is the "Quit" button.

It seems the MX 400 is invisible.  Maybe it is too old to use as a second monitor.
Any ideas?

---

### Post by Nazaroo on 2009-07-21
update!

I had it booting off the PCI (MX 440) in the BIOS (pre-Linux loading).

This enables Linux to install some version of the nVidia drivers, whereby you can then load an updated version of same if you want.

So that is, I first install one nVidia card and Linux and the driver software.

Then I popped in the other card (in this case an AGP-slot version of an MX 400).

I reboot and this time, I attempt to change the display.

Again I am redirected to the nVidia software program.

THis time it finds the second card but shows its status as inactive.

Fiddling with the nVidia software enables the card, and dragging and dropping the mini-display of the two card/monitors in the orientation box allows you to decide 'right or left' for the second monitor.

Now you have to save your configuration settings (it writes a .config file).

Then you can't "APPLY" the new deal, you just get an error message.

You have to close everything and reboot again.

Now the first screen comes up during the loading of Linux as before, but the second screen is also activated using the saved settings config file.

Yeah!  TWO SCREENS/MONITORS, and quadruple my productive output.

They don't behave like WINDOWS dual monitors however:

You can move the mouse from the one to the other, but you can't have an open window halfway onto each screen, at least I don't know how you do that.

Instead, you have two sets of pulldown menus, one for each screen, and you have to open each application on a chosen screen/page.

You can have multiple pages for each screen as before, but if you have six for one, you have six for the other etc..  Some features appear to apply to both screens.

If anyone knows how to have one window cross both screens, I'd like to know.

I think I can have each screen wider than the visible monitor area, but that is a separate trick, and different than a "windows-style" dual screen.

Nazaroo

---

### Post by Nazaroo on 2009-07-21
Final note for now:

I was able to set up a double-width screen on the right, which works intelligently with the mouse.

You are able to have several programs open on the righthand monitor.

If you move your mouse to the right, you pan to the second half of the virtual window.

You can't use the same trick on the left however, because you pan in the opposite direction.  The window you have open on the left pans offscreen as you try to cross over to the righthand monitor, and so if you have a document open there, it disappears before you can get to the other program you are pasting and editing from.

You could put the window on the right side of the first screen on the left, but then your menus at the top would be offscreen, and you have to pan back to access them.

Other arrangements are possible, but I have the cheap small monitor on the left for viewing html files in FIrefox locally while editing them (on the righthand screen), and uploading them on the 2nd half of the righthand screen. Then (via tabs in Firefox) I can view them locally and on a remote site on the left. 

Nazaroo

---

### Post by kaurie on 2009-08-05
Thanks for this thread

I have just been trying to get twinview working on my new computer with newly installed Ubuntu 9.04. I had just bought another identical AOC 936W screen and found that I could not follow the documentation and was lucky to stumble across this post and so I now have two twin screens working just how I want it.

There is only one problem - I don't know how I did it. 

I did manage to backup /etc/X11/xorg.conf before I configured and after a long wandering used 

[LIST=1]
[*]System - Administration - Hardware Drivers - to load the NVIDIA accelerated graphic driver version 180 (which apparently is OK for my GeForce 9500GT video card)
[*]System - Administration - NVIDIA X Settings; to configure the X Server Display Configuration (with lots of errors) found by many apply trials to get the correct setting
[/LIST]

What I do know is that I would not have done it without this post.

So thanks. :KS

---

