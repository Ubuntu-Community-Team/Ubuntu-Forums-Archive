---
title: "Sony VAIO VGN-FZ18E headphone jack not working on Ubuntu 7.10"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by Aeren on 2007-12-11
I've tried to use my headphones on my recently acquired laptop, which is a sony vaio vgn-fz18e, but it seems the headphone jack isn't recognised with ubuntu 7.10. The internal sound doesn't mute, and no sound is emitted through my headphones. it's quite annoying for me as well as for others.
Is there any kind of workaround to make it work? (drivers or anything else).

---

### Post by ClarkePeters on 2007-12-16
same problem here. 
headphone jack works fine (and automatically) with Windows so I know the problem is with ubuntu

---

### Post by lssaravan on 2007-12-16
I happen to be a new user to Linux and after installing Gusty, my Acer Aspire 5573 also had a similar problem.  What I would suggest to you is, try double clicking on the volume control icon in your taskbar and go to Edit->Preferences.  Select everything that you feel is related to the speaker and headphones and play around with them.  In my case, the surround volume bar acts as the main speaker control and the front speaker volume bar controls the headphones.

Hope this works out for you.  Let me know if it helped.
cheers

---

### Post by Fabiotc on 2007-12-16
Try this first:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

If it doesn`t work, try this:
 [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)



And don`t forget, in the end:

sudo gedit /etc/modprobe.d/alsa-base

Add the line: 
options snd-hda-intel model=vaio position_fix=0


:)
Regards from Brasil

---

### Post by G@B0 on 2007-12-22
> **Fabiotc said:**
> Try this first:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

If it doesn`t work, try this:
 [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)



And don`t forget, in the end:

sudo gedit /etc/modprobe.d/alsa-base

Add the line: 
options snd-hda-intel model=vaio position_fix=0


:)
Regards from Brasil

That works. Now I have audio on headphones. :)

Im still working on how to reduce brightness on this laptop.

Salu2

---

### Post by amxs on 2007-12-28
Hi all, I've tried so hard to make work my headphone with community and official documentations,with your links but It doesn't work.I've a Sony Vaio vgn-FZ18M and ubuntu 7.10. Can anyone help me?thank'you

---

### Post by zakaroo on 2007-12-29
I am in the same boat as AMXS -- I have a Vaio VGN-FZ130E.  I had sound, but not on the headphone jack, I followed the instructions on these two websites and now I have NO sound at all!  I went back and did it again and saw the single line error on the ./configure on the alsa-drvier section.  I am running Ubuntu 7.10 with the xen 3.1 overlay.  Any suggestions would be helpful, otherwise I'm going to have to reload the entire systems to get my sound back.

---

### Post by idrinktoomuch on 2008-01-14
> **Fabiotc said:**
> Try this first:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

If it doesn`t work, try this:
 [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)



And don`t forget, in the end:

sudo gedit /etc/modprobe.d/alsa-base

Add the line: 
options snd-hda-intel model=vaio position_fix=0


:)
Regards from Brasil


FYI Method 1 above fixes the issue with the headphones not working on the Sony Vaio VGN-FZ21S

Thanks

---

### Post by sammydadams on 2008-01-17
try this...it reloads ALSA to an older version which seems more stable...it fixed mine on fz180e

Audio/Headphone Fix (VAIO):

IMPORTANT!!
make sure in software sources "pre-release updates" is NOT selected! (i did this once and made a mess of things)
...to simplify this, run automatix (i know some hate automatix, but it has never let me down =) ) first which will configure the software sources for you then IMMEDIATELY fix the ALSA driver as below!!!!!!!!!!!!!

reinstall ALSA driver
run:
$ sudo apt-get install module-assistant
$ sudo m-a update
$ sudo m-a prepare
$ sudo m-a a-i alsa
in terminal

add line:
options snd-hda-intel model=vaio
to
/etc/modprobe.d/alsa-base

not sure if this was needed...try above first along with modprobe.d fix and reboot/check

run:
$ sudo apt-get install linux-backports-modules-generic
in terminal


reboot

---

### Post by aimaz on 2008-01-24
Fixed!

I have a Sony Vaio AR51E. The main speakers were working but the headphones were ignored. I fixed this by doing the following things.

First I enabled gutsy-backports.

System -> Administration -> Software Sources

Enter password and change to the "updates" tab.

Check the box "Unsupported updates (gutsy-backports)" and close the window.

It should then say that it needs to update the package lists, let it do this.

Open a terminal and enter the following.

```
sudo apt-get install linux-backports-modules-generic
```

This will install a bunch of new modules, including new alsa stuff.

Then you need to an option for the sound module.

Open /etc/modprobe.d/alsa-base in your "favourite text editor" and add 

```
options snd-hda-intel model=vaio
```

In a line of its own.

After rebooting the computer this fixed my non-working headphones.

---

### Post by chris_77 on 2008-02-29
I used the method by described above by aimaz. worked perfectly on my **VGN-FZ18M**. 
Thanx a lot!

---

### Post by patrickfromspain on 2008-02-29
sudo apt-get install linux-backports-modules-generic and adding options snd-hda-intel model=vaio to alsa base worked for me in a VGN-FZ21E

---

### Post by bondo on 2008-03-11
Did anybody notice when they follow step 1 the ALSA sound is nolonger loaded. this option works great but I no longer have the ALSA driver loaded just OSS. I only noticed this because I had my mediaplayer set to use the ALSA driver.

any thoughts

-Bondo

---

### Post by frenchtomytoast on 2008-04-02
aimaz's method works on FZ280E. Thanks :)

---

### Post by sspingal on 2008-04-08
Guys try this link called **Envy**.
It worked for me. I am using Acer Aspire 4710z.

"Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) package the driver that comes with ATI or Nvidia's installer (from their respective websites)
3) install all you need to package and install the driver
4) configure the Xserver for you



[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

All the best.

---

### Post by aimaz on 2008-04-22
So, a few days ago I upgraded to Hardy Heron and the headphone jack problem came back. This probably happened because I chose to install the package maintainers version of **/etc/modprobe.d/alsa-base**.

To fix it I just had to re-add

```
options snd-hda-intel model=vaio
```

to **/etc/modprobe.d/alsa-base**

then I just restarted the computer and it was working again.

---

### Post by oooh on 2008-04-26
Solved!! Thanks to your solution, just add this line: 

options snd-hda-intel model=vaio

In the file /etc/modprobe.d/alsa-base. 

And restart.

---

### Post by srfito on 2008-06-24
Hello everybody!

I have been using Windows for many years, but today I decided to install Linux (Ubuntu 8.04) in my new laptop (Sony Vaio VGN-SZ71MN/B). Though I am very happy, I already have my first problem, which is exactly the one you explain here: external speakers/headphones don't work, while internal ones do (even if headphones are plugged). I tried the above instructions, but the computer doesn't allow me to change the alsa-base file (it says I'm not the owner). What can I do? 

Thank you very much in advance!

---

### Post by aimaz on 2008-06-25
> **srfito said:**
> Hello everybody!

I have been using Windows for many years, but today I decided to install Linux (Ubuntu 8.04) in my new laptop (Sony Vaio VGN-SZ71MN/B). Though I am very happy, I already have my first problem, which is exactly the one you explain here: external speakers/headphones don't work, while internal ones do (even if headphones are plugged). I tried the above instructions, but the computer doesn't allow me to change the alsa-base file (it says I'm not the owner). What can I do? 

Thank you very much in advance!

Hi srfito,

Congratulations on making the jump to Ubuntu. In linux and unix each file has an owner. System files belong to a user called "root" so that any old user can't just mess things up. If you want to edit files belonging to root you need to get extra privileges, don't worry this is quite easy.

If you're comfortable using the command line then you can open a terminal and enter "sudo nano /etc/modprobe.d/alsa-base" (you can swap nano for a different editor if you prefer), if you're not comfortable with the command line then press Alt+F2 this opens the run application dialog box. Enter "gksudo gedit /etc/modprobe.d/alsa-base", this will then allow you to edit the file after entering your password.

Hope that helps and that you continue to enjoy using Ubuntu, you're doing well already by finding this help and trying to follow it.

Aimaz

---

### Post by srfito on 2008-06-25
It worked! Thank you very much!

I have to admit that I don't feel very comfortable doing things that I don't understand, but at least I know that I have the possibility to know and learn (unlike in Windows, where nobody really knows what happens) 

Thanks again.



> **aimaz said:**
> Hi srfito,

Congratulations on making the jump to Ubuntu. In linux and unix each file has an owner. System files belong to a user called "root" so that any old user can't just mess things up. If you want to edit files belonging to root you need to get extra privileges, don't worry this is quite easy.

If you're comfortable using the command line then you can open a terminal and enter "sudo nano /etc/modprobe.d/alsa-base" (you can swap nano for a different editor if you prefer), if you're not comfortable with the command line then press Alt+F2 this opens the run application dialog box. Enter "gksudo gedit /etc/modprobe.d/alsa-base", this will then allow you to edit the file after entering your password.

Hope that helps and that you continue to enjoy using Ubuntu, you're doing well already by finding this help and trying to follow it.

Aimaz

---

### Post by bwnguyen on 2008-06-28
Hey! It works perfectly for me now! :)
After a bunch of problems trying to compile the stuffs, it turns out to be fixed with a simple way :D
Thanks a lot man!
(Mine is VGN-FZ240E)

---

