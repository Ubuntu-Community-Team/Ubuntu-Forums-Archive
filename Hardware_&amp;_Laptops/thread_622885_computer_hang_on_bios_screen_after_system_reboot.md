---
title: "computer hang on bios screen after system reboot"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by macmus on 2007-11-25
Hello,

I have installed on my nootebook toshiba A210-129 ubuntu gusty as a secondary system (it has also the windows vista installed with laptop).
I am having problem after i restart my system on Ubuntu. It simply hangs on bios splash screen ( the one with toshbia in the middle of screen before the bootloader starts) - i have to turn off and then on the laptop to make it work.

The problem however does not occure on windows system. After i press reboot the laptop reset, comes to bios boot and then to bootloader section. 

There was no problem also when i had fedora 7.

I would apreciate your help at this matter.

Thanks in advance.

---

### Post by catfishk on 2007-11-25
may i ask which video card is in your laptop?  mine did this before upgrading to the newest fglrx (8.43.2) driver (AMD/ATI X1300) and removing the 'vesa=xxx' line from the grub parameters

 for my issue, it seems the card didn't power down or became locked in a peculiar state on reboot, suspend/hibernate, and sometimes shutdown.  using the virtual terminals would also hang the video

 good luck!

---

### Post by macmus on 2007-11-26
> **catfishk said:**
> may i ask which video card is in your laptop?  mine did this before upgrading to the newest fglrx (8.43.2) driver (AMD/ATI X1300) and removing the 'vesa=xxx' line from the grub parameters

 for my issue, it seems the card didn't power down or became locked in a peculiar state on reboot, suspend/hibernate, and sometimes shutdown.  using the virtual terminals would also hang the video

 good luck!

thx for answer

my grafic card is HD2600 and i have installed 8.42 drvier for it and successfuly run AIXGL ( with all the bugs, scrolling slowdowns but it works :) 

i have installed that using envy .. i will get new envy now and try to install 8.43 drvier 

also i have problem while switching to console ( black screen occurs ) no mater what VGA=... parameters do i use :( have u have same problem laso

---

### Post by Princegiri on 2008-01-04
I have the exact same issue but 

i did not have the problem for a month after installing ubuntu (7.0.4).......
it suddenly cropped up around the time i installed virtualbox on my system (irrelevant)

i have a HP pavilion dv9505tx laptop and it runs on 8600GS nvidia card.

this problem happens so rarely that i can never find out what exactly the problem is..... its so annoying... i contacted HP care about it....waiting for a reply.....

dont know if its the bios, ubuntu or the card being set in some state like this thread says....

---

### Post by ADK01 on 2008-06-09
Exactly the same problem here, I am running Debian/GNU Linux etch
kernel 2.6.25 on a Thinkpad T60, my graphics chip is an Intel GMA 945
 This problem happens nearly every time i reboot, has anyone found a solution to this yet?

---

