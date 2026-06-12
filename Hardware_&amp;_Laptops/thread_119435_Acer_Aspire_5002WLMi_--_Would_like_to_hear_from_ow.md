---
title: "Acer Aspire 5002WLMi -- Would like to hear from owners"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by gmc on 2006-01-19
Hello Folk,

Well I'm officially 40 :( now and have decided buy myself a birthday present :razz: .

From the specifications of this [laptop ]("http://www.notebookdepot.com/specsheet.asp?productid=453054537")and am giving it consideration.

I'm interested in hearing how successful you have been with Ubuntu
Breezy on it. I'm specifically interesting in hearing about how/if wireless 
works and generally how happy you are with it,

Thanks
G.

---

### Post by Andrew Shimmin on 2006-01-19
Hi,

I've got the Acer travelmate 4402, which is the business version of that computer (plus dedicated video; ATI x700), and have been thrilled with it. I was able to install Ubuntu very easily, with three problems. The modem doesn't have a free linux driver, so it doesn't work without a third-party $15 one. The wifi doesn't work out of the box, but it seems pretty easy, so long as you have a LAN internet connection to configure it with, to workaround that. The third problem is that the clock runs too fast, by a factor of two. There are workarounds for this too (the one for the 64 bit Ubuntu build seems easier and failsafe; I haven't actualliy gotten the 32 bit one to work, yet).

My only complaint about the hardware is that the screen is a little darker than most. Oh, there's also a minor issue of taste: the buttons flanking the up arrow are  &#8364; and $. So, I occasionally enter either, unintentionally.  Good luck.

---

### Post by lzfy on 2006-01-19
I have an Acer Aspire 5024, everything works out of the box except wireless, maybe that works too but i haven't tried that yet.

---

### Post by gmc on 2006-01-24
Hi Guys,

Thanks for the feedback. I did get an Acer, but not the 5002. If you're interested in which Acer I did get... [read here]("http://ubuntuforums.org/showthread.php?t=121125")

G.

---

### Post by digitaldoug on 2006-02-23
I have owned the 5002WLMi for about 6 months now.  I consider this the best laptop I have ever owned (out of about 10 in the last 6 years).  I upgraded to 2Gb RAM and recently to Breezy 64 bit kernel.  I tri- boot Windows32/32bit and 64bit Ubuntu.  (The 32 bit Ubuntu is still Warty).  Since updating to Breezy, I find little need for the 32 bit kernel (64 Breezy seems to run 32 bit programs just fine).
The 32/64 bit kernels share  /boot  and  /home  --  /  is in a separate partition.

My (small) Issues are:
1) Short battery life -- particularly with Linux.
2) Synaptic pad is off to the right and too sensitive.
3) Wireless is still a problem (however it worked briefly in 32 bit using ndiswrapper). Haven't got 64 bit ndiswrapper to work yet.
4) The 64 bit Warty kernel would not boot half the time -- freeze during boot.
5)  I get this output in dmesg (in all kernels) every 15 seconds:

[20650.850374]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[20650.850385] search_node ffff81007afa0e00 start_node ffff81007afa0e00 return_node 0000000000000000
[20650.850393]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81007afa0c00), AE_NOT_FOUND

6) I vaguely recall having to edit the /etc/X11/xorg.conf file a little to get the display to use the full screen (1280 x 800) on Warty.

I have not spent a lot of time trying to fix the above problems, however any help would be appreciated.
BTW, this is my first post

digitaldoug

---

### Post by Crayoneater on 2006-02-23
i have an acer aspire 5002wlmi and it works great...i get about 2 and a half hours of battery life....i use 32 bit breezy, and wireless works great with ndiswrapper....to install i had to use the vga=771 option.....to get it to read the battery information correctly, i had to add the kernel boot option:
 acpi_os_name=Microsoft Windows 2000 
to /boot/grub/menu.lst

other than that it has worked very well....i installed gtkwifi to take care of the wireless card....it connects my wireless on startup.....i actually originally installed hoary and then updated to breezy by changing the repositories....i guess that's all...my sound worked until i updated to breezy, but then all i had to do was run alsaconf and it set my sound back up again, so it's all working again.....i installed the graphics driver for it and use the sis driver now.....i really haven't had any problems with this laptop.....the person in the above post might want to try that kernel option acpi_os_name=Microsoft Windows 2000  cause that fixed the acpi errors for me.....

---

