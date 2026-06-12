---
title: "Looking for an inexpensive Plug N Play Printer / Scanner"
date: 2020-03-17
forum: Hardware
---

### Post by PopsTheSailor on 2020-03-17
I had a Canon printer / scanner. Plugged in the USB and it printed and scanned. I've tried 2 since and both are worthless. Anyone have a $40 to $60 USD printer / scanner that is actually Plug-N-Play? I'd love wifi but I'd settle for USB at this point.

---

### Post by ajgreeny on 2020-03-17
I've used HP printers over my wifi lan for quite a long time now; not necessarily the cheapest for ink cartridges, though I have been using compatible versions for years now with no problems.

On my computer I did not have to take any action to connect or use the printer as it was found automatically.  I have however installed hplip-gui to get the best GUI for printer configuration that I know of.

---

### Post by Autodave on 2020-03-17
+1 with ajgreeny.  HP is the simplest ones to setup and use.

---

### Post by TheFu on 2020-03-17
I have a Samsung $55 laser printer.  Plug it in and use the system-config-printer tool.  Pretty bonehead.  Works as a network printer from any other system on the network using the IPP protocol.  Crazy simple.

Scanners are harder.  Look for SANE support.  i use a Brother-all-in-one ($60), but setting up the scanner was more difficult.  it has been years since i did that. Ink costs so much that after it ran out, i never printed again.  Wanted it for the automatic sheet feed/scanner and fax which works really well.

---

### Post by Autodave on 2020-03-18
HP laser and HP ink jet: both wireless, my setup consisted of turning the printer on and going into *Printers* and selecting it.  Add* hplip* and *hplip-gui* and make sure *xsane* is installed in order to scan.

---

### Post by kurt18947 on 2020-03-22
I think for stone simple HP is going to be hard to beat. We have 2 Brother devices, 1 older inkjet MFD and one color laser. The printer install is pretty simple  using Brother's installer script. The scanner install can be more of a challenge, the installer should create some links between files in different folders and does so but incompletely it seems. Epson and Canon have linux installers as well but I have no experience with them. 

If you buy a multi-function device and can't get the scanner to work, it might be worth looking at VueScan by Hamrick software. There's a demo version that produces images with water marks but will let you know if your scanner is found and works. Buying a license removes the watermark.

---

