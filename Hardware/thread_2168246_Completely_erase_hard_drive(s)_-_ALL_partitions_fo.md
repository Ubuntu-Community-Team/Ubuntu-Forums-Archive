---
title: "Completely erase hard drive(s) - ALL partitions for fresh Ubuntu Install"
date: 2013-08-17
forum: Hardware
---

### Post by ssk-copan on 2013-08-17
Dear Users, Gurus, and Gods, (technical symptoms at bottom)
[B]
Mission Statement:[/B]  Completely erase all hard drives/partitions/recovery partitions/BIOs and install fresh copy of Ubuntu 12.04 LTS.  So that is my question, is there a tool or method to safely and completely erase everything, thereby wiping out any possibility of a virus surviving?

See below for all details..

  I seek your help today for an issue I have been battling for the last 8 hours and am about to resume tomorrow.  I'll try to keep it short and sweet..  but I'm keeping in as many details as I can in case someone knows the issue specifically.

  I am working on a laptop for my Korean friend and tutor.  It is an LG which is about 5 years old and purchased in Korea.  Initially she had a pirated copy of Windows 7 Ultimate K, then pirated Windows 8 Pro from halloweenpsycho (and I digress, I'm not trying to promote pirated software in any way).  Anyway.. everything was working very well until last Thursday when she texted me to let me know there was a problem opening program windows.

  I checked it out myself, and it acts in some ways like a virus but in other ways it leads me to believe it could be a hardware malfunction.  In order to avoid future software issues I obviously opted and highly recommended to her an Ubuntu install.  She said that would be okay, but unfortunately I couldn't get the install CD to boot.  After running in safe mode and changing msconfig to load only such and such I somehow got that Windows 8 cd to boot for me, and made a new install.

[U][I]Here are the symptoms:


[/I][/U]
[LIST=1]
[*]Symptoms persist even after deleting and creating new partition on main Windows drive, then reinstalling Windows.  There is also an extra storage partition (not sure if it is physical drive or virtual as it is laptop).  I am going to delete that tomorrow.
[*]In BIOS menu before OS starts it will ask to save and quit without saving changes, but won't choose an option, just goes back and forth sporadically.  This  can cease by rapidly pounding on any key.  Then I can proceed to change BIOS settings.
[*]Boot doesn't work for Ubuntu CD, just get that annoying BEEP BEEP BEEP sound from inside the computer. The one you get from any machine when holding down F-buttons too long on boot.
[*]In Windows itself, program windows will minimize or choose not to open spontaneously.  Sometimes it works, sometimes it doesn't.
[*]Typing in the Windows Start Screen, or Internet Explorer and some other applications I get spaces in between letters and it sporadically deletes my text, making me start over.  After multiple attempts I concluded it was not targeting specific letter combinations (kaspersky, virus, keyboard etc..) just random.  **However.. I can type JUST FINE in Microsoft Word. ??**
[*]I can open msconfig and Task Manager okay, but msconfig can sporadically close.  Again, sometimes it works and sometimes it doesn't.  This is atypical for a virus in my opinion, as past viruses would simply block you from accessing system tools like msconfig.
[*]Again, spontaneously as I'm typing I sometimes get thrown back to Windows start screen but I haven't pressed the windows button.  Especially when trying CTRL+A to highlight all text.
[*]To summarize, this abnormal behavior is inconsistent with any virus I've seen, and symptoms persist even in BIOS and after a new install of Windows.
[/LIST]

That wraps it up for the symptoms.  Now I just want to delete everything and install a fresh copy of Ubuntu 12.04 LTS.

Thank you so much for your time.

---

### Post by ssk-copan on 2013-08-17
Also I don't believe it's a physical sticky key problem, as I can type just fine in MS Word.  So strange.

---

### Post by grahammechanical on 2013-08-17
Flashing the BIOS is a separate action not connected to installing Ubuntu. Do you think that the BIOS is infected?

As for your other mission just download a copy of Ubuntu 12.04.2 and burn it to DVD. Set the BIOS boot options to look at the DVD Drive for an operating system before looking to the hard drive and then boot the machine with the Ubuntu DVD in the drive. The Live session will load. Select Install Ubuntu and you will be asked to chose an install option select to Erase Disk and Install Ubuntu.   And that will do what you want.

Linux uses a different file system to Microsoft. So, installing Ubuntu with this option will Erase everything on the disk and create two Linux partitions. One for Ubuntu formatted as £xt4 and one for a swap partition. Everything previously on the disk will be gone.

Regards.

P.S. I gave an answer according to the post heading. Which failed to indicate the true problem. Try using another keyboard. If the keyboard does not work in the BIOS then it must be a keyboard problem and not an OS problem. Have you asked yourself what the three annoying bleeps are trying to tell you? They might be saying faulty keyboard.

---

### Post by sourchier on 2013-08-18
Three beeps is bad base memory (Base 64K mem failure). It can also cause keyboard and other "random" errors. Sometimes this can be fixed by flushing the bios by removing the battery for five minutes, or so. If the problems continue a new bios battery may be needed.
As for your original question. You can wipe everything by downloading, burning, and using this:

[http://www.dban.org/]("http://www.dban.org/")

However, you need to back up **everything** before use. Good luck.

---

