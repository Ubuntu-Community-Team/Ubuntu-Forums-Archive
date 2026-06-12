---
title: "Hp commpaq 615 drivers issues"
date: 2009-07-22
forum: Hardware
---

### Post by rbahati on 2009-07-22
hello everyone:o,
I recently bought a laptop hp compaq 615 in which I decided to run Ubuntu 9.04.
Unfortunately i'm neither able to use the advanced graphic effect nor hear any audio sound. i have an ATI RADEON HD 3200 integrated display card and an high definition integrated audio card. Please can someone out there help me!
THANKS IN ADVANCE:P.

---

### Post by runesvend on 2009-07-22
You should be able to use AMD's proprietary graphics driver for your Radeon HD 3200 and thereby get 3D acceleration.
First try opening up the "Hardware Drivers" dialog which is present in the "System" menu under "Administration". Ubuntu *should* be able to automatically install the correct driver. Try it out. If it doesn't work go to [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) and fill out the blanks and you should get to a site where you can download the driver.

You will need to be more specific concerning you sound card before anyone can help you. Take a look at the output of "sudo lspci -vvnn" (or, alternatively, install the package *hwinfo* and take a look at the output of that) and see if you can find more information about it.
Have you set the correct device in the "Sound" configuration dialog under "Preferences" in the "System" menu? Where it says "Default Mixer Tracks" try different devices to see if you have the correct one. The live cd of Jaunty I'm running right now automatically selects a device which starts with "Capture:" (I don't want to capture). But if I select the correct device that starts with "Playback:" it works. Try it out.

---

