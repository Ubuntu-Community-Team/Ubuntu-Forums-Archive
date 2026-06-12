---
title: "[SOLVED] problem installing ubuntu 8.04"
date: 2008-10-03
forum: General Help
---

### Post by Nailhac on 2008-10-03
I am experiencing problem attempting to install ubuntu 8.o4 on acer notebook. All the criteria is met hdd ram etc. The instal appears to go well with the various choices etc live, full, language etc. the instal hangs during installation. I have successfully instlled ubuntu 8.04 on my desktop pc and was so impressed that I wish to do a full install on notebook. I would appreciate any advice.

---

### Post by Partyboi2 on 2008-10-04
What part of the installation is it hanging at? Are you installing using the desktop live cd or the alternate cd?

---

### Post by Nailhac on 2008-10-04
Hi Partyboi2- The last line prior to halting on live cd is
"running local boot scripts (/etc/rc.local) [OK]"
that is the last line and I have attempted this 3 times.
I have also attempted a full instal and receive a similar message.

My instal on desktop was OK with CD so that is not defective. Any advise would be appreciated.

---

### Post by Partyboi2 on 2008-10-04
Have you tried press F4 at the main menu and starting it in safe graphics mode?
what video card does your acer use?

---

### Post by Nailhac on 2008-10-04
Yes have tried safe graphic mode. The video card is via unichrome agp8x.Thanks for your interest in my problem.

---

### Post by Partyboi2 on 2008-10-04
Have you tried installing using the alternate cd? You can download it from [[COLOR=Blue]here[/COLOR]]("http://releases.ubuntu.com/8.04.1/")

---

### Post by Nailhac on 2008-10-06
Have downloaded alternative cd and attempted to install on ACER. I get a stage further with some undecipheral graphics and instructions and therefore cannot continue with the installation. It would appear but am unsure that there is some type of graphics problem. How can I rectify the problem? The system still works OK in Windows

---

### Post by Partyboi2 on 2008-10-06
> **Nailhac said:**
> Have downloaded alternative cd and attempted to install on ACER. I get a stage further with some undecipheral graphics and instructions and therefore cannot continue with the installation. It would appear but am unsure that there is some type of graphics problem. How can I rectify the problem? The system still works OK in Windows
what model of acer do you have?

---

### Post by Nailhac on 2008-10-07
Acer Aspire 1353 LC

---

### Post by Partyboi2 on 2008-10-07
Ok, I found this on a french site
> At the launch of the CD, add vga=773 otherwise the display will be unreadable.
At the end of the installation, when the installation offers to restart, open a console (Ctrl + Alt + F2) and edit the xorg.conf
```
 nano /target/etc/X11/xorg.conf  
```Add to monitor section
```
 HorizSync       31.0 - 48.0
``` After saving (Ctrl + O) and exit (Ctrl + X) nano, you can return to the Desktop  (Ctrl + Alt + F7) and  restart.  [LEFT]
Actually page is found [[COLOR=Blue]here[/COLOR]]("http://translate.google.com.au/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/acer_aspire_1353lc&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3DAcer%2BAspire%2B1353LC%2Bhardy%2Bubuntu%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-GB:official%26hs%3Da3l%26sa%3DG")
[/LEFT]

---

### Post by Nailhac on 2008-10-09
many thanks partyboi2 i managed to get a stage further. have now reached the final stage of inserting codes but cannot get the computer to save and restart in desktop mode.

---

### Post by Partyboi2 on 2008-10-09
I had to edit that post from the french site as the terminal commands where wrong.
So what you need to do is
1st 
add vga=773 as a boot option. When you boot the ubuntu cd and are at the main menu screen press F6 and add ```
vga=773
``` then press enter. Then choose to use ubuntu without installing, if I remember rightly that is the first option. Then when you have booted to the desktop click on the install icon.
2nd
 Then after you have installed and the installer asks if you want to reboot or continue using the live cd, choose the live cd. Then Press Ctrl+Alt+F2, this will bring you to a terminal. Then type:
```
nano /target/etc/X11/xorg.conf
``` this will open a file. Look for the monitor section eg
```
Section "Monitor"
                     Identifier      "Configured Monitor"
``` under identifier add
```
HorizSync       31.0 - 48.0
``` eg.
```
Section "Monitor"
                      Identifier      "Configured Monitor"
                      HorizSync       31.0 - 48.0
```then to save the changes Press Ctl+o then press "enter" to accept the changes then finally to exit the text editor Ctrl+x Then Press Ctrl+Alt+F7 to get back to the desktop, then reboot.

---

### Post by Nailhac on 2008-10-10
Thanks again Partyboi2. Unfortunately I can only get as as far as the following (After about 3 or 4 minutes booting time)

*checking battery status.....[OK]
*running local boot scripts (/etc/rc.local) [OK]
_



It will not continue through to desktop mode.

I will keep trying alternatives but would certainly welcome any more advise you may come up with. It would appear that Acer computers to seem to have a bad time with Linux from what I read. Maybe Acer should get their finger out and make life a little easier for Linux enthusiasts.

---

### Post by Partyboi2 on 2008-10-10
Try booting into recovery mode now that you have installed ubuntu. When you boot the machine and see  grub loading....  press Esc this will take you to the grub menu where you can choose recovery mode. Try selecting xfix after you have have selected recovery mode and see if that will allow you to get to a working desktop. If that does not work then you could look at using the openchrome driver. See the graphics card section from [[COLOR=Blue]here[/COLOR]]("http://translate.google.com.au/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/acer_aspire_1353lc&sa=X&oi=translate&resnum=9&ct=result&prev=/search%3Fq%3Dinstalling%2Bubuntu%2BAcer%2BAspire%2B1353LC%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3DUt5%26sa%3DX")
I didn't release you where in France so [[COLOR=Blue]here[/COLOR]]("http://doc.ubuntu-fr.org/acer_aspire_1353lc") is the french version as well, probably easier reading for you.
To follow that guide to install the chrome driver you will need to input those commands from a terminal which can be done by either booting into recovery mode or when you boot normally and see "running local boot scripts (/etc/rc.local) [OK]" you can press Ctrl+Alt+F2 You will also need a working internet connection to your acer to install the chrome driver.

---

### Post by Nailhac on 2008-10-11
Partyboi2 Many thanks eventually got it on track thanks to you. Just before I was about to throw the Acer in the bin. Works well. I owe you a beer.

---

### Post by Partyboi2 on 2008-10-11
happy to help :)

---

