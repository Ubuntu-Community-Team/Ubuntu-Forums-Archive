---
title: "Install options for dual-disk dual-boot?"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by Dirtpile on 2009-07-21
I haven't yet but I want to install Jaunty as a dual boot to XP.
My question is: In order to install Jaunty on my second HDD from a Live Disk should I select
1) Install alongside Windows (I assume this option will only install on the XP drive) or 2) Use entire disk and select the second drive from the drop menu.
 
I am aware that Grub should prompt to add XP as a boot option either way but is there anything i should watch for?
 
Also since I'm currently stuck with Dial-Up and really only want to "Get my feet wet" with Linux for the time being, is there an easy and safe way to set XP to boot by default? 
(meaning that if left to start-up unnattended, it would boot to XP instead of Ubuntu.)
Will Startupmanager do this?

---

### Post by gastly on 2009-07-21
Yes, select the second HD from the menu to install in it, Ubuntu will itself detect the Windows install and add an option to boot from it in Grub.

As for the default one, yes you can use the StartupManager to change the default option to Windows, instead of Ubuntu.

Good luck ;)

Cheers :)

- gastly

---

### Post by Dirtpile on 2009-07-21
Thanks for the verification.
 
I was pretty sure that's how it would go but wanted to be sure before I tried installing.
 
I have dual booted (SuSe 9.1 and XP) on my old computer before but it was on the same drive so I wasn't exactly sure.

---

