---
title: "Dual booting Vista with Ubuntu 8.10 (Vista installed first)"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by syedrehan84 on 2009-03-15
I AM A BEGINNER to linux and i just installed Ubuntu. I want Vista back as my primary OS when I restart my laptop. What do I need to do that? Also want to leave Ubuntu as my 2nd option.

---

### Post by chubble10 on 2009-03-15
> **syedrehan84 said:**
> I AM A BEGINNER to linux and i just installed Ubuntu. I want Vista back as my primary OS when I restart my laptop. What do I need to do that? Also want to leave Ubuntu as my 2nd option.
You could use [Wubi]("http://wubi-installer.org/") to install Ubuntu *inside* Windows. It will then come up with the Windows boot manager every time you boot, with Vista being default, and Ubuntu no. 2.

---

### Post by syedrehan84 on 2009-03-15
but ive already installed ubuntu

---

### Post by syedrehan84 on 2009-03-15
but I also didn't do it because it said that I will get reduced performance if I install Ubuntu from inside the windows.

---

### Post by Mark Phelps on 2009-03-16
When you boot your laptop, does it go straight into Ubuntu?

If so, once in Ubuntu do the following:
1) Open an editor doing the following in a terminal "gksudo gedit /boot/grub/menu.lst"
2) This will display the boot options file.  
3) Scroll down to the line that says "default" with a number.  That is the default OS that will boot, counting from zero.
4) Now scroll down to the bottom of the file, counting the OS boot stanzas. Each one starts with "title". The sequence number of the Windows OS boot is the one you want to change in the "default" line.  Remember, it's based on zero.  So, if the Windows OS stanza is the 6th one in your file, you replace the "0" with "5".
5) When done, click the diskette icon to save the changes.
6) Reboot


If you're unsure about this and want to experiment, instead of changing the "default" line, change the "hiddenmenu" line to insert "##" in from of "hiddenmenu" on the line.  Save and reboot.  Now, you'll get a menu of options.  The default will be highlighted.

When done changing "default" to what you want, remove the "##" from the hiddenmenu line and save, reboot.

Now it will boot by default into the OS you selected.

---

### Post by TheVulcanGod on 2009-03-16
Well, you could follow the systematic instructions of Mark Phelps. 

AFAIK, If you could reinstall Vista bootloader then I guess you can reboot to Windows Vista. Now, you are booting Ubuntu bcos Grub by default takes over the dual boot responsibilities. 

Try looking over the website for Neosmart as they do have a few tips for dual boot.

For install, you could refer to this link below.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

The suggestion here is to install the grub bootloader to the linux partition so as to leave the vista bootloader in place. Then, using EasyBCD you could configure it so that an extra entry is added for Ubuntu but leaving Vista in charge.

I did read that Vista SP1 did a check to ensure that vista was in the boot sector of the primary partition which is why quite a few of the forums came up with suggestions to leave Vista in charge.

---

