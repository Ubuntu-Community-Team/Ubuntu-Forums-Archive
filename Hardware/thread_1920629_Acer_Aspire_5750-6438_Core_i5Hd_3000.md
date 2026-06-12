---
title: "Acer Aspire 5750-6438 Core i5/Hd 3000"
date: 2012-02-05
forum: Hardware
---

### Post by Plasmah on 2012-02-05
Hi all

I'm a newbie here and searched the forums but could not find an answer.

I just purchased a New Acer Aspire 5750 i5 laptop yesterday and want to wipe Windoze off it and install Ubuntu 11.10. Anyone know if this lappy is Ubuntu friendly before I wipe windows? I checked the Ubuntu friendly engine and it says the Model 5750g is good. I'm thinking it's a go. Just please anyone here with the same spec laptop reply so I know for sure.

Thanks all

Update: Ubuntu 11.10 install on my 5750 went great with 2 minor issues. 1. Can't adjust screen brightness. And 2. OS did not install Intel HD 3000 video drivers.

OK Finally found a viable solution to the brightness control issue!
I tried many of the fixes on the forums here and none worked, Here's the one that did.

If you duel boot like me then when your computer is at the GRUB screen you can change the brightness there before you choose what OS to boot. FINALLY! ;). Please post here if it worked for you. I would love to hear if it helped you as well.

---

### Post by wvu_ravens_fan on 2012-08-05
I just bought an Aspire 4830t and had the same issue.  You need to modify your grub file as follows.  This will allow your fn+arrow key to adjust the screen

1. Open a terminal (Program - Accessories - Terminal)
2. Type in "sudo gedit /etc/default/grub" (without the "")
3. Find the line that says: GRUB_CMDLINE_LINUX="quiet splash"
4. Edit it so it says: GRUB_CMDLINE_LINUX="quiet splash acpi_backlight=vendor"
5. Save and exit
6. Run the command "sudo update-grub" (again without quotes of course)
7. Reboot and enjoy!

Note my orginal files showed GRUB_CMDLIN_LINUX=" "

If you want Ubuntu to recognize the video card install Mesa.  Just fine mesa-utils in synaptics.  Then you will see intel sandybridge in the system info

I hope this helps

---

