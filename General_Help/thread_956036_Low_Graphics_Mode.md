---
title: "Low Graphics Mode"
date: 2008-10-22
forum: General Help
---

### Post by perks on 2008-10-22
After I upgraded to the 2.6.24-21 kernel, my computer starts in low graphics mode. I can't seem to fix it using the methods I've read in other posts. My video card is a nVidia 8500 GT.

---

### Post by perks on 2008-10-22
After I upgraded to the 2.6.24-21 kernel, my computer starts in low graphics mode. I can't seem to fix it using the methods I've read in other posts. My video card is a nVidia 8500 GT and I'm using the 64-bit version.

---

### Post by gunjin1 on 2008-10-22
What other methods are there? I did a similiar upgrade last night and now NONE of my drivers work. Starts in Low Graphics mode. I have no NIC so no network connectivity. I have Dell D620.

Going to keep searching, just hope people respond here as well...

---

### Post by camoanimal on 2008-10-22
I am having the same problem.  I tried to adjust the graphics back to my native res. at 1280x800 60 Hz and now the screen is over inflated so that it now spreads out of the view of my screen.  Like looking at a little part of the whole.  

If anyone would like to take a look:
[http://ubuntuforums.org/showthread.php?p=6016087#post6016087]("http://ubuntuforums.org/showthread.php?p=6016087#post6016087")

---

### Post by FAMUgolfer on 2008-10-22
I had this similar problem when i realized that my nvidia graphics card was not checked in the system> admin> hardware drivers setting.  After I checked it ubuntu started downloading updates to the card and then asked to reboot......once i did that I got the 'low graphics mode' dialog box.  

What helped me for some reason was downloading EnvyNG....I really can't explain it but this is what someone posted on my thread...[http://ubuntuforums.org/showthread.php?t=955586](http://ubuntuforums.org/showthread.php?t=955586)

---

### Post by gunjin1 on 2008-10-22
I found the steps [here]("http://ubuntuforums.org/showthread.php?t=948584&page=8") to work.

Went into GRUB and booted with the 19 kernel recovery did the fixes from the recommended post. and booted back up normally. Going to grab the envyNG files just in case. My resolution and wireless both work now. but you never know.

Thanks all. To the O.P. I hope your issues get resolved too :D

---

### Post by Yellow Pasque on 2008-10-23
> I can't seem to fix it using the methods I've read in other posts
What have you tried? Envy?

---

### Post by perks on 2008-10-23
> **gunjin1 said:**
> I found the steps [here]("http://ubuntuforums.org/showthread.php?t=948584&page=8") to work.

Went into GRUB and booted with the 19 kernel recovery did the fixes from the recommended post. and booted back up normally. Going to grab the envyNG files just in case. My resolution and wireless both work now. but you never know.

Thanks all. To the O.P. I hope your issues get resolved too :D

What steps are you referring to in that post?

---

### Post by perks on 2008-10-23
I tried EnvyNG and that didn't work. I also tried running Envy but after I enter the administrator password the program crashes.

---

### Post by perks on 2008-10-25
For me, this was no help. EnvyNG installs a Nvidia driver, but this driver just offers 640x480 and 320x240. The 'NVIDIA X Server Settings' program works only when the NVIDIA X driver is active. Running 'nvidia-xconfig' as root and then rebooting the X server does not help. It does not use the NVIDIA X driver. It seems to be necessary to activate the proprietory NVIDIA driver in the 'Hardware driver' program. After a reboot the driver works 640x480 and the 'NVIDIA X Server Settings' program is unusable in 640x480. This problem occured after upgrading to the 2.6.24-21 kernel.

---

### Post by perks on 2008-10-25
For me, this was no help. EnvyNG installs a Nvidia driver, but this driver just offers 640x480 and 320x240. The 'NVIDIA X Server Settings' program works only when the NVIDIA X driver is active. Running 'nvidia-xconfig' as root and then rebooting the X server does not help. It does not use the NVIDIA X driver. It seems to be necessary to activate the proprietory NVIDIA driver in the 'Hardware driver' program. After a reboot the driver works 640x480 and the 'NVIDIA X Server Settings' program is unusable in 640x480. This problem occured after upgrading to the 2.6.24-21 kernel.

---

### Post by bapoumba on 2008-10-25
Threads merged.

---

### Post by perks on 2008-10-26
EnvyNG finally worked for me after several attempts. Thank you for the help. I have one more question though, is there a way to enable the restricted NVIDIA drivers while using the drivers that EnvyNG installed? Or do I have to install the ones from the Ubuntu repositories to get it to show up in System>Administration>Hardware Drivers?

---

