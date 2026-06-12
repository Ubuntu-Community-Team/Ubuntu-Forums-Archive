---
title: "Help with Thinkpad 600: USB fails after APM resume"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by sb73542 on 2005-06-10
Hello, I have Hoary on an older IBM Thinkpad 600.  I have found after EXTENSIVE research and testing that the laptop will suspend and resume (using APM) with the Function keys if I boot with "apm=on acpi=off" and it also doesn't hurt to add "noapic nolapic".  This works well in kernel 2.6.8 from Warty.

However, in kernels 2.6.10 and 2.6.11 (I have tried several from Ubuntu and MEPIS) a bug seems to have been introduced so that my USB controller quits working after resuming from an APM suspend to RAM or disk.  After resuming, the dmesg output is completely filled with hundreds and hundreds of indentical lines that say 

"drivers/usb/input/hid-core.c: input irq status -84 received"

Obviously an IRQ conflict between APM and the USB controller.  I can restore the functionality by restarting the hotplug service.  However, restarting it takes a long time, so I don't think it's a very good solution.  Is there anything I can do to fix this?  I am currently running the 2.6.8 kernel because of this bug, but I don't want to keep using it forever on future releases because >=2.6.10 has some nice features that 2.6.8 lacks.  Any suggestions please?  Thanks!!

---

### Post by Frihet on 2005-06-10
Hello sb73542,

I too have a 600 and am having problems with power management. I think you just answered one of my questions.

I'm going to do another install right now.

I don't have your answer, but it's good to know there are others like me out there.

---

### Post by sb73542 on 2005-06-10
[QUOTE=Frihet]Hello sb73542,

I too have a 600 and am having problems with power management. I think you just answered one of my questions.

I'm going to do another install right now.

I don't have your answer, but it's good to know there are others like me out there.[/QUOTE]
 :-)  Glad I unwittingly helped!  These 600's aren't half-bad laptops are they?  Durable, lightweight, good-looking.

---

### Post by Frihet on 2005-06-10
Ok, I finished the install and edited the boot line per you post.

I still have the later kernel in service. Can you tell me how to install the 2.6.8 kernel?

As I am, my USB is totally dead and I have no sound. With Mandriva 2005 LE, APM works and I have sound and USB.

---

### Post by john_walsh54 on 2005-06-11
I get an Ooops in Warty unless I specify the above options. I have no problems with USB but on shutdown there is only "Hiberate the computer" which may not suit your needs.
In fact, I might use your settings in a future install. As stated earlier its good to know there are Thinkpad 600 users out there.

---

### Post by Frihet on 2005-06-11
Hi, John.

It's good to hear from you. We 600 users need to hang together  :smile: 

I really like this machine. I've tried about everything to get it running with Ubuntu. It does fine with Mandriva. However I really want to have access to the Debian Universe, so I'm still trying.

Is your entire boot line as you indicated in your last post?

Thanks!

---

### Post by Frihet on 2005-06-11
Question: Are the quotes around the boot line command arguments required?

Also, I found my no USB problem. Something happened to the mouse during the install last night. It died. Won't work on anything. It's off to Microcenter for a new mouse.

---

### Post by sb73542 on 2005-06-11
[QUOTE=Frihet]Question: Are the quotes around the boot line command arguments required?
[/QUOTE]

Nope, I'm just too lazy to use the proper HTML tags.   :-P

Try this:  Install Hoary.  Then dig up your Warty CD and put it in the drive.  In a command prompt, type (with no quotes) "apt-cdrom add" and follow the prompts.  Then do an apt-get update.  Then in synaptic, look for a package called  linux-image-2.6.8.1-3-386.  After installing it, edit /boot/grub/menu.lst so that it has this section:

title  Ubuntu, kernel 2.6.8.1-3-386 
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda2 ro apm=on acpi=off quiet splash
initrd  /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

(Make sure that you fix the root partition options to be the same as the other entries, appropriate for your system.)

This will allow you to suspend to RAM using hardware buttons or software commands.  Interestingly, with kernel 2.6.10 (hoary stock) you will also be able to suspend to disk using the Gnome shutdown option.  However.... it is a bit irritating that this bug has been introduced which breaks USB functionality after resume, when using kernel 2.6.10 or higher.  Any ways to fix this?  Experts?

---

### Post by john_walsh54 on 2005-06-12
Sorry Frihet,
I don't use quotes. 
It sounds like you can't get ubuntu to work at all!! After the initial Ubuntu boot, you can specify optional parameters before pressing "ENTER to boot" (proceed) with the install/livecd. If you have the Ubuntu livecd type:
livecd apci=force pci=noacpi
If you have the Ubuntu install CD type:
linux apci=force pci=noacpi
then follow the instructions for the install...
If you have a Thinkpad 600X, your lucent winmodem will not work, but I have been down this path already....
Ubuntu 5.04 installs restricted-modules by default, which includes modules for the lucent winmodem. However you need to edit some files to get it working;

1. Select Applications -- System Tools -- Terminal to open a console.
2. Type sudo gedit /etc/modules
3. Add lt_serial and lt_modem to the file to force the modules to load on boot. save modules file.
4. Type sudo gedit /etc/udev/rules.d/10-local.rules to create a new file (10-local.rules) and put these lines in it:
 #ltmodem
KERNEL="ttLTM0", SYMLINK="modem"
5. Type sudo gedit /boot/grub/menu.lst to edit the boot menu. Add pci=routeirq to the "boot" command line i.e. put it after the pci=noacpi parameter. save the file.
6. boot into ubuntu, select System -- Administration -- Networking. Click on Properties for the modem, enter your ISP details under the General tab. Under the Modem tab click Autodetect which should bring up /dev/modem and select Volume Low if you wish to hear your modem dial. Click OK.
7. Click Activate  modem to connect to the internet. If you do not Deactivate your modem before you logoff, your modem will connect on boot.
Thats it. Listing of relevant section in menu.lst file:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro acpi=force pci=noacpi quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro acpi=force pci=noacpi single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Hope this helps. I think thats everything.

Regards

John

---

### Post by sb73542 on 2005-09-13
Any idea if this has been fixed in Breezy?

---

