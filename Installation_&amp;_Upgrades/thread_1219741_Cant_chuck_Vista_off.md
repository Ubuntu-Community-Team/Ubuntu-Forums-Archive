---
title: "Cant chuck Vista off"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by pbremner on 2009-07-22
Hi. Very frustrated semi tech newbie here. Just bought a new Compaq presario CQ61. I cannot get rid of vista to install Ubuntu 9.0. I have tried setting the dvd drive as the default/primary boot device without success. This vista really has self preservation at heart, all its done is make me hate Microsoft even more. I have read stuff about the MBR and BCD etc. I have also been told to create a DOS boot disk on a flash drive, boot off it and format the drive. I am now confused, frustrated and not sure which option(s) i should try. Any help is appreciated.
regards,
Patrick

---

### Post by grubnoob on 2009-07-22
For computer specific problems, you need to search the internet for people with same problem as you. Use google and type your computer model and your problem, as a real question. Usually you get a hit or two were people have same problems as you and if you are lucky, it has been solved by someone else.

Good luck

---

### Post by prshah on 2009-07-22
> **pbremner said:**
> I have tried setting the dvd drive as the default/primary boot device without success.

If this has not worked, then you need to check either the drive (unlikely to be a problem) or the Ubuntu disc you are using in it (very likely to be the problem).

At this point in the game, Vista has not yet loaded and cannot be interfering in any way.

Get another CD / DVD, burn an Ubuntu image onto it at a slower speed, and try again.

I have also noted that some (brand-new) LG DVD-RAM drives are flawless at handling DVDs but less forgiving with _some_ CDs. Not that you need to change your drive; just use a higher quality blank CD.

---

### Post by dk06 on 2009-07-22
> **pbremner said:**
> Hi. Very frustrated semi tech newbie here. Just bought a new Compaq presario CQ61. I cannot get rid of vista to install Ubuntu 9.0. I have tried setting the dvd drive as the default/primary boot device without success. This vista really has self preservation at heart, all its done is make me hate Microsoft even more. I have read stuff about the MBR and BCD etc. I have also been told to create a DOS boot disk on a flash drive, boot off it and format the drive. I am now confused, frustrated and not sure which option(s) i should try. Any help is appreciated.
regards,
Patrick

Put your Ubuntu CD in & Reboot
Then:
Press [esc] at boot (gives you a menu)
Then Press [F9] for 1 time boot menu
Then....Select your CD/DVD Drive & Press [enter]


edit: 
& like it states in the previous post, if you're still having issues, re-burn -or- re-download & re-burn
check out ISORecorder for burning & DownThemAll for downloading

---

### Post by Tclarkie on 2009-07-22
just wipe the hdd, delete, delete, delete
:D

---

### Post by sanderj on 2009-07-22
> **pbremner said:**
> Hi. Very frustrated semi tech newbie here. Just bought a new Compaq presario CQ61. I cannot get rid of vista to install Ubuntu 9.0. I have tried setting the dvd drive as the default/primary boot device without success. 

What exactly have you tried, and how, with what result?

FYI: You have to change the boot order so that your CD/DVD-drive is booted before your harrdisk. You have to press a key at the moment your BIOS is booting. It depends on the BIOS which key you have to press: ENTER, F10, F2, F12, ESC. Look at the screen; normally it will tell which key to press. Otherwise, consult your manual for info.

---

### Post by pbremner on 2009-07-22
Hi All. I have tried setting the DVD to boot first and HDD last without success. Keeps reverting to HDD and boots Vista. The Ubuntu CD is good as I have installed Ubuntu on an older notebook with no problems (ASUS). I even tried to disable the HDD in the BIOS as a boot option - not able to do; U can move it down the boot order but not disable it.

The Vista on the machine I am trying to chuck off is running and registered.

If I take out the HDD and install on another machine as a slave or the like and then format it, reinstall in notebook and then try to install Ubuntu - do you think this will work?

Regards,
Patrick

---

### Post by sanderj on 2009-07-22
> **pbremner said:**
> 

If I take out the HDD and install on another machine as a slave or the like and then format it, reinstall in notebook and then try to install Ubuntu - do you think this will work?


Yes, that will work (as long as you don't install special video card drivers). 

But fixing the boot sequence should be easier.

---

### Post by Mark Phelps on 2009-07-22
> **pbremner said:**
> If I take out the HDD and install on another machine as a slave or the like and then format it, reinstall in notebook and then try to install Ubuntu - do you think this will work? 

Yeah -- because you've basically cleaned out the drive.

But ... before you do that, do you know for certain that Ubuntu will work properly on this machine?  If you wipe the drive and the Ubuntu install fails or some things don't work, you'll be left with an electric brick!

Strongly suggest you try the following first:
1) Remove (or disconnect) the hard drive from this machine
2) Insert the Ubuntu CD and boot into LiveCD mode
3) Run Ubuntu and confirm that it detects all your hardware (including wireless), that you can get decent screen resolution, and other stuff works as well.  It will be slow, but everything should work.
4) If you run into problems with things not working, search these forums for similar information to see if fixes are available.  Make note of the ones you find and apply them.

Only if you get all the stuff working reasonably well should you then wipe the drive and install.

---

### Post by sanderj on 2009-07-22
> **pbremner said:**
> Hi All. I have tried setting the DVD to boot first and HDD last without success. Keeps reverting to HDD and boots Vista. 

Question: are you able to get in the BIOS' boot order menu, and are you able to switch the boot order?

If so, and you can get the CD/DVD as the first boot option, and still your system does not boot from the Ubuntu CD, you have to find why that happens. Do you hear the Ubuntu CD spinning?

Another workaround: use another computer to live-boot Ubuntu and then create a live USB-stick, and try to boot from that live USB-stick in your 'unwilling' machine.

---

### Post by running_rabbit07 on 2009-07-22
You should be able to put the LiveCD in while in Vista and click install. From there the LiveCD will restart the PC itself and start the install.

Another thing to try is put the CD in then restart and when P.O.S.T. is complete you should be able to hit F12 and choose what hardware to boot from which is a one time thing. After that you should be able to install.

---

