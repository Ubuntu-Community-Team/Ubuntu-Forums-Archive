---
title: "convert a Dell ChromeBook P22T to ubuntu 22.04"
date: 2023-01-06
forum: Hardware
---

### Post by jgw on 2023-01-06
I have an old dell chrombook p11t I would like to convert to ubuntu.  I did a search on that one and there seems to be a LOT of different ways to go.  That being said I thought that I might ask her about doing this for the best way to go.

Thank you................

---

### Post by jgw on 2023-01-07
OK, i have decided to make a run at this conversion from dell chromebook to ubuntu.  I am trying with the instructions at [https://ubuntu.com/tutorials/install-ubuntu-on-chromebook#3-installing-ubuntu-with-crouton](https://ubuntu.com/tutorials/install-ubuntu-on-chromebook#3-installing-ubuntu-with-crouton).  Started with enabling developer mode.  Followed:
```
To get to Developer Mode, we need to first reboot into Recovery Mode. On most Chromebooks, you do so by turning the device off, then holding down the ESC and Refresh keys while you press the Power button.

Once in this mode, press Ctrl-D. You will be prompted with an opportunity to “turn OS verification OFF”. Press Enter to do so.

When you boot up your Chromebook, it will begin with a warning screen noting that “OS verification is OFF”. You will need to press Ctrl-D to continue. Your device will now transition to Developer Mode.
```

I ended up at starting up the chrombook again.  This means I screwed this up.  I turned off the OS verification OFF and pressed ^D and it took me to startup.  So, I am doing something from the start that isn't right.  Before I do it again I will await somebody to tell me where I screwed up.

---

### Post by bobunderwood99 on 2023-01-07
Hello,

Did you reboot after pressing Enter to turn OS verification off?

Crouton is not actively supported anymore - [https://github.com/dnschneid/crouton](https://github.com/dnschneid/crouton) 

Try Mr. Chromebox instead - [https://mrchromebox.tech/#home](https://mrchromebox.tech/#home)

---

### Post by jgw on 2023-01-08
Thank you for the reply.  


I went to: [https://mrchromebox.tech/#home:](https://mrchromebox.tech/#home:)
My Chromebook: Dell Chromebook 11  3120 Model P22T
Supported: Dell Chromebook 11 (3120) 	CANDY 		&#9989; 	&#9989; 		screw 

I started reading and came across:
Standalone Linux

On many Intel-based Chromebooks, you can simply boot a Linux ISO via the stock firmware's Legacy Boot mode and install like you would on any other PC. When installing Linux via ISO in conjunction with the stock firmware + Legacy Boot Mode, there are sometimes issues booting the install media due to bootloader conflicts (e.g., Syslinux) or setting the graphics mode (GRUB/Ubuntu 16.10) or broken sleep/suspend due to the TPM (all CR50 devices). Because of this, most devices will benefit from running the latest UEFI Full ROM firmware, which should be flashed prior to OS install when running Linux and not dual booting w/ChromeOS. 

According to the paragraph above: I am assuming that, in theory, my dell chromebook can be moved to Ubuntu by simply installing ubuntu (booting up with installation gps?)  Then it gets tricky and wants the latest EUFI Full ROM firmware to be 'flashed'.  I am not sure of that.

There was a lot of stuff in the mrchromebox.tech/#home.  

My problem is really pretty simple  I bought this chromebook for very little money from ebay.  It works well.  I actually have firefox and google chrome currently running as well as hey google.  I also suspect that what I should really do is leave it alone and give it to a grandchild rather than mess with it.   I am saying this because there is really nothing wrong with this machine.  I was thinking of putting a larger ssd in it but after I took off the back and looked around I would have to take off another back just to get to it and I suspect there really isn't enough room to do that on this machine.  

I would be interested in your thoughts on this.

---

### Post by bobunderwood99 on 2023-01-09
What version of Chrome OS (CrOS) is it running? Google is up to v108. If it's reasonably current, using it as-is (not in Developer mode) is probably a low to moderate security risk.

You could try Crouton. Use the minimum number of targets on initial install ([FONT=courier new]sudo crouton [/FONT]-t xfce -r jammy).

If you're not confident about flashing the BIOS - don't. Try booting a "Try Xubuntu" USB drive to see how it goes.

You might want to get a CrOS recovery USB drive made up - se[SIZE=2]e "Recovery option 2: Use USB drive" [/SIZE]in 
[https://support.google.com/chromebook/answer/1080595](https://support.google.com/chromebook/answer/1080595)

---

### Post by jgw on 2023-01-10
Thanks for the reply......

Here is all I have on the dell chromebook:
```
Dell Chromebook 11  3120 Model P22T
Brand:				Dell							Screen Size:				11.6 in
Processor:			Intel Celeron N2840			Model:					Dell ChromeBook P22T
Operating System:	        Not Included					Type:					Notebook/Laptop
Processor Speed:	        2.16 GHz						SSD Capacity:				16 GB
Hard Drive Capacity:	Not Included					Storage Type:				HDD (Hard Disk Drive)
Features:			        Optical Drive, Wi-Fi				Color:					Black
Series:				Chromebook					RAM Size:				4 GB
Most Suitable For:	Casual Computing, Light Gaming		Graphics Processing Type:	Integrated/On-Board Graphics
Connectivity:		Gigabit Ethernet, USB 1.0/1.1, VGA         Manufacturer Color:		Black

```

I am going to be giving this some more thoughts.  I am also wondering if I can boot from a ubuntu 22.04 usb memory stick - results might be interesting.    I also wonder what would happen if I figured out how to replace the existing memory with a ubuntu ssd.  

My problem is time.  I don't seem to have a lot of it.   I was just thinking about setting the chromebook back to new system status and then thinking of doing something with it.  I have diddled with it long enough I suspect.\

Anyway - thanks again!

---

