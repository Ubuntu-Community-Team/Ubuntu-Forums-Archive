---
title: "Running Ubuntu 7.10 on Acer aspire 4520"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by amitabhishek on 2007-12-18
I have purchased this new laptop and want to install Ubuntu 7.10 but unfortunately Gutsy does not detect my graphics card and runs at safe mode (800x600).Basic specs are:

# AMD Athlon 64 X2 Processor - TK-53 (1.7GHz, 512kB L2 Cache combined)
# Nvidia nForce 610M chipset
# Nvidia GeForce 7000M onboard graphics capable of up to 256MB VRAM (shared)
# 2GB DDR2 667MHz RAM 
# 160GB 5400RPM 2.5-inch SATA HDD

I am currently (for time being) running Suse Enterprise linux Dektop(SLED)
which also runs at 65,000 colors which is pretty unimpressive.

Pls help.

---

### Post by jaideep.rayapudi on 2007-12-19
](*,)
Welcome to Aspire 4520. You may just need to load and bear with Windows (only Vista will do on this machine).
Acer insiders are trying to write the drivers for this system so hope it will solve these problems.

---

### Post by Norrad on 2007-12-19
You can run Windows XP quite comfortably on it too. You just have to hunt for the drivers.
I'm dying to try Ubuntu on mine, but I'm going to wait for Acer to release linux drivers for it.

---

### Post by amitabhishek on 2007-12-19
Oh God! thr goes my hard earned money...very proudly in front of retailer I announced that I hate M$ OSs. Now all I am left with a machine that  can't boot, can't connect & can't talk. Ironically this machine came with pre-installed Lipus Linux (!).

BTW I checked this thread [http://oedha.wordpress.com/2007/11/08/acer-aspire-4520-tried-to-kill-me2/](http://oedha.wordpress.com/2007/11/08/acer-aspire-4520-tried-to-kill-me2/) & installed Gutsy but after installation its getting struck up at splash screen.

Thr must be some way out...

---

### Post by nvshaji on 2007-12-19
Ok .. Here is the solution.

at Grub prompt, press 'e'
Select kernel and press 'e' again.
Now add the kernel option "all_generic_id" after "splash"

After booting, you can edit the same in /boo/grub/menu.lst

Wish you all the best with Acer 4520 - I have had a tough time, but now it works like a charm

---

### Post by prodigalson666 on 2007-12-19
> **nvshaji said:**
> Ok .. Here is the solution.

at Grub prompt, press 'e'
Select kernel and press 'e' again.
Now add the kernel option "all_generic_id" after "splash"

After booting, you can edit the same in /boo/grub/menu.lst

Wish you all the best with Acer 4520 - I have had a tough time, but now it works like a charm

How about sound, I have an acer 5520, brand new, couldnt load, stuck at splash screen as well, after seeing all the many threads about sound I'm wondering what worked for you, thanks.

---

### Post by electric_head on 2007-12-19
Hi,

I bought the same notebook a few days ago and I managed to get it running perfectly with Ubuntu 7.10.

As stated before, you should check out this URL:
[http://oedha.wordpress.com/2007/11/08/acer-aspire-4520-tried-to-kill-me2/](http://oedha.wordpress.com/2007/11/08/acer-aspire-4520-tried-to-kill-me2/)
And also this thread on this forum:
[http://ubuntuforums.org/showthread.php?t=510352](http://ubuntuforums.org/showthread.php?t=510352)

I already have wifi, sound and video working fine. Acpi, webcam and other stuff worked out of the box.
The only thing that doesn't work is the Memory Stick reader in the 5-in-1 card reader (I installed MMC and SD dirvers, and it should be working, though, I can't test it).

I haven't been able to test Firewire, IR, or S-Video out yet.

But anyway, don't think you're stuck with Windows, because you CAN use Ubuntu 7.10 on this laptop.

Gnome with Beryl looks just beautiful! :P

---

### Post by prodigalson666 on 2007-12-19
Still cant boot, suggestion did not work, any ideas?

---

### Post by nvshaji on 2007-12-20
Sorry - it should be "all_generic_ide" and not "all_generic_id"

---

### Post by nvshaji on 2007-12-20
So far :

The following works:

-Video at 1280x800 with OpenGL and compwiz
-Sound
-Wireless

To check:
-IEEE1394 to connect to my camcorder
-card reader
-cd/dvd burning

---

### Post by amitabhishek on 2007-12-20
Thanks Guys! Will try this tonight...& ke

---

### Post by eabhi on 2007-12-28
Hey even I have the same config as mentioned in the 1st post. Here is what I have done

1. Got graphics card detection problem while trying to start Ubuntu 7.10 in Live CD. So started in "Safe Graphics mode" (runs in 800x600 resolution) and finished installing in the same mode.
2. Sound, WiFi and Display were not OK.
Installed Restricted Drivers for nVidia (nvidia-glx-new). You would need to enable all the four repositories in "Adminisration -> Software Sources". Then Manually search for the Acer monitor and set the resolution to 1280x800. Enable all the the 3D Effects
3. Follow the below mentioned post for getting sound enabled. Work absolutely fine.
4. Bluetooth Works Out of the Box
5. Need to try WiFi soon to get everything working. Will update here if I am able to do that uccessfully or will ask more doubts

I have following issues now

1. The Resolution keeps on getting resetted to 800x600 whenever I reboot the lappy and need to manually go and change it to 1280x800
2. The eth connection number keeps on incrementing like eth1, eth2, eth3,... everytime I reboot the lappy.

Second one is OK, but does anyone has a fix for the 1st problem.

Cheers
eabhi

---Edit: I have got the Solution for the Resolution problem... here it is

1. Make sure the restricted driver is installed (in Synaptic search for nvidia-glx-new)
2. Execute this command in a terminal:
              sudo dpkg-reconfigure -phigh xserver-xorg
3. Open Restricted Drivers Manager and enable the nVidia driver.
4. Reboot, and you should be good to go.

Hope this helps..


> **electric_head said:**
> Hi,

I bought the same notebook a few days ago and I managed to get it running perfectly with Ubuntu 7.10.

As stated before, you should check out this URL:
[http://oedha.wordpress.com/2007/11/08/acer-aspire-4520-tried-to-kill-me2/](http://oedha.wordpress.com/2007/11/08/acer-aspire-4520-tried-to-kill-me2/)
And also this thread on this forum:
[http://ubuntuforums.org/showthread.php?t=510352](http://ubuntuforums.org/showthread.php?t=510352)

I already have wifi, sound and video working fine. Acpi, webcam and other stuff worked out of the box.
The only thing that doesn't work is the Memory Stick reader in the 5-in-1 card reader (I installed MMC and SD dirvers, and it should be working, though, I can't test it).

I haven't been able to test Firewire, IR, or S-Video out yet.

But anyway, don't think you're stuck with Windows, because you CAN use Ubuntu 7.10 on this laptop.

Gnome with Beryl looks just beautiful! :P

---

### Post by s.jesudasan on 2008-01-16
> **nvshaji said:**
> Sorry - it should be "all_generic_ide" and not "all_generic_id"

can anyone explain me how to add this 
whether i should just type it after giving 1 space

---

### Post by s.jesudasan on 2008-01-17
> **s.jesudasan said:**
> can anyone explain me how to add this 
whether i should just type it after giving 1 space

Finally my aspire 4520 works on 
ubuntu 7.1. Thanks for all ur help

Now can i install beryl 
will it work ????????????????????????

---

### Post by cdinz on 2008-03-02
> **nvshaji said:**
> Sorry - it should be "all_generic_ide" and not "all_generic_id"

TQ that helped.....

---

