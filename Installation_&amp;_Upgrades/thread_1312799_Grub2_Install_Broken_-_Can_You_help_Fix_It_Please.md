---
title: "Grub2 Install Broken - Can You help Fix It Please?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by wacky.banana on 2009-11-03
Oh what a pain. Just built my system up from scratch using 9.10. All was well until I decided to add a splash image to the grub boot screen.

I followed the instructions in HowTo Forge for doing this to the letter, having first made a backup of the relevant files. I ran grub-update, rebooted, and found that neither Uuntu nor Windows XP would boot.

I then used the instructions detailed here {http://ubuntuforums.org/showthread.php?t=1195275} to restore grub from a live 910 cd. The error message I get here, again having followed the instructions outlined, is:  "unable to resolve host ubuntu. grub-probe: error: cannot find a device for /boot/grub".

I have double checked and confirmed the correct partition which has the linux install using both commands "sudo fdisk -l" and "df -Th", to be sure as to where grub should be on the install.

Can anyone help me interprete what is wrong here and how I can rectify it please? I know I can easily reinstall 910 from scratch again but that is self defeating as I don't get the opportunity to solve the problem and learn from it plus it took me hours to fine-tune the system in the first place.

Thanks in advance for any help offered.

WB

---

### Post by sliketymo on 2009-11-03
You might try booting the live CD,and un-doing what you did before you started having problems,then" sudo update grub"

---

### Post by wacky.banana on 2009-11-03
Sliketymo,

Thanks for your input. That was the first thing I tried to do so I could restore the backup files I had made earlier; however I could not access the file system on the mounted drive for some reason.

All I could get to was the file system of the live cd, which is not what I was looking for. Therefore I could not undo what I did via that method.

Any other ideas please?

WB

---

### Post by sliketymo on 2009-11-03
This might help:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by wacky.banana on 2009-11-03
Hi again,

After 4 hours of intense frutration I gave up and decided to rebuild as nothing from the exhaustive long thread that you pointed me to worked.

Seems like the Ubuntu partition had somehow become corrupted when I originally updated Grub 2 as I ended up having to reformat it to make grub stick.

I am slowly rebuilding the PC, this time starting with the highly breakable items first like grub 2 tuning. When complete and working to my satisfaction I will rebuild fully to spec.

Found quite a useful link which should help others running Karmic here....[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html](http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html)

Once again thanks for your help; much appreciated.

WB

---

### Post by sliketymo on 2009-11-03
Grub 2 is a rather new animal for folks it seems.Yes,researching ones equipment is a pain,but well worth the effort.My two cents:I dont spend time staring at a splash screen.I use my computer to accomplish a task,not admire the pretty boot-up show,but thats just me.Good luck to you!

---

### Post by wacky.banana on 2009-11-04
Sliketymo,

Completely agree with your comments on the key purpose of using a PC. However having moved across from MS Windows 6 months ago I have been anxious to upskill myself to the same level of unconscious proficiency in Ubuntu as I have in Windows.

For me though the proof of the pudding has definitely been in the eating and I can see why the average user still finds it more difficult to use Linux than MS Windows.

So far my experience of 910 has been disappointing, compared to the magic I experienced when I first moved to 904. However rather than moan about it I intend to persevere.

I definitely think that Canonical should move to an annual refresh rather than this 6 monthly cycle which does not give them enough time to sort out the bugs and annoyances that are a real pain to everyday use. The 100 annoyances project is a master stroke and allied to an annual refresh cycle should allow Ubuntu to hold its head up compared to MS Windows in the acceptability and ease of use categories.

Meanwhile I am off to crack the next problem which is to establish why Ubuntu will not reconnect my network card when it comes out of hibernate/sleep mode (same problem as in 904).

Again thanks for your help here; appreciated.

WB

---

