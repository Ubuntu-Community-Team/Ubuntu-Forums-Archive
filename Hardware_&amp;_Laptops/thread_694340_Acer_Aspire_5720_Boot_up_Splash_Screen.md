---
title: "Acer Aspire 5720 Boot up Splash Screen"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by deepaknr on 2008-02-11
Hello,

I have noticed a strange thing, when I boot Ubuntu on my Acer Aspire 5720 notebook, I never see the boot splash screen. The screen flashes somewhere in between (during the booting process) and I just get login screen. Even during shut down, I don't see any splash screen. Is this common on Acer Aspire 5720 notebook?

Secondly is there a way to see the booting process, some times it takes a longer time to boot and I am quite curious to see what exactly its doing.

Kindly let me know.

Thanks

---

### Post by Yellow Pasque on 2008-02-11
> Secondly is there a way to see the booting process, some times it takes a longer time to boot and I am quite curious to see what exactly its doing.
Boot with the nosplash option (you can edit this in at the Grub menu or add the option in /boot/grub/menu.lst in advance)

As for seeing the splash screen, a lot of people have trouble with that. What kind of video do you have? (lspci | grep VGA). You can also try displaying the splash screen at a diferent resolution by checking the /etc/usplash.conf file.

---

