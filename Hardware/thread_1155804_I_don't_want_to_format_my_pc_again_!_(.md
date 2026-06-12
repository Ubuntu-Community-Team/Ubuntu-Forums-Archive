---
title: "I don't want to format my pc again ! :("
date: 2009-05-11
forum: Hardware
---

### Post by napstar on 2009-05-11
Hi Everyone , 
I'm very new at ubuntu and have the following graphic card : 

ATI Radeon 9550 / X1050 Series  (256mb)

Everytime i install Ati Catalyst Center , or ATI Binary X.org stuff 
I can't log in again 
I see a Screen Like trash , and color , this really annoying 
Also i couldn't run compiz .

---

### Post by Ms Spock on 2009-05-11
Do you mean you don't have the right drivers for your graphics card?

Do you mean you get the black screen after you get the spalsh screen?

I am very new to Ubuntu as well. I am not quite sure what you are saying.

Cheers,

Spock

---

### Post by napstar on 2009-05-11
After the installation of ati catalyst or ati binary x.org 
I reboot and get the black screen with colorful trashes.
and can't login anymore ..

---

### Post by Peter09 on 2009-05-11
There is no need to re-install.

Initially try going to recovery mode (hit escape at the Grub prompt and use the arrows to go down one line to select recovery).

When you get to a menu select the fix the xserver option.

---

### Post by barisurum on 2009-05-11
napstar: Your graphics card is not supported with the latest ATI driver (9.4) and older drivers are not compatible with the new x.org server (1.6). So you have to use the open source ati driver which fully supports your card. 
To remove the installed proprietary driver (*.run) downloaded from ati's site choose recovery mode, when it comes to the menu do the 'drop to command shell' option and:


   1. Navigate to the /usr/share/fglrx folder "cd /usr/share/fglrx".
   2. With super user permissions, enter the command "sh./fglrx-uninstall.sh" 

You have now successfully uninstalled the ATI Linux Proprietary Driver.

Now select the xfix command in recovery mode.

---

### Post by napstar on 2009-05-11
i chose the "xfix" option and still couldn't login ..

---

### Post by Peter09 on 2009-05-11
Ok, do the same again but when it comes to the menu do the 'drop to command shell' option.

Once there do the commands that [barisurum]("http://ubuntuforums.org/member.php?u=67553") mentioned. (you will not need the sudo bit as you are in an administrative shell.

---

