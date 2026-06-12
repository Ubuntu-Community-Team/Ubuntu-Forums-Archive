---
title: "Live CD 5.10 Freezing at Splashscreen"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by spandon on 2006-02-16
I have an Acer Aspire 1654 with:
Pent M760, ATI Radeon X300 PCIE, 1 Gb DDR2, 100 GB hd.
Have been trying the Live CD 5.10 to check if I can install BB 5.10 onto it.
Have tried many threads for advice and the best I could find was to type after the Boot: promt:-
live acpi=off, hw-detect/start_pcmcia=false, vga771
This works untill it gets to the splash screen with the mouse pointer, the hd and cd works for a few seconds afterwards then stops, the mouse works ok, left it for a few mins afterwards, but nothing else happens.
Is there another command I can add at boot or on a command line once it freezes?
Thanks
Don

---

### Post by spandon on 2006-02-18
Cracked it.
having tried many times to load the Live CD,getting the same result each time, with no help forthcoming from anyone decided to try something else.
The disks I was using worked perfectly on desktops, but not with the laptop, but the Kubunto Live CD worked perfectly other than I could not get thi Internet to work (ADSL), so why wouldn't the ubunter disk work?
Decided to download another iso and reburn it.
This now worked using the boot up command:
Boot: Live noapic, hw-detect/start_pcmcia=false, vga=771
This time it went passed the splash screen into the ubuntu desktop (Gnome), but like the Kubunto setup the internet had not been auto configured as is the case of using the Live CD into other desktops?
Solved this by System>Admin>Networking>Network Settings,found that the ethernet hadn't been configured, selected the ethernet tab then selected properties, ticked box to Enable this Connection, changed the Static IP address to DHCP selected OK and Wholla! when I tried the internet worked perfectly (using it at present to write this message)
Hope this may assist someone with the same kind of problem that I had?
I shall now wait for the (Dapper) release before I actually do an install, possibly some of the laptop installation problems may have been resolved by then?
Don

---

