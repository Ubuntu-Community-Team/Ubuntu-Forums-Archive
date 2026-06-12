---
title: "Ubuntu-8.10 Grub Memory Test Problems"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by begarkitta on 2008-12-24
I have installed Ubuntu-8.10 (Intrepid Ibex) from a Live CD. Installation was smooth and completed without a problem. The problem started when I tried to boot up:

1. There is an entry for Memtest-86+ in the grub. This memory test runs for well over an hour and restarts the whole test cycle when it completes. After the first test that lasted for more than an hour my RAM was given a clean certificate.

2. Since I do not want to wait for 1 hour every time I want to boot my Ubuntu, I want to know how I can skip this memory test. I tried to edit menu.lst file booting through the Live CD. But permission was denied. In any case I dont think I could have made a successful job of editing a Linux file -- my current knowledge does not go that far.
Please help

---

### Post by Yes on 2008-12-24
You should never need to run memtest unless you think there's a problem with your RAM or you've been overclocking.  The default boot option should be Ubuntu, just let it boot into that.

---

### Post by begarkitta on 2008-12-25
Thanks a lot for that quick reply. I thought as much that Memtest is an option. But in my grub menu.lst it is entered as a default. So, if I want to boot Ubuntu, I have to go through this memtest and I cannot bypass it.

Where then is the problem? What do I do.

Thanks again.

---

### Post by smartboyathome on 2008-12-25
Here's a simple way of changing it:

Alt-F2
gksu gedit /boot/grub/menu.lst
change which one has the "default" setting at the very bottom.

That should help. :)

---

### Post by begarkitta on 2008-12-25
Thanks, Smartboyathome.

When and where  do I hit Alt+F2?

I tried Alt+F2, serenely and frantically at various stages of stage of booting and after memtest started. No magic occurred. More help please!

Thanks again for taking time.

---

### Post by FuturePilot on 2008-12-25
> **begarkitta said:**
> Thanks, Smartboyathome.

When and where  do I hit Alt+F2?

I tried Alt+F2, serenely and frantically at various stages of stage of booting and after memtest started. No magic occurred. More help please!

Thanks again for taking time.

From the desktop.

---

### Post by begarkitta on 2008-12-25
smartboyathome,

I dont think I have explained my problem correctly; you see, the system never boots; the only non-xp option I get in the bootloader goes straight into a memtest which is a never-ending cycle. There are three lines in the bootloader screen none of which boots. The only  line that clicks is this memtest on. Although I am no Linux Pundit, I have used mandriva and Fedora before and must have installed linux at least a 50 time now. This thing has never happened. I have taken this as a challenge. I am using a multi-boot CD (has ubuntu, kubuntu, xubuntu, edubuntu, mythbuntu and ubuntustudio, all live Environment [you boot and then install])that came free with a linux mag.

---

### Post by caljohnsmith on 2008-12-25
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your Grub menu problem might be.

---

### Post by begarkitta on 2008-12-25
caljohnsmith

Thanks for your reply.

Thanks. I entered your command and this is what I got:

 [http://home.comcast.net/~ubuntu_grub/boot_info_script.txt](http://home.comcast.net/~ubuntu_grub/boot_info_script.txt)
Resolving home.comcast.net... failed: Name or service not known.
wget: unable to resolve host address `home.comcast.net'

I also reproduce below the three lines found in my grub (Ubuntu-8.10, Inrepid Ibex)

-- uuid 00b72c71-9a9c-4149-8ccb-b3ee4361f429

-- kernel   /boot/memtest86+.bin

-- quiet

Thanks

---

### Post by caljohnsmith on 2008-12-26
So it looks like you have an internet connectivity problem, or at least a DNS problem since your computer couldn't successfully look up the "home.comcast.net" host. Are you using the same computer to access the forums? How about following that link from whichever computer you have that has internet access, save the "boot_info_script.txt" file, and then transfer it to your Ubuntu Live CD or whatever you are using now for Ubuntu. If you put the "boot_info_script.txt" on your Ubuntu desktop, you can run it with:
```
sudo bash ~/Desktop/boot_info_script.txt
```
Let me know how that goes.

---

### Post by begarkitta on 2008-12-29
Hellow,

I tried your recipe over the weekend but could not get it work; I think my knowledge does not go that far yet. I just installed Fedora-7 and settled down to enjoy it.

Thanks a lot. I'll grow up and come back to pick your brains.

---

### Post by stchris on 2009-04-17
Well... I'm afraid I have the same problem. I've tried editing the bootfile straight from the boot loader but I don't really know what to put in. The weired thing is that the system has been working before. 

Can anyone send me the normal boot entry for Ubuntu 9.04 rc?

Thanx in advance.

BTW: I tried reinstalling but that didn't work out either.

---

### Post by frodon on 2009-04-17
Moved to installation & upgrade forum.

---

