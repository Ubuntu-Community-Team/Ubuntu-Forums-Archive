---
title: "Problems with Screen Resolution"
date: 2005-01-07
forum: Installation &amp; Upgrades
---

### Post by TheDude on 2005-01-07
I'm extremely new to Linux and am having problems with my screen resolution.  My friend installed Linux on my second drive a week ago and I have been messing around with it with the hope of getting away from windows eventually.  When he installed it, we had to use his monitor which has a max resolution of 1024 * 768, because mine was having problems.  When I got my monitor working and hooked it up, the max resolution that Ubuntu will let me use is 1024 * 768 even though my monitors max res is 1280 * 1024.  He tried to fix the problem for me, but was stumped and I have no clue what to do from here.  

Please help a n00b  :confused:

---

### Post by fng on 2005-01-07
Go to the Top-Left of the screen
Computer -> System Configuration -> Screen Resolution

---

### Post by TheDude on 2005-01-08
Yeah, I've tried that, but the highest it goes up to is 1024 * 768.  I can run the same monitor on xp pro and it will run at 1280 *1024

---

### Post by scannereaf on 2005-01-08
during bootup kindly go to the unbuntu (recovery mode)
..... then u will have an option to type in ur root pswd 

once u r in root: 
type in **vi /etc/X11/XFconfig something ... XFconfig-4 i guess...** 
then there is an option to automatically update it
copy the three lines of commands and exit it 

just follow the option screen (just enter on the default entry) until u need to change the **horizontal sync and vert sync**

hope that works

=)

---

### Post by fng on 2005-01-09
Open up any terminal
Then type 'sudo nanoi /etc/X11/XF86Config-4' (or replace nano by your favorite editor)
Look for the section that looks like this:
```
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection
```
Change the resolutions according to your monitor

Then you need to look for:
```
Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5 - 68.7
    VertRefresh 50-160
    Option "DPMS"
```
Change theHorizSync VertRefresh according to your monitor

Save the file, log out of gnome, and log in again.

This can be a bit hard in the beginning, don't give up on it!

---

### Post by TheDude on 2005-01-09
[QUOTE=fng]Open up any terminal
Then type 'sudo nanoi /etc/X11/XF86Config-4' (or replace nano by your favorite editor)[/QUOTE]

I just tried this and it says 'sudo: nanoi: command not found'

---

### Post by TheDude on 2005-01-09
oops!, nano, not nanoi.  Okay, so I edited the first part and that didn't seem to work.  But I don't know what to put on HorizSync or VertRefresh...Where do I find that info about my monitor?

---

### Post by wallijonn on 2005-01-09
Since he is used to Windows it would be best to use a known editor like gedit since it is the defaukt text editor. 

you would therefor start a Root Terminal (Applications -> System Tools -> Root Terminal) and issue a [COLOR=Red]sudo gedit /etc/X11/XF86Config-4[/COLOR] command. 

Or we can direct him to run [COLOR=Red]/etc/X11R6/bin/xf86config[/COLOR]. The mouse is [COLOR=Blue]/dev/input/mice[/COLOR] and you enable 3 button emulation.

---

### Post by TheDude on 2005-01-10
Ok, I just tried that and no worky.  I guess I'll just have to mess with this for a while and hopefully I'll get it working eventually.  Thanks for all the help so far and if anybody has any other ideas, I'm all ears. :mrgreen:

---

### Post by hashimoto on 2005-01-10
The Dude, run "dpkg-reconfigure xserver-xfree86" and answer the questions. Sould be easy enough 'cause even I was able to do it. I was also missing the higher resolution...

BR
Hashimoto

---

### Post by hashimoto on 2005-01-10
Oh, and I found this in the FAQs:
[http://www.ubuntulinux.org/support/documentation/faq/RreprobeMonitor](http://www.ubuntulinux.org/support/documentation/faq/RreprobeMonitor)

Hashimoto

---

### Post by TheDude on 2005-01-10
[QUOTE=hashimoto]The Dude, run "dpkg-reconfigure xserver-xfree86" and answer the questions. Sould be easy enough 'cause even I was able to do it. I was also missing the higher resolution...

BR
Hashimoto[/QUOTE]

Thanks for the tip...but I tried that and couldn't get it to work.  I ran through all the questions but never saw anything that had to do with resolution.  Then I looked at that faq and couldn't figure anything out from there.  I wish I wasn't so new at this.  Other than this little problem, I am loving Ubuntu

---

### Post by TheDude on 2005-01-10
Thanks again everyone for the help.  I've been talking to a friend who is much more knowledgable then myself about Ubuntu and he has been working on my computer trying to help me solve this problem.  He has concluded that the problem is probably with my extremely old ATI video card.  So I've decided that I'm going to go ahead and make an upgrade that I should have made long ago. 

On top of that, I have to send my new monitor back because it has a flaw, so I wont be using my desktop computer for a while.  Hopefully when I get the new card and my monitor back I can finally solve the problem.  Thanks again to everyone and I will update when I get everything back.

---

### Post by scannereaf on 2005-01-10
i agree with hashimoto...i guess that's fairly easy...
try to vi XF86Config-4 and u will see how to run the dpkg-reconfigure xserver-xfree86.

=)

---

### Post by TheDude on 2005-01-10
[QUOTE=scannereaf]i agree with hashimoto...i guess that's fairly easy...
try to vi XF86Config-4 and u will see how to run the dpkg-reconfigure xserver-xfree86.

=)[/QUOTE]

Yeah, I tried that but no worky.

---

### Post by TheDude on 2005-02-01
Well I just got my new Dell 17" Ultrasharp monitor set up, and it is letting my use the max resolution.  Not sure why it wouldn't let me on the other monitor, but oh well, it's working now.  One step closer to getting rid of windows

---

