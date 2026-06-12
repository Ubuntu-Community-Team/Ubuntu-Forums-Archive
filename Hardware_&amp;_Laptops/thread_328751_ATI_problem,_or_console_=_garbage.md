---
title: "ATI problem, or console = garbage"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by imrazor on 2006-12-31
About a week ago, I upgraded from an Nvidia 6600GT to a Radeon X1800GTO. All went well in Windows, so I know I don't have defective hardware. The fglrx driver under Dapper gave me so much trouble, I decided to go ahead and install Edgy. fglrx installed OK, however ever since I installed I've run into a weird problem. All of my virtual consoles are colored garbage. Hitting CTRL-ALT-F1 gets me a rainbow colored mess. Booting off the live CD results in the same problem. This isn't a problem as long as X is working, but if something goes wrong with X I'm in trouble. Anyone got a clue?

As an aside, video playback really stinks with the fglrx driver. Is there any kind of a fix for that?

---

### Post by thebert on 2006-12-31
I had the same problem with the fglrx driver on my laptop with a FireGL V5000. I found that turning off the splash screen for ubuntu would fix this.

1. Edit the /boot/grub/menu.lst file
2. Find the section where it boots ubuntu
3. Remove the quiet and splash options.

For example if you have this:
/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash

Change it to this:
/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro

---

### Post by imrazor on 2007-01-02
> **thebert said:**
> I had the same problem with the fglrx driver on my laptop with a FireGL V5000. I found that turning off the splash screen for ubuntu would fix this.
 
1. Edit the /boot/grub/menu.lst file
2. Find the section where it boots ubuntu
3. Remove the quiet and splash options.
 
For example if you have this:
/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
 
Change it to this:
/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro
 
Thanks for the tip. Worked like a charm. Console font is a little goofy, but it's light years better than the rainbow colored mess I had before.
 
Thanks again!

---

