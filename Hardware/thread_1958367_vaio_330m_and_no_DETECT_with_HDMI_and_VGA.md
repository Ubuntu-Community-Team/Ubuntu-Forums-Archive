---
title: "vaio 330m and no DETECT with HDMI and VGA"
date: 2012-04-14
forum: Hardware
---

### Post by scordato on 2012-04-14
Hi guys
I am new and i don't know if this is the best forum area for my problem.
I have a sony vaio vpcf11m1e notebook with intel i5 and invidia 330m with 1 gb ram ,HDMI and VGA ooutput.


i tried to connect my ubuntu 64BIT 11.10 with external monitor but the OS don't find it 

I tried :

1   with old nvidia drivers and recent drivers (295.xx or similar)  but the NVIDIA XSERVER don't find the external monito when i do DETECT.

2 with hotkey FN+F7 but ubuntu give me same screen.


3 I connected my HDMI to external first to boot but nothing , Ubuntu doesn't detect it.

4 Tried with 3 differents monitor and tv but nothing ,i received the NO SIGNAL  answer from them.

Help me pls because i need go to external monitor

---

### Post by efflandt on 2012-04-14
Are you using **nomodeset** kernel boot parameter?  Without that the monitor (DVI to HDMI HDTV) on my desktop says "no signal" with nvidia drivers after the grub menu when I boot 64-bit 11.10.  I don't need that boot parameter in 64-bit 10.10 when it was using the same exact nvidia x-swat driver version.

I think that has something to do with the different way that 11.10 boots, and nouveau and nvidia cooperating as modules instead of being mutually exclusive in kernel mode setting.

If that works when editing the grub menu during boot to include **nomodeset** in the linux line (that includes **quiet splash**), edit /etc/default/grub and sudo update-grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

---

### Post by scordato on 2012-04-14
Sorry for questiOn but i am newbie so  : what is nomodeset?how can i configure this Parameter?

---

### Post by gordintoronto on 2012-04-14
To configure nomodeset:
open Terminal and enter this command:
gksudo gedit /etc/default/grub

about a dozen lines in, you should see:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Add the word nomodeset after splash:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

Save the file, exit, then one more command:
sudo update-grub

Now reboot.

However, that might not be the actual problem. Many laptops have a magic key combination to cycle through built-in display, external display, both. Look at the manual for your Sony to see if it uses such a thing.

Do you dual-boot? Does it work in Windows?

---

### Post by scordato on 2012-04-14
yes i have dual boot with windows 7 64bit .

I tried to setting nomodeset ,but nothing happened

---

### Post by scordato on 2012-04-17
Up the thread.

Nobody can help me about this my problem.
Last day i needed use my laptop for karaoke and i used windows os with is sloooowly startup instead Ubuntu.

---

### Post by scordato on 2012-04-20
up

---

