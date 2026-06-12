---
title: "ATI Radeon HD4650: no video"
date: 2010-12-15
forum: Hardware
---

### Post by Splat_NJ on 2010-12-15
I just got an agp-version ATI Radeon HD 4650 to give my pc new life. I did a fresh install of Maverick and get nothing on the screen upon bootup. The monitor stays alive but no video. Rebooted a few times and still nothing. Now I'm trying my Ubuntu image I made a few days ago. I'm hoping it'll work and I can install the 4650 drivers and be good to go. I've researched but 99% of the threads on this card are pre-Maverick. BTW, card works fine with XP. Anyone have/had similar issues with this card?

---

### Post by Splat_NJ on 2010-12-15
Imaged Ubuntu gets me no video either. I'm going to do another fresh install, then run the livecd and see what's what.

---

### Post by Splat_NJ on 2010-12-15
One thing weird is when doing a fresh install from the cd I get all types of command line text in the beginning before the desktop ever appears. This happened both times doing the fresh install. The mouse is lagging, too.  So I get video during the install but booting to the fresh install on the harddrive gets me nothing.

---

### Post by Splat_NJ on 2010-12-15
Great.... just great. No video after hitting "Try Ubuntu" on the install cd. I'm up the river here guys. Please don't send me back to XP!  :(

---

### Post by Splat_NJ on 2010-12-15
OK, swapped the 4650 with my old Radeon, rebooted. Installed fresh Ubuntu. Installed the ATI Radeon drivers for the 4650 obtained from AMD's site. Swapped the cards again. Did "sudo aticonfig --initial" which created the xorg.conf file in the /etc/X11 directory. Restarted gdm so I could use sudo gedit to modify xorg.conf file with additions from [here]("http://ubuntuforums.org/showpost.php?p=9061946&postcount=1") .  Got the graphics working fine now. Have to check out vids and streaming to see how it really works. Also, I noticed doing an lspci -v that the audio device on this card is enable.  I already have a SB card for sound so how would I disable the 4650's sound chip? Thanks.

---

### Post by Splat_NJ on 2010-12-15
Well, so far, so good!  Youtube's smooth and DVD's are playing smooth too. My hat's off to ATI/AMD for both releasing this card for those of us with older AGP systems and for also the ATI drivers for this card.  Now how do I mark this thread as solved?

---

### Post by Yellow Pasque on 2010-12-15
> **Splat_NJ said:**
> I already have a SB card for sound so how would I disable the 4650's sound chip?

You can blacklist the snd-hda-intel driver.

---

### Post by Crusty Old Fart on 2010-12-15
Nice work, Splat.

Follow the green link in my signature to mark your thread as [SOLVED].

---

### Post by Splat_NJ on 2010-12-16
Thanks guys. I was able to disable the ATI's soundchip via the "Sound" section off the Main Menu. All is well. 

Merry Christmas and Happy Holidays!

---

### Post by Splat_NJ on 2010-12-16
I apparently spoke too soon. After updating I now get a black screen with a purplish-pink border all around the outer perimeter of the screen. I guess the update messed with the driver(s). Is there a way around this or something I need to look out for upon every update?

---

### Post by Splat_NJ on 2010-12-16
Got it working again. Had to boot into recovery mode, chose lowered graphics and then reinstalled the ATI drivers. What a PITA but it works now. Cheers!

---

### Post by ~~Tito~~ on 2010-12-22
Is there anyway to accomplish making the GPU work with out a spare GPU?

---

### Post by Splat_NJ on 2010-12-22
> **~~Tito~~ said:**
> Is there anyway to accomplish making the GPU work with out a spare GPU?

If that's the only card you have, then I don't know what to tell you. I guess you'd have to install the drivers from a command line if you get one. That might get you to a working desktop, then edit xorg.conf as needed, or edit it from terminal.

---

### Post by ~~Tito~~ on 2010-12-22
> **Splat_NJ said:**
> If that's the only card you have, then I don't know what to tell you. I guess you'd have to install the drivers from a command line if you get one. That might get you to a working desktop, then edit xorg.conf as needed, or edit it from terminal.

*Sigh* What command line to use? I am doing this mainly to put Ubuntu on my CR-48. Right now I am SOL to download anything.

---

### Post by Splat_NJ on 2011-01-01
I figured out how to install the ATI drivers from the shell. This will help out doing a fresh install or when swapping out for a new card that then gives you no video/desktop/gui. After installing Ubuntu and rebooting I would get nothing more than a blinking cursor at top left of screen. Obviously I couldn't install the ATI driver package then. Well, here's how to install the ATI driver package when you can't get the GUI working:

Install Ubuntu if desire, then reboot.

After reboot hit ***<Shift>*** right after your Bios loads to temporarily edit the Grub.cfg file.
Highlight the first option and hit ***<e>*** to edit the option. 
Edit the line that loads the Linux kernel, adding the word "***text***" at the end of the line, with a space after "splash"  then hit ***<control><x>*** to reboot. This will allow you to boot right into the shell.

Log into the shell.

You have to have the ATI driver install package somewhere you can get to it when inside the shell. I copied the driver package onto my flashdrive and mounted it with these commands (these work on my PC, yours may be different):

[B][I]sudo mkdir /media/flashdrv
sudo mount -t vfat /dev/sdc1 /media/flashdrv[/I][/B]

Then I copied the ATI package to my topmost shell directory(don't forget to use the <TAB> key to fill in the ATI file name instead of having to type it in)
[B][I]cp /media/flashdrv/ati-driver-installer.... ~
[/I][/B]
Change directory ("cd") to wherever you have ATI package, then type: 
[B][I]chmod +x ati-driver-installer....... .run
sudo ./ati-driver-installer....... .run
[/I][/B]
When installation is complete type:
***sudo aticonfig --initial***

Once that's done, reboot.

Upon bootup you should get the desktop/gui. If you do, you're good to go! :)   If you still get no gui then you may need to edit your Xorg.conf file. More info can be found here: [http://ubuntuforums.org/showpost.php?p=9061946&postcount=1](http://ubuntuforums.org/showpost.php?p=9061946&postcount=1)


FWIW, I was getting "irq 16: nobody cared" message upon bootups so I entered "noirqdebug" before "quiet splash" in my Grub.cfg file and no more messages and everything appears to be working fine.

---

### Post by Splat_NJ on 2011-01-02
Something interesting... I backed up my system with Remastersys and this was the first time I restored using that image. For some weird reason I needed to reinstall the ATI drivers. The Catalyst Control Center and the CCC (admin) entries were still listed under System/Preferences but could not execute. The given reason was the drivers were missing. So I rebooted, using the "text" option as I noted above, and reinstalled the ATI driver package. Good to go again. I can't fathom why the drivers would be uninstalled upon either making the backup with Remastersys or upon restoring. Interesting.......

---

### Post by Splat_NJ on 2011-01-09
A few folks wrote me asking if I tried "nomodeset" in my Grub. Yep, I tried that, but it didn't work. FWIW, what I wrote above is the only thing that has worked for me.

---

