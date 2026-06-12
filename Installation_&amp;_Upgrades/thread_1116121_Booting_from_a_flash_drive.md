---
title: "Booting from a flash drive"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by mikemwa on 2009-04-04
I want to be able to boot my computer with Ubuntu from a flash drive. If I boot from the CD, go to Administrative, and make a startup disk the flash drive will boot but seems to just do the same as if you were to boot from the CD.
If I do an install from the CD from when it first boots up it seems to install and takes a long time. 
When I try to boot from the flash drive it doesn’t and goes straight to XP. If I try to see the directory of the flash drive it says the flash drive is not formatted and asks if I want to format it.
What steps do I need to do to do a true install on a flash drive? I have version 8.10

Mike

---

### Post by ronparent on 2009-04-04
First off, if you have ubuntu installed to your usb drive, it will not be seen by windows. Windows does not read a linux partiotion! DO NOT ACCEPT THE WINDOWS OPTION TO REFORMAT IT, or you will have to reinstall Ubuntu. When inserted, the flash drive should look exactly like the cd until you customize the desktop! Unless I'm misreading what you have written, It sounds like you have a bootable ubuntu install on your flash drive. If so, you will see a grub menu on booting (for a default 3 seconds) which will also allow you to secect booting windows. When drive is not inserted you should boot directly to windows. This is a sweet setup, incidently, that allow you to carry your your complete operating system with files to any computer with the bios set to boot from a usb drive if inserted!

---

### Post by mikemwa on 2009-04-04
OK I understand that then. I kinda figured Windows wouldn't recognise the flash drive.
What is the difference then between when you first boot the cd, select language and go to install Ubuntu or letting the cd boot up then go to System, Administration and create a usb startup disk?

Mike

---

### Post by bluelamp999 on 2009-04-04
Take a look at this...

[http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows](http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows)

I haven't tried it but it looks kind cool...

---

### Post by mikemwa on 2009-04-04
> **bluelamp999 said:**
> Take a look at this...

[http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows](http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows)

I haven't tried it but it looks kind cool...


I saw that last night also. Looks a little harder to do though. Not sure if you can boot directly from the flash drive which is what I want to do or if it's just for doing inside windows. I'll have to check it out when I get time.

---

### Post by ronparent on 2009-04-04
I have a 32 Gb flash drive I have been able to use on several computers. Don't ask me how I got ther though. It wasn't straight forward. So good luck.

---

