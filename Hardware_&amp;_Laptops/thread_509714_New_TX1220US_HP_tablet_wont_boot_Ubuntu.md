---
title: "New TX1220US HP tablet wont boot Ubuntu"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by Spectre31337 on 2007-07-25
:confused:I have a HP TX1220US Tablet PC I bought it to replace my Acer 5670. It came preinstalled with M$ Vista and i would prefer not to use it. I was a Beta tester on Vista but have yet to use it for day to day use (nor do I plan to start now) The fist thing I did was put in the Ubuntu 7.04 Live disk and try to boot into the OS... No joy... after 30 minutes of waiting nothing happened. I rebooted and tried in graphics safe mode... but still nothing. I have try Sabayon and it will boot fine and install correctly but it does not support my sound card, webcam, or my wireless card (it will connect but I can only browse the net and sub 56K speeds) Does anyone have this laptop and gotten Feisty to boot? I have also tried the Alpha 3 Gibbon but that wont boot either. Any help would be greatly appreciated

---

### Post by Spectre31337 on 2007-07-26
Any ideas?:confused:

---

### Post by emm721 on 2007-09-27
I've got the same laptop and the same problem. It really sucks, because even when ubuntu installs I doubt the touchscreen would work.

---

### Post by bradleyb01 on 2007-11-14
I just installed 'Gutsy' for AMD64 on my tx1220us in text mode and I had to add the 'noapic' (minus quotes) option at the end of the 2nd boot line (you do this by using 'e' to edit on the grub menu). I also made  sure that the remote was OUT of the express card port.

I then edited the /boot/grub/menu.lst and added noapic on the 'kernel' lines after 
## ## End Default Options ##

It boots great mow and is very fast, so I am very pleased so far.

I am working on making sound, WLAN and touchscreen working. I will update my progress if anyone is interested.

---

### Post by emotional1 on 2007-11-22
I am very much interested in your progress as I am fed up with Vista.  I have been using Linux for the past 5years and recently bought this tablet/laptop tx1220us for some required programs at the university I now attend. Are you dual booting this laptop or are you just running Ubuntu?
Any information would be greatly appreciated.

Eric](*,)

---

