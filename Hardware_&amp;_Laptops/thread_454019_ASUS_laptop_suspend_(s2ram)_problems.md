---
title: "ASUS laptop suspend (s2ram) problems"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by simoncullen on 2007-05-25
Dear Ubunters,

I've never been able to get my [ASUS F3Jp laptop]("http://au.asus.com/products.aspx?l1=5&l2=26&l3=316&l4=0&model=1358&modelmenu=2") [specs] to go into suspend.  I'm not entirely sure why this is, as there are no other reports of the problem so far as I know.  Recently I tried using s2ram.  I have discovered that I can cause the machine to go into suspend by booting to a minimal state with the parameter "init=/bin/bash".  The system will then suspend correctly with the command "s2ram -f -p".  (I have tried the other combinations on the s2ram website too.)  So that was nice.  

When I try it after letting the machine boot---*even* after killing gdm and removing the fglrx module---the machine wont sleep.  It switches to VT1 and then just sits there.  I can switch VT's with Ctrl+Alt +F(n), but I cannot type into any of them and i cannot issue alt + ctrl + del to restart the system.  So although it is not, it is for all intents and purposes frozen and I have to hard reset it.  The same thing happens from within X.

I've read the forums and mailing lists and can't seem to find anything else to try.  Any help wouldl be enormously appreciated!

Thanks,
Simon

---

### Post by simoncullen on 2007-05-25
UPDATE:  

By editing "/etc/default/acpi-support" to:

MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

the system now will go into sleep---well, kinda.  The screen will turn off, and I think the harddisk will even stop.  But the fan doesn't, and the power light does not start flashing as it should to indicate suspend.  Still, I can press caps lock and see the light changing---so I know it is not completely frozen, though the screen will not return.

Cheers!

---

