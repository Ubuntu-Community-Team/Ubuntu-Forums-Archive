---
title: "HOWTO: Connecting devices with Gnome 'Bluetooth Applet'."
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by pingnak on 2008-01-26
Being a recent convert from Full-Time Windows with Linux in VMWare to Full-Time Linux with Windows in VMWare, I couldn't initially figure out how to setup my bluetooth keyboard/mouse, and found help here that resorted immediately to the command line.  

After some more tinkering, I got the gnome 'Bluetooth Applet 0.14' icon in Ubuntu 7.10 (installed by default) to connect my keyboard and mouse 'the easy way'.  

[LIST]Right-click on the bluetooth icon, still holding the right mouse button, select 'Preferences'.[/LIST]
*** No icon?  See below...

[LIST]Under the 'Services' tab, highlight 'Input Service'. [/LIST]

[LIST]Make sure it's checked, highlighted and says 'Running'.  [/LIST]

[LIST]Hey LOOK!  More controls!  It would've been nice to have some help there in that blank space saying 'highlight a service to add/remove devices' or something... ANYTHING, instead of blank space and the presumed knowledge that I had used it before and knew something 'magic' would happen.[/LIST]

[LIST]From here, it's easy.  Click '+Add' down at the bottom.  It comes up with another empty, cryptic dialog box saying 'Select Device' with no devices in it.  [/LIST]

[LIST]Don't dismay, it is ALREADY listening for devices.[/LIST]

[LIST]Press the 'discover me' button on your keyboard and/or mouse.  [/LIST]

[LIST]Your device(s) should pop up on the list briefly after pressing the 'find me' button(s).[/LIST]

[LIST]You can now highlight it/them and the 'connect' button will enable, and you can press it.[/LIST]

[LIST]Click 'Show All' if it doesn't work and try pressing the button again.[/LIST]
[LIST]If it still doesn't work, check your batteries, maybe they're a bit low?  The little blue light can blink, and low batteries will prevent a successful connection.  [/LIST]
[LIST]Also try repositioning the device, if say there's a piece of metal RFI shielding between your device and your bluetooth antenna.[/LIST]
[LIST]Also try going back to the 'Services' tab and stopping/restarting the service and repeating the steps, especially when something just 'stops'.[/LIST]
[LIST]If it still doesn't work,. there's *probably* 'something wrong', and I don't know what.[/LIST]

And YES, the settings are persistent, and they do reconnect after you reboot (generally after you press a button to wake up the device its self).  Even in time to type your password into the initial login screen.

*** No Icon?

If you don't see the 'Bluetooth' icon: Go to "System->Preferences->Bluetooth Preferences" for the same dialog.  If it's not there, you might have uninstalled it (bluez-gnome in the Synaptic Package Manager), or might be using a different tool, or might be using KDE or X instead of Gnome (which means this 'HOWTO' is not for you).

The 'General' tab has the icon settings.  If it says to display it 'Only when adapter is present', and the icon still doesn't appear, then there's *probably* something wrong with your bluetooth adapter configuration, and I don't have a clue what as far as this 'HOWTO' is concerned (though somebody else has probably written an article here or elsewhere on how to enable your particular adapter).

This link should have more information on how to use it... though I could only find programming API and shell configuration help after several minutes of pecking links....
[http://www.bluez.org/documentation.html](http://www.bluez.org/documentation.html)

---

