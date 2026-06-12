---
title: "ubuntu help"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by Goemon4 on 2006-04-27
i have a fairly old ibm thinkpad that ran win 98, now it wont boot into win 98 (all it says is pleas insert system diskette, which i dont have) and im trying to install ubuntu onto it with an iso file (that i downloaded from the ubuntu site)and burnt it to a disk on my mac.

 my question is how can i install linux onto the thinkpad if i cant boot onto windows???


thanks
-Goemon4

---

### Post by jazzmuzik on 2006-04-27
You don't need Windows at all for an Ubuntu install.

Go into your computer's BIOS settings and tell it to use the cdrom as the first boot device. Then put the Ubuntu CD in the drive and reboot. Ubuntu should then start the installation process.

---

### Post by Goemon4 on 2006-04-27
ok thanks

---

### Post by Goemon4 on 2006-04-27
sorry for the dubble post, but i only had to download one iso right?? (ps i am new at this) also was there anything else i needed??

---

### Post by jazzmuzik on 2006-04-27
Right. There's only one install iso file that you burn to a CD. The rest of the programs can be installed from the Ubuntu repositories once you are online.

I think the DVD version has more stuff on it, but I'm not 100% sure about that.

---

### Post by Goemon4 on 2006-04-27
ok so i did that but it keeps saying please insert system diskette (after configuring the bios settings) what else could i do??

---

### Post by jazzmuzik on 2006-04-27
Hmm. Look at the BIOS settings again. Your first boot device should be your cdrom. The second one isn't important at this point, but it could be set to your hard drive.

And make sure the Ubuntu install disk is loaded in the cd drive before you reboot. Very important.

If this doesn't work, I'd say you burned a bad disk. You **must** burn the Ubuntu iso file in iso mode, sometimes called "image" mode. Burning in data mode won't work.

---

### Post by Goemon4 on 2006-04-27
it just says boot from c driv or boot from a drive, bu tuderneath that it says boot from cd and its enabled...but nothing happens.....well except for the "please insert system diskette"

---

### Post by jazzmuzik on 2006-04-27
[QUOTE=Goemon4]it just says boot from c driv or boot from a drive, bu tuderneath that it says boot from cd and its enabled...but nothing happens.....well except for the "please insert system diskette"[/QUOTE]

The CD being underneath the other drives is the problem. See if you can move the CD to the TOP position. That should make the CD the FIRST boot device. You see, you don't want to just enable the CD. You want to make it FIRST in the list of boot devices. See if there is a keystroke to move the drives up and down on the list.

---

### Post by confused57 on 2006-04-27
The bios in a computer I bought in 2000 doesn't support booting from CD so  I had to use a floppy with Smart Boot Manager to boot from the CD rom:

[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

I'm not sure if there is a rawrite for mac  though.

---

### Post by jazzmuzik on 2006-04-27
[QUOTE=confused57]The bios in a computer I bought in 2000 doesn't support booting from CD so  I had to use a floppy with Smart Boot Manager to boot from the CD rom:

[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

I'm not sure if there is a rawrite for mac  though.[/QUOTE]

Wow. I didn't know that was possible. All of mine for years and years could boot from CD.

However, I don't think that's the problem here.

---

### Post by confused57 on 2006-04-27
Here's another thread about burning iso's, which may help(good luck):

[http://www.ubuntuforums.org/showthread.php?t=167182](http://www.ubuntuforums.org/showthread.php?t=167182)

---

### Post by Goemon4 on 2006-04-28
wow thanks for all of the help, im at school right now, so ill try this later...

-Goemon4

---

