---
title: "Imma A Linux Noob"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by zelox991 on 2008-01-30
Alrite....overcame with all the difficulties, i finally installed linux x86 arctechture onto my E6550.....
while i've done that...i need now to install NVIDIA driver
i have
8800 gt
e6550
500 gb HDD SATA
cd/dvd drive IDE
7.1 high definition sound from Realtek

i put the driver in my new folder on the desktop called NVIDIA...
went to the terminal...which was sort of like ms dos on widows
typed in this command
sh NVIDIA-Linux-x86-169.09-pkg1.run

and then it runs...said it was decompressing
then it popped up saying the NVIDIA driver needs to be in root or something

Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 169.09............................................................................................................................................................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.

alrite...thx for helping me...greatly appreciated xD

---

### Post by gsiliceo on 2008-01-30
make the command 
sudo sh NVIDIA-Linux-x86-169.09-pkg1.run
And type your password.

---

### Post by zelox991 on 2008-01-30
I am sorry but i dont get it.
It didn't prompt me to put in a password

how should i type in the password
maybe with a special command?
 thx

---

### Post by zelox991 on 2008-01-30
ok...i got that part
now it says im running an X server....
wat should i do to proceed?>

---

### Post by zelox991 on 2008-02-01
alrite...so i used envy to install my driver.
but i have one question though.
my screen is not recognized as it should be.
and the refresh rate is 50.
how should i change it.

and is Beryl originally on ubuntu?
if not. how do i find the respritories or where do i find the package. 
thx so much for helping me

---

### Post by faulkes on 2008-02-01
> **zelox991 said:**
> alrite...so i used envy to install my driver.
but i have one question though.
my screen is not recognized as it should be.
and the refresh rate is 50.
how should i change it.

Although generally the worst that will happen is it won't work, [U]changing the settings
can be hazardous (or at least has been in the past and without more information
I can't say).[/U]

[B]I would suggest you find the specifications for your monitor/screen before doing 
anything.[/B]

> 
and is Beryl originally on ubuntu?
if not. how do i find the respritories or where do i find the package. 
thx so much for helping me

Beryl has been merged in compiz which is supplied by default but to my knowledge not
enabled by default.  They can be enabled by going to 

System->Preferences->Appearance->Visual Effects and selecting the appropriate
level.  Additional modifications can also be made via System->Preferences->Advanced Desktop Effects Settings.

Faulkes

---

