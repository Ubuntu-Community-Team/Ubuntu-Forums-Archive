---
title: "HELP - Screen problem on Ubuntu - Toshiba Qosmio x500"
date: 2011-04-13
forum: Hardware
---

### Post by pkmluudung on 2011-04-13
I am using a Toshiba Qosmio x500 and trying to install ubuntu on it but there is a problem with the screen. (image below). With ubuntu 10.10, it appear right after I click Install now, with ubuntu 11.04 beta, it is ok to install but the same problem after I turn it on. 
I thought that it is a VGA card problem ( my laptop is usung nVidia geforce 250m 1 Gb) because the ubuntu 11.4 istallation does not use ubuntu 's GUI so I can insatll it but cannot run it. But I have checked the card 's driver and it is ok. :sad:
Does anyone help the same problem or can help me with this ?
Thank u so much :popcorn:
[URL="http://anhso.net/pkmluudung/photo/3821671/a-1/"][IMG]http://farm2.anhso.net/pic/o/3572/842011182734495/a-1.jpg

---

### Post by pkmluudung on 2011-04-17
Can anyone help me?
I really want to install ubuntu as soon as possible :(

---

### Post by guilleaf on 2011-04-25
Yes, I had the same screen. Here the steps to install Ubuntu 11.04 (Beta 2, today) 

1. Install Ubuntu using the Alternate CD, not the normal one. It will install in text mode

2. After installation, enter into your system using the failsafe mode (second in the grub list)

3. It will show you a text menu, with options to start, select "root mode with network"

4. Update your system to the latest packages

sudo apt-get update
sudo apt-get upgrade

5. Restart again in failsafe mode, select the X in failsafe graphics mode, it will select
the Classic mode instead of Unity

6. Enter into the menu Administration -> Additional drivers, it will show you the option
to install the Nvidia drivers. Select install those drivers.

7. Restart ubuntu in normal mode, it will enter without problems

---

### Post by flexi_47 on 2011-05-07
Hi, same problem occured at my toshiba qosmio x505 model after installling ubuntu 11.04.It still display same result.Did you solve your problem by doing @ guilleaf's solution.Please help me about this silly bug please.Anyone & anyidea ?

---

### Post by BicyclerBoy on 2011-05-07
Cool a built in Pacman arcade game..

Use Grub failsafe mode
or...
Boot to GUI screen (corrupt) & then ...

You can <ctrl>+<alt>+<F1>

and login to your PC in console (text mode)..

Then follow the upgrade procedure list above (previous posts)..


AFAIK Your install Cd/DVD gives you options to access your machine or boot your existing install in failsafe mode..

---

### Post by xium on 2011-09-24
i faced the very same problem and solved it with success by following these steps :
[http://www.youtube.com/watch?v=0iyw4-KcPMg&feature=related]("http://www.youtube.com/watch?v=0iyw4-KcPMg&feature=related")
+ i marked "mark all upgrades" 
finally restart yr system 

):P

---

