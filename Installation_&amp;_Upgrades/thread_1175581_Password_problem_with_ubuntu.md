---
title: "Password problem with ubuntu"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by topher85 on 2009-06-01
I have never used ubuntu before today.
I have  a new dell mini 9 with ubuntu and I went through the start up procedure and created a user name and password.  Then I logged in using that user name and password and everything went fine.  Next I tried to setup my wireless and it prompted me for my password.  I put it in and it said that it was incorrect and every admin task I tried to do said I had the wrong password when I am sure that it is correct.  So now I am stuck at the login screen for ubuntu and can't login.

Does ubuntu have a default password or something?  Anybody have any ideas on what happened to my password?

---

### Post by lake54 on 2009-06-01
I presume you've checked CAPS LOCK isn't on? Also have you tried just pressing enter, to see if there is no password set?

James

---

### Post by topher85 on 2009-06-01
Yeah I tried with and without caps lock and no password

---

### Post by sisco311 on 2009-06-01
Did you change the keyboard layout?

You can try to reset your password:
[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by coffeecat on 2009-06-01
> **sisco311 said:**
> You can try to reset your password:
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

Unfortunately, that may not work with a Dell. I was involved in another thread a couple of weeks ago where the owner of a Dell with Ubuntu-installed-by-Dell couldn't get into the grub menu in order to boot up in recovery mode (to reset the password as well). The OP posted a video of the bootup process. There was not a hint of the 'Grub loading, please wait.. Press ESC..' message.

Goodness knows what Dell had done. The thread never was resolved.

---

### Post by topher85 on 2009-06-01
I left the keyboard layout on USA and it types just fine.

As for the link when I go to the boot menu my options are:

Hard Drive
CD/DVD/CD-RW
Removable Devices
NetworkBoot
Diagnostics

None of which are recovery mode.

---

### Post by raymondh on 2009-06-01
> **topher85 said:**
> I left the keyboard layout on USA and it types just fine.

As for the link when I go to the boot menu my options are:

Hard Drive
CD/DVD/CD-RW
Removable Devices
NetworkBoot
Diagnostics

None of which are recovery mode.

Hello,

I hope this link can help you.  Note that this gives you the option to make a new username and password.

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

Good luck and regards,

---

### Post by lake54 on 2009-06-01
Wait a few more seconds - that's your computer's main boot menu, not GRUBs.

James

---

### Post by topher85 on 2009-06-01
When I boot up I do not every get the grub prompt.

I get a Dell Inspiron boot up screen
a screen that says MBR
and a ubuntu boot up screen

---

### Post by lake54 on 2009-06-01
The MBR one is where you press the ESC button.

James

---

### Post by sisco311 on 2009-06-01
[uhelp]community/DellMini9#Booting into Recovery mode[/uhelp]

---

### Post by topher85 on 2009-06-01
When I press escape during the MBR prompt.  I get a prompt of 2FA: and then I can't type anything else in.

---

### Post by topher85 on 2009-06-01
Got it working!  Thanks for all the help guys!

---

