---
title: "Laptop headphone detection in Karmic solution"
date: 2009-11-08
forum: Hardware
---

### Post by wileur on 2009-11-08
It seems that with the new Karmic there is no obvious way to enable headphone detection. After a bit of googling and some testing it turns out that all you need to do(at least on my laptop) is to "unmute"(funny term) Alsa's 'Headphone Jack Sense'. In previous Ubuntu versions you could enable it right in the volume control, but Karmic requires a little more work.

A big thanks to egaistek at [vaioubuntu]("http://vaioubuntu.wordpress.com/2009/07/07/headphonesfront-switch-script/") whose post got me looking at amixer.

**The quickest way** of doing it is to run alsamixer in a terminal and unmute 'Headphone Jack Sense'. Navigate to the control and press 'm'. If it in the top left corner before said Item: ...... 'off', 'off' should now be gone. Exit with Ctrl-C. Done!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135308&d=1257700399[/IMG]

**The more practical way** is to use amixer and make a script that is run every time you log in. 

**[COLOR="Red"]In the following steps, replace the X in /home/X/headphonejs with your user name.[/COLOR]**

**Create the script.** Open gedit Text Editor(Applications->Accessories->gedit) and paste in the following:

```

#!/bin/bash
# Script for activating Headphone Jack Sense
#Andreas Wileur <wileur@gmail.com> 2009-11-08

amixer -c 0 sset 'Headphone Jack Sense' unmute

```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135310&d=1257700399[/IMG]

**Save the file** in your home directory, call it headphonejs
**Make it executable.** Press ALT+F2 to open the run dialog. Enter the following and press enter:
```
chmod +x /home/X/headphonejs
```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135311&d=1257700399[/IMG]

**Make it run at startup** Go to System->Preferences->Startup Applications.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135313&d=1257700535[/IMG]

**Click 'Add'** and enter the following:
```

Name: Headphone Jack Sense
Command: /home/X/headphonejs
Comment: Activate Headphone Jack Sense

```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135309&d=1257700399[/IMG]
Click 'Add' and then in the first window 'Close'

**Start it.** Now you can either logout and re-login or manually run your script by pressing ALT+F2 and entering this:
```

/home/X/headphonejs

```

That's it! From now on your computer will sense the headphones.

---

### Post by juana on 2009-11-21
hey i was just wondering, why does my alsamixer doesn't have that option and many others? i added an image

---

### Post by juana on 2009-11-21
i forgot to explain my problem (:   my headphones don't work and i wanted to use your solution but my alsamixer doesn't have the "headphone sense option". any help is appreciated, thanks

---

### Post by muratcorlu on 2009-12-07
I have same problem and I don't have "Headphone Jack Sense" option. How can I solve this problem?

---

### Post by nazishy2k on 2009-12-19
i am not able to get sound from the headphone after unmuting the headphone. There is no option to increase headphone sound i use the front arrow key of the keyboard to increase sound but it is disabled not working. i am attaching the snapshot of alsamixer.In mine also jack sense option is not there. Please help i want to listen music from my heaphone
:(:(

---

### Post by markoper on 2009-12-23
same on aspire 5735 with karmic. no jack detection, so impossible to switch off speakers while using headphones. on alsamixer missing sense option.

---

### Post by .ringaila on 2010-03-02
> **nazishy2k said:**
> i am not able to get sound from the headphone after unmuting the headphone. There is no option to increase headphone sound i use the front arrow key of the keyboard to increase sound but it is disabled not working. i am attaching the snapshot of alsamixer.In mine also jack sense option is not there. Please help i want to listen music from my heaphone
:(:(
same on Asus F3Ka laptop.

---

### Post by ellaivarios on 2011-06-21
has anyone found a way to activate this feature/tool/option in Alsa Mixer? In my alsa mixer I do not have this option for "headphone sensor Jack" so I cannot disable it and enable it at will so as to have both my speakers and the headset play audio at the same time.

I can do it in Microsoft Windows 7 with a little Tweak tool, so I SHOULD be able to do it in Linux too!

Any ideas?

thank you.

---

### Post by compilable on 2011-06-30
> **wileur said:**
> It seems that with the new Karmic there is no obvious way to enable headphone detection. After a bit of googling and some testing it turns out that all you need to do(at least on my laptop) is to "unmute"(funny term) Alsa's 'Headphone Jack Sense'. In previous Ubuntu versions you could enable it right in the volume control, but Karmic requires a little more work.

A big thanks to egaistek at [vaioubuntu]("http://vaioubuntu.wordpress.com/2009/07/07/headphonesfront-switch-script/") whose post got me looking at amixer.

**The quickest way** of doing it is to run alsamixer in a terminal and unmute 'Headphone Jack Sense'. Navigate to the control and press 'm'. If it in the top left corner before said Item: ...... 'off', 'off' should now be gone. Exit with Ctrl-C. Done!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135308&d=1257700399[/IMG]

**The more practical way** is to use amixer and make a script that is run every time you log in. 

**[COLOR=Red]In the following steps, replace the X in /home/X/headphonejs with your user name.[/COLOR]**

**Create the script.** Open gedit Text Editor(Applications->Accessories->gedit) and paste in the following:

```

#!/bin/bash
# Script for activating Headphone Jack Sense
#Andreas Wileur <wileur@gmail.com> 2009-11-08

amixer -c 0 sset 'Headphone Jack Sense' unmute

```[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135310&d=1257700399[/IMG]

**Save the file** in your home directory, call it headphonejs
**Make it executable.** Press ALT+F2 to open the run dialog. Enter the following and press enter:
```
chmod +x /home/X/headphonejs
```[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135311&d=1257700399[/IMG]

**Make it run at startup** Go to System->Preferences->Startup Applications.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135313&d=1257700535[/IMG]

**Click 'Add'** and enter the following:
```

Name: Headphone Jack Sense
Command: /home/X/headphonejs
Comment: Activate Headphone Jack Sense

```[IMG]http://ubuntuforums.org/attachment.php?attachmentid=135309&d=1257700399[/IMG]
Click 'Add' and then in the first window 'Close'

**Start it.** Now you can either logout and re-login or manually run your script by pressing ALT+F2 and entering this:
```

/home/X/headphonejs

```That's it! From now on your computer will sense the headphones.


Thank you very much for the comprehensive explanation. It worked perfectly. :P

My Laptop was : HP Laptop with Ubuntu 11.04 (natty). 

Good post !! :KS

---

