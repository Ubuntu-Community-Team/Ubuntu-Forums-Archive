---
title: "Pent 4 HT - SMP 686 kernel"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by kondor on 2006-09-13
I cannot get the SMP 686 kernel to work on a Toshiba with P4 HT. Of course, the install uses the 386 kernel and that works, except without HT. Any of the 686 SMP kernels  result in a corrupted boot display as it prints on the  screen and then a freeze when Gnome opens. The display in Gnome is ok, just frozen along with mouse cursor.Everything locks up.

What is lacking or added in the Ubuntu SMP kernel that bombs this thing? Obviously, the change of kernels lasks a corresponding transfer of hardware info to the new kernel, or some such.

I currently have SUSE 10.1 in it, 2.6.16-21 SMP and it works. However, the SUSE installer is somewhat intuitive and matches kernel to hardware. I currently run Dapper with the 2.6.15-26 -46 SMP kernel on this desktop without difficulty. Never have trouble on a desktop with Ubuntu, only the laptop.

I am guessing that I will have to compile an SMP kernel to get Ubuntu to work on the laptop some reason. I wanted Ubuntu on the laptop, not SUSE. But, I have to go with what works.



Thanks!

---

### Post by Herman on 2006-09-16
Hello, kondor,
Here is an excellent howto by Indras, [**HOWTO: Change bootup resolution**]("http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters"), please read that how-to through a few times before doing anything.

My idea for you to try booting up from [Grubs' Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
There are two things to try simultaneously from Grub;s CLI.

Boot up in recovery mode. 
Tip: If you need to refer to your menu.lst file to remind you the right commands for doing that, do a 'cat /boot/grub/menu.lst' to check what to type in CLI mode Grub to boot into recovery mode.

Also during booting from Grub's CLI, try setting  a vga parameter to see if you can keep your text display from being corrupted.
Maybe try this 'scan' option, quoted from Indras's excellent how-to,> You can set "vga=ask" in your menu.lst file to force the kernel to ask you what resolution you prefer each time, but you will choose from a rather small list of options. You can type "scan" to have it check your hardware to see which modes it is capable of, but this is mainly for compatibility issues, and it won't give you as complete of a list as above, and you cannot type in 791, or 0x317 here, only a number from 0 to 9 from the list it gives you. 

Then do '[sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html")' when your computer boots up to see if you can find a more suitable video driver.

Then reboot into Gnome.

I hope this will be helpful to you,
Regards, Herman :D

---

### Post by kondor on 2006-09-18
Herman,

Thanks for the reply. I saw on my other Ubuntu machine that there had been a kernel update (47) for SMP and decided to try it again. Also, this time, I selected KDM and it worked. Then, I eliminated KDM, and it worked with GDM, so I am in business again.

I also note that in KDM and KDE, the graphics are not as good, in that screen brightness suffers compared to Gnome. For this little Toshiba, GDM is definitely better.

I still have the corruption of the boot screen which occurs late in the process. The regular contents of the screen are correct as I can see the report at the end of the line, as in "ok" but the entire process is overwirtten by gibberish. But, since I get into GDM without difficulty, I am happy. I'll simply edit to silent and not worry about it.

temp running 44 - 49 C

Thanks again.

So, this is a Toshiba A-65-S1054, Pent4 HT with DVD/CD, ATI chipset and ATI shared graphics, 1 gig memory, of which 960 is available (other dedicated to graphics). The ethernet works automatically with the installer requesting which is default, wireless or ethernet. I have not used wireless but since the card is recognized I assume it will work. ACPI is good and although I don't have any hard temp readings, I use the highly scientific method of holding a tissue over the fan outlet. The fan works variably in  Ubuntu and when it is getting warm, the tissue is blown horizontally by the force of the fan. So, it works! I have avoided any suspend nonsense, although it would be nice to have it. I simply remember to shutdown before I close the lid. The SMP latest or 386 latest works fine. All USB works and mouse pad works. I never use dual monitor. Battery time is normal as this one is good for perhaps 2 hours max.

Thus, Ubuntu is working on this laptop with nearly automatique config. I  note that GDM gives a better graphics display than KDM for this machine. Perhaps the display could be tweaked at command line, but it is simpler just to use GDM. This laptop is about 3 years old.

---

