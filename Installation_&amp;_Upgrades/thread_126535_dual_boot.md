---
title: "dual boot"
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by gary.b on 2006-02-06
hello
I am new to ubuntu and just finished my installation which went very well thanks to the instructions posted at [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm).
Many thanks for these instructions.

My dual boot automatically is set to ubuntu and it will cause confusion for other  users on my computer. I wish to have the default bboot to Windows Xp. 

I have followed the instructions on the following grub page 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
but I am still having problems.

Any help appreciated.

---

### Post by Robgould on 2006-02-06
open boot/grub/menu.lst with gedit as super user
 
sudo /boot/grub/menu.lst
 
Tead the file very carefully.  Near the top there is a selection for default.  It is set to 0.  Cahnge it to your windows (probably 4).  To know for sure count each entry at the bottom of the file starting at 0.  
 
After changing the setting, save the file.  Reboot to test.  Hope this helps.

---

### Post by gary.b on 2006-02-06
[QUOTE=gary.b]hello
I am new to ubuntu and just finished my installation which went very well thanks to the instructions posted at [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm).
Many thanks for these instructions.

My dual boot automatically is set to ubuntu and it will cause confusion for other  users on my computer. I wish to have the default bboot to Windows Xp. 

I have followed the instructions on the following grub page 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
but I am still having problems.

Any help appreciated.[/QUOTE]
Thanks Rob
I will give it a shot

---

### Post by gary.b on 2006-02-06
Thanks Rob
I will give it a shot

---

### Post by gary.b on 2006-02-06
Rob, when I try this I keep getting a command not found message.


[QUOTE=Robgould]open boot/grub/menu.lst with gedit as super user
 
sudo /boot/grub/menu.lst
 
Tead the file very carefully.  Near the top there is a selection for default.  It is set to 0.  Cahnge it to your windows (probably 4).  To know for sure count each entry at the bottom of the file starting at 0.  
 
After changing the setting, save the file.  Reboot to test.  Hope this helps.[/QUOTE]

---

### Post by Installer36 on 2006-02-06
The command should read   sudo gedit /boot/grub/menu.lst
  Hope this helps...Installer36

---

### Post by gary.b on 2006-02-06
got there! 
thanks

[QUOTE=Installer36]The command should read   sudo gedit /boot/grub/menu.lst
  Hope this helps...Installer36[/QUOTE]

---

### Post by gary.b on 2006-02-06
when i try to make a backup of my menu.lst using "sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup" i get the following error message :

cp: missing destination file

help !

---

### Post by Herman on 2006-02-07
Hello, gary.b, you should be able to copy the commands right off the website and paste them into your terminal if that helps you.
 It saves making all kinds of mistakes like typos. I test these commands myself too, so they should all work, but if any don't, I do monitor the forums in case there are any problems.
I don't see anything wrong with your above command:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``` One thing I tried when I installed for the first time was to type 'menu.1st', (with a number one) thinking it was short for 'menu first'. It's 'menu.lst', short for 'menu list' (with an L). That's one trap for new players. It looks like your is okay though. I can't think what else could be wrong. 
Menu.lst has to be there, or you wouldn't be able to boot in the first place. It would be very odd if menu.lst was in any other directory than /boot/grub.
I will watch and see if you need more help, good luck with it, and keep on trying, it gets easier as you get used to it. :-D (Herman)

PS, Another tip: when you do need to type a command yourself, try just typing the first one or two letters of the filename, and then press your tab key. Most times the rest of the filename will auto-complete itself.
pss: Use your up and down arrow keys to scroll back to commands you have used before that you remember worked well, rather than re-typing them all the time.

---

### Post by Robgould on 2006-02-07
Looks like I forgot the "gedit" in my original post.....sorry for any confusion.

---

### Post by gary.b on 2006-02-07
thanks for your help!

---

### Post by gary.b on 2006-02-07
I just completed my first sucessful dual boot.
thanks for all the help !

---

