---
title: "Acer Aspire One ZG5 Grub problem, then kernel panic."
date: 2009-03-28
forum: Hardware
---

### Post by abisdad on 2009-03-28
[LIST]
[*]Ubuntu 8.04.2. kernel 2.6.24-23-generic
[*]Acer Aspire One ZG5 (1GB RAM, 150GB HDD)
[*]Used USB boot, wired LAN, Australian mirror.
[/LIST]

Read history below, then I have two questions:

1/ How do get the USB to go back to the install mode again?
2/ What do I do differently to stop Ubuntu crashing?


Hi, I'm no Linux expert, but have played on and off for a while.  So when the school I work in said they were going to give us all an Acer Aspire One ZG5, (1GB RAM & 150GB HDD) - but they won't be ready for a month or two while they re-image them, (with XP Pro instead of the XP Home) - I borrowed one to try to install Ubuntu as a duel boot using grub.

Used [[COLOR="Blue"]_USB boot as per this post_[/COLOR]]("https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html"), and network cable connection.

Install took quite a while to download, but worked, so while it was re-booting I switched it off so I could sleep, on the first re-boot after downloading from the mirror.

The next morning, switched on, leaving the USB in but not pressing F12 to boot from it, and the system came up with a blank screen, which I watched for 5 mins - no sign of activity (no LEDs flashing, etc).

I had expected GRUB to boot, or maybe NT boot loader, but nothing.

Re-booted again, and this time pressed F12, expecting to go back to load the USB installer, but (I think) what happened was that it tried to boot Ubuntu, and after a load of stuff scrolling up the screen, informed me that there was a Kernel Panic, and it was trying to kill itself! (well the init anyway...)

"Oh bugger!" thought I, now what?  So I rebooted, F12ed again, and this time it came up with GRUB!?! The following choices were offered:

Ubuntu 8.04.2. kernel 2.6.24-23-generic
Ubuntu 8.04.2. kernel 2.6.24-23-generic (recovery mode)
Ubuntu 8.04.2. memtest68+
Other operating systems:
Windows NT/2000/XP
Microsoft Windows XP Home Edition


Both Ubuntu kernel options crashed differently each time (some output is at the bottom of this post.)
Ubuntu memory test tested OK.
Windows NT/2000/XP sometimes went into error state, saying 
"Starting up...
NTLDR is missing
Press any key to restart" then after pressing a key
"GRUB Loading stage1.5." and just hangs... and sometimes went into Acer recovery!
Microsoft Windows XP Home Edition told me that it was starting up... (but didn't - mostly, it just hung there!) (Just managed to get 

Sometimes it will boot into XP Home, but if you've booted from USB first it quite often won't! (Like NOW!) So I just carry on rebooting using F12 and USB, then after a while it decides to work again... (I hope :-)) It did after the NT/2000/XP option hung again...

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I work in a public Secondary School in Adelaide, we have about 1400 pupils, 130 odd staff and about 800 PC/laptops - all of which are Micorsnort, (+ two overworked good MS techies), I would love to be able to flash a working Linux system at the senior management and say "Look, an alternative, partly created in Oz which is most likely going to be the future of the world, please expose our kids to it - just a bit!"

Thanks for any help - and I think the Aspire One is very cute, battery lasts 6 hours +, and if I can get Linux working too it will be fantastic.

Rob.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I have tried to add a few of the error messages below, these were all trying to boot from GRUB after F12ing, then selecting 1st Ubuntu option:

"BUG: unable to handle kernel paging request at virtual address 46d2c54a"

"EIP: [<        >] raise_softirq_irqoff+" ..... then repeats...

"EIP: [<c0131a80>] cpu_callback+0x10/0x250 SS:ESP 0068:f7c65c65
---[ end trace <a different no> ]---
Kernel panic - not syncing: Attempted to kill init!"
 

"Bug: Unable to handle kernel paging request at virtual address 61a37bd8
printing eip: c031dfff *pde = 00000000
Recursive die() failure, output suppressed
---[ end trace 20e10afb16ef0b15 ]---
Kernel panic - not syncing: Attempted to kill init!"

---

### Post by abisdad on 2009-03-29
Update.

I think it's due to the kernel 2.6.24-23, but how do I choose a different kernel using a USB? The last time it just downloaded from the nearest mirror I found.

Also how do I get it to re-install? 

Each time I boot from my USB, it now goes straight to GRUB, and doesn't give me a choice to partition/install or even go to the command-line base system.

Any help much appreciated.

Thanks.

---

### Post by Garratt on 2009-04-01
bit of a double post but anyway, I'd search the web for the grub boot options, theres a way to enter command mode by pressing C then entering in data, I just have no idea what to enter, or what will allow you to change kernel number...
That and it is a possibility that being it's a fresh install there may not be any previous kernels, so.. you may need to reinstall but don't let it update the kernel :P haha i got nfi

I just know that if you can get it to run in a prior kernel then you can simply start-up terminal and:

cd /boot/grub/
sudo nautilus menu.lst   *or*
sudo vi menu.lst

and just change the kernel number to a previous version.

Ubuntu 8.04.2, kernel 2.6.24.21 or 2.6.24.19...

just not 23, as it seems to hate acer aspires.

EDIT: actually just use the live cd or live usb in your case and load ubuntu without any changes, then go in to terminal and mount the drive and then edit menu.lst that way

---

### Post by Garratt on 2009-04-01
load up live cd without changes to your computer.

when it starts up open terminal 

now mount your drive and edit the list
```
sudo mkdir /media/slash

mount /dev/*your drive* /media/slash

gksudo gedit /media/slash/boot/grub/menu.lst
```

*your drive* being the drive ubuntu is located. you can find this out by typing fdisk. usually its sda1 so you would type:
mount /dev/sda1 /media/slash

this should be it, now restart and grub should load a previous kernel

---

### Post by abisdad on 2009-04-02
Thank you Garratt, 

I'm sorting out a USB to try that now. Will let you know how I get on.  I had assumed that I would only have one kernel as it was a new install.

Rob.

---

### Post by abisdad on 2009-04-10
Kind of resolved the problem, but had to wipe the hard disk, and start again!

I think the main problem was:

When I tried the Ubuntu Live install USB, over the top of my first one described above in my first post, I didn't manage to format the USB correctly.  This stopped GRUB running properly - and hung after displaying the word GRUB on screen!

I got around this by using a "HP USB disk storage format tool" (downloadable from the WWW), then did it and it worked brilliantly.


Before I sorted the boot USB, I installed XP Pro, using the whole disk, then discovered the USB disk worked, so made the XP partition smaller and installed 8.10.  It worked great - until I came to boot XP Pro again, then came up with the error:

Starting up...

A disk read error occurred
Press Ctrl+Alt+Del to restart

AND it somehow stopped the external USB CD from booting the XP Pro CD to recover my XP Pro, which I had just spent a day getting just right!

Not impressed, trying to get the USB CD to boot from GRUB now, but I'm stuffed time wise, I'm off in a day for the family holiday, and missus & daughter don't want me bringing a bust PC along...

Rob.

---

### Post by n2space on 2009-05-26
I had a similar problem with Ubuntu8.04. I installed 2 512m mems and Ubuntu had a kernel panic, saying it could not sync.  I put the 2 256m mems back in and it works like it used to. I wonder if I need to change kernels?

---

