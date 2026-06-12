---
title: "Ubuntu 9.10 on Laptops"
date: 2009-12-07
forum: Hardware
---

### Post by tiddlydum on 2009-12-07
I have managed to sort out my Ubuntu 9.10 on my Acer Aspire 5738, so here's the solution to those still trying.
First up: If you haven't managed to install, insert the live CD, then choose your language, and select "Install Ununtu". Press F6 (other options), press ESC to close the popup menu, and then add the code above to the end of code you will see, then hit enter, to begin your install.

For those who upgraded, or (like I did, installed it with an external monitor) If you find the screen is black whilst booting, yet you get the welcome sound, we need to get you into your install.
Note: If you upgraded, you will have GRUB legacy. If you did a fresh install, you have GRUB 2. If you have GRUB 2, skip the next section.

**_[SIZE="3"]FOR THOSE WHO UPGRADED (GRUB LEGACY USERS):[/SIZE]_**
So here's the temporary fix. When GRUB loads, you need to highlight the Ubuntu 9.10 (If you can't see the menu, press ESC). Then press 'e' to edit the command. Look for the line that begins with kernel, then add this on the end:
```
i915.modeset=0
```
Then press b to boot. Once you have booted, you need to log in, and apply the permenant fix. If you don't see anything pop up, yet you still hear the welcome sounds, you've either done it wrong, or I can't help you.
Once into your system, open a terminal and navigate to your /boot/grub/ directory. 
```
cd /boot/grub/
```
Then:
```
sudo nano menu.lst
```
For those who prefer to edit command line, or, for other people:
```
gksudo gedit menu.lst
```
You then need to find this:
```

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		e4b87e4d-7636-4d7f-9c8d-aafb82cc19cd
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e4b87e4d-7636-4d7f-9c8d-aafb82cc19cd ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

```
(It's near the bottom.)
You may not find the exact same code, but just look for the first line. Once you've found it, add this to the end of the line beginning with 'Kernel':
```
i915.modeset=0
```
save the file, and you've added that fix! Skip past the next section for the screen brightness.

**_[SIZE="3"]FOR THOSE WHO INSTALLED FRESH FROM A 9.10 CD (GRUB 2 USERS):[/SIZE]_**
On GRUB 2, the grub that ships with fresh 9.10 installs, the default silent timeout is 0. This means that you will need to use a live CD to apply the fix below. To boot the 9.10 CD, choose your language, then press F6 (other options), press ESC to close the popup menu, and then add this: ```
i915.modeset=0
``` to the end of the line you will see, then hit enter. Let's hope this boots. If it doesn't, someone else might be able to help you.
Once you have booted and logged in, open a terminal and navigate to your /boot/grub/ directory. 
```
cd /boot/grub/
```
Then type type this:
```
sudo nano grub.cfg
```
For those who prefer to edit command line, or, for other people:
```
gksudo gedit grub.cfg
```
Ignore the request not to edit this file: The options you are setting are not editable by the means it asks you to use. Look for this code:
```

menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 264540f9-210b-40bb-8f16-ade86b454ac1
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=264540f9-210b-40bb-8f16-ade86b454ac1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}

```
add this code to just after the bit that says "quiet splash":
```

i915.modeset=0

```
Save the file, and you have fixed that. Now for the screen brightness.

The only way I have found is to type this into the console:
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```
This IS NOT a permanent fix. I also don't know that it works for everyone running 9.10, however, [this thread]("http://ubuntuforums.org/showthread.php?t=1321403") has a grub solution. Good luck.

Post successes and failures below, if I can't help you, someone else might be able to.

---

