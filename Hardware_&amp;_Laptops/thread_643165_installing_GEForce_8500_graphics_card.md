---
title: "installing GEForce 8500 graphics card"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by Luksion Knight on 2007-12-17
well I've never installed a graphics card before, so I'm not sure what to do. I've installed it on the motherboard and secured it in place with screws, and when i start up my computer with the monitor plugged into the card, it shows the bios and the GRUB loading, then the screen goes black and doesnt come back on. ive tried putting the monitor back into the mother-board plug, but it gives no output. what do i do?

---

### Post by crouton on 2007-12-17
The graphics card is fine (you're seeing BIOS and GRUB), it sounds like the bootsplash is having screen resolution issues.

Try hitting Esc when Grub loads, highlight the first line and hit 'e', then go down to the line starting with 'kernel' and hit 'e'.  Go to the end of the line and remove 'quiet splash', then hit Esc then 'b'.  This will force the system to boot without the fancy graphical splashscreen.

If/when you get to your commandprompt or graphical login screen, you'll want to redo your usplash-theme to use a supported resolution.  I'll look it up and edit my post with the particulars.

[edit] Here's the link: [http://geekybits.blogspot.com/2007/11/fix-for-no-splash-in-ubuntu-710.html](http://geekybits.blogspot.com/2007/11/fix-for-no-splash-in-ubuntu-710.html) but I'll cut'n'paste in case the link dies.

> After installing Ubuntu 7.10 there is no splash screen displayed at startup nor at shutdown. I just get a 'Signal Out of Range' message from my monitor.
A program called usplash controls this process, so I looked into it's configuration, the values were totally off for my monitor, which uses a resolution of: 1024x768.
By default the file looks like:
; Usplash configuration file
xres=1280
yres=1024
I edited the file:
# sudo gedit /etc/usplash.conf
I changed the xres to: xres=1024 and the yres to: yres=768.
Then I reconfigured the usplash program with the new settings:
# sudo dpkg-reconfigure usplash
Problem fixed, now the splash image displays both at startup and shutdown.


Change the xres/yres as necessary.

---

### Post by Luksion Knight on 2007-12-17
the problem still persists, i should haave been more clear, the screen turns off and NEVER comes back on no matter how long i wait, unless i reboot it. i dont think its a problem with the up-splash screen, but the drivers. i had envy install nvidia drivers, but that was when i was using my integrated graphics. is there a way i can install the drivers for the specific card without having it installed yet? (when i take the card out it reverts to integrated graphics)

---

### Post by crouton on 2007-12-17
The drivers won't come into play until the graphical environment is trying to load.  If you edited the GRUB entry you should see a wall of text fly by.  Alternately, you can select the Recovery Mode option from the GRUB menu and try booting that - it should dump you at a command prompt without attempting to load the graphical environment.

If you get to this point successfully, I or someone else can help you change the Xorg.conf file to use the proper drivers.

---

### Post by Luksion Knight on 2007-12-17
ok i booted recovery mode, and its at the terminal and im in root.  what next?

---

### Post by crouton on 2007-12-17
edit your /etc/X11/xorg.conf file (use nano or whatever you like) and look for the BusID line. Above it should be the Driver line.  If it has something other than "nvidia" change it to "nvidia", save, exit, and reboot.  

If that doesn't work we'll need to dig a little deeper, but I'm hoping that "nvidia" will work as a default.

---

### Post by Luksion Knight on 2007-12-17
can you give me the exact commands for this? i have little experience in command line (theres no loaded gui either, even when i do regular boot without the upsplash its just a command line)

---

### Post by Dark_Stang on 2007-12-17
Enter "dpkg-reconfigure xserver-xorg" and you'll get a the xserver reconfiguration tool. Just select the nvidia driver, your keyboard layout, screen resolution, etc.

---

### Post by Luksion Knight on 2007-12-17
well what you told me seems to have configured the graphics card and gotten it working, but now my resolution is really low (like 640*480) and i dont see how to change it in the xorg file. how do i change it?

---

### Post by Luksion Knight on 2007-12-17
nevermind, everything is hunky dory now. thanks for all the help.

---

### Post by mastergunner on 2007-12-21
Is there a How-TO on setting up a Geforce 8500GT and the Nvidia driver for it?

---

