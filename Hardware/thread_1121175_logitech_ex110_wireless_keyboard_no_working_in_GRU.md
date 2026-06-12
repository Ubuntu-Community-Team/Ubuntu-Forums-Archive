---
title: "logitech ex110 wireless keyboard no working in GRUB menu"
date: 2009-04-09
forum: Hardware
---

### Post by IsraeliHawk on 2009-04-09
hi all,

i have a wireless Logitech EX110 keyboard and mouse, with ubuntu 8.10 installed.. alongside Windows XP. 

when the computer starts, _**the keyboard isn't working**_, i can't choose between the OS and therefore i can't log in to Win.XP!

will be happy for all the help :(

thanks in advance

---

### Post by fructivore on 2009-06-09
I have a similar problem whenever I restore my desktop system from standby.  The ex110 keyboard is basically nonfunctional.  If I listen closely I can hear the click, click that the BIOS(?) makes when the key buffer is overrun, so it's not completely busted, but I can't type.

Once it fails, the failure lasts between reboots and even power downs.

I don't know if that's what you're seeing but the solution for me was to do the following:

 - reboot into Ubuntu
 - from the desktop, activate remote desktop (System -> Preferences -> Remote Desktop)
 - check "allow others to access your remote desktop"
 - check "allow others to control your remote desktop"
 - check "you must confirm access to this machine"

From another computer (with working keyboard!) on your LAN
 - run VNC (WinVNC for instance)
 - connect to your busted machine

Now you can use the working keyboard to type into the Ubuntu box

 - Accessories -> Terminal
 - sudo gedit /boot/grub/menu.lst
 - go to the bottom, count the number of different boot options (each one begins with 'title' I think)
 - figure out which number corresponds to your Windows installation (remember that it starts at 0, not 1)
 - change the line that says "default 0" (or whatever the number is) to be "default " plus the new number
 - sudo grub-install /dev/xxx (where xxx is hda or sda or sdb or whatever your boot device is)
 
You should now have your new grub configuration installed and ready to go.

 - reboot

If everything was correct, you should now boot to Windows.  If your EX110 works like mine, once you're in Windows the Logitech driver will fix everything, and you will have keyboard services again.

If you messed up and your grub loader is totally hosed, you will need to repair it from a boot disk.  There are probably instructions around here for how to do that.

---

