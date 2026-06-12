---
title: "can't login"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by mba56 on 2009-10-06
Hello
i am new to linux and few days back install Ubuntu,i just did a blunder, i change username and login name andreboot the machine,now i cant login either using new username or old username.when i enter old one it shows error message and stops.any help would greatly be appreciated.

---

### Post by mikewhatever on 2009-10-06
Try booting into recovery mode (usually the second line in boot menu). If it works, use the following command to add another admin user:

adduser [username] admin

You'll be asked for a new password, and [username] is the word you want to use, such as mba56.

---

### Post by lindsay7 on 2009-10-06
How to reset your password in Ubuntu
There are many reasons you might want to reset a password: 
Someone gave you a computer with Ubuntu installed on it but not the password for the user account.
You just installed Ubuntu and forgot what password you selected during the installation process. 
You have too many passwords in your life and can't keep track of them all.
Well, this tutorial will help you reset your Ubuntu user account password, regardless of what reason you have for resetting it. 
First, you have to reboot into recovery mode. 
 
If you have a single-boot (Ubuntu is the only operating system on your computer), you may have to press the Escape key during bootup in order to see the boot menu. If you have a dual-boot (Ubuntu is installed next to Windows, another Linux operating system, or Mac OS X; and you choose at boot time which operating system to boot into), the boot menu should appear without the need to press the Escape key. 
 
From the boot menu, select recovery mode, which is usually the second boot option. 
 
After you select recovery mode and wait for all the boot-up processes to finish, you'll be presented with a few options. In this case, you want the Drop to root shell prompt option so press the Down arrow to get to that option, and then press Enter to select it.
The root account is the ultimate administrator and can do anything to the Ubuntu installation (including erase it), so please be careful with what commands you enter in the root terminal. 
Once you're at the root shell prompt, if you have forgotten your username as well, type 
ls /home
That's a lowercase L, by the way, not a capital i, in ls. You should then see a list of the users on your Ubuntu installation. In this case, I'm going to reset Linda Williams's password. 
To reset the password, type 
passwd username
where username is the username you want to reset. In this case, I want to reset Linda's password, so I type 
passwd linda
You'll then be prompted for a new password. When you type the password you will get no visual response acknowledging your typing. Your password is still being accepted. Just type the password and hit Enter when you're done. You'll be prompted to retype the password. Do so and hit Enter again. 
Now the password should be reset. Type 
exit
to return to the recovery menu. 
 
After you get back to the recovery menu, select resume normal boot, and use Ubuntu as you normally would—only this time, you actually know the password! 
Note:
In pre-8.04 versions of Ubuntu, there is no recovery menu. Once you select recovery mode, it goes straight to a root shell. After you've reset your password, you can type 
reboot
to get back to the regular boot menu and boot normally instead of selecting recovery mode. 
Another Note:
Some people get freaked out about having recovery mode logging you in as root. For more information, read Recovery mode makes me root user. Isn't that a security risk?

---

### Post by jpaugh64 on 2009-10-06
I recommend that you do not keep a user account that uses its name as its password, especially an admin*istrative* account. However, you can use that as a temporary account, as long as you remove it after you create another, permanent admin account. (I assume, though, that you will want to go keep and use that account, for simplicity's sake, while you get a feel for linux.)

---

### Post by hantechbl on 2009-10-06
Try using the Live Cd Konboot i've never tried it but I heard that it does something with the kernel to bypass the login and after restart the kernel is left as it was before using the cd.

---

