---
title: "Keyboard LCD"
date: 2008-10-12
forum: General Help
---

### Post by ickyfeet on 2008-10-12
I've got a Logitech Bluetooth MX 5000 Keyboard.  The keyboard works just fine but there is an small LCD screen on the keyboard that is completely unused.  Is there any way to display information on the LCD?  I'd love to get conky to display info on the keyboard itself.  I don't even know where to begin setting this up.  Any help/information would be greatly appreciated.  Thanks in advance!

---

### Post by sparky-steve on 2008-10-16
Hi,

Is that the bluetooth version?

I cant immediately help with your question - though I have seen a utility somewhere that can display info to the LCD screen and will look through my bookmarks - However, I have the very same keyboard, but my keyboard isnt instantly recognised in gnome or KDE - that is to say when the computer boots, the keyboard is fine, but as soon as X starts, and I get the login prompt, I have to unplug the bluetooth dongle, and plug it back in - a few seconds later my keyboard responds......

Have you ever had this issue, and if so did you resolve it?

Sorry to hijack your thread, will do my best to find the website I was reading with the LCD control.

---

### Post by sparky-steve on 2008-10-16
LCD sites:

[http://linux.softpedia.com/get/Utilities/MX5000-33106.shtml](http://linux.softpedia.com/get/Utilities/MX5000-33106.shtml)
[http://www.kde-apps.org/content/show.php/MX5000+keyboard+lcd+utility+for+mail+che?content=71139](http://www.kde-apps.org/content/show.php/MX5000+keyboard+lcd+utility+for+mail+che?content=71139) (same?)

Hope it helps.

---

### Post by ickyfeet on 2008-10-17
I actually fried my original bluetooth dongle that came with the combo.  It's never a good thing to use the wrong power brick on a usb hub . . .  I bought a cheap-o kingston bluetooth dongle from my local big box computer store.  I actually have the exact opposite problem as you.  I can't get to my bios without a wired keyboard but I have no problems once X starts.  

The bluetooth dongle that comes with the mouse/keyboard actually registers as a usb hub with a bluetooth adapter attached.  The reason it works in bios is that the dongle recognizes the bluetooth input and outputs it to the virtual hub in keyboard/mouse format.  I would imagine that X recognizes it as a bluetooth dongle and doesn't look for keyboard and mouse input from the device.  You might trying to pair the two and see if recognizes it at boot next time.

---

