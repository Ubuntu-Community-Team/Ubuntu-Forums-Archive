---
title: "Screen &quot;dead&quot; after closing laptop lid"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by cninham on 2005-08-12
I have a Dell Latitude C840 laptop.  It is running the Intel Mobile Pentium 4 2.20 GHz CPU, 512 MB RAM, and nVidia GeForce4 440 Go video card.  I have installed Ubuntu Linux 5.04 (the Hoary Hedgehog Release).

Everthing installed fine, and the system seems to be running great.  However, when I close the lid of my laptop, and open it up after a while, the screen is dead/blank.  (It appears that the system is running, I can hear disk and cooling-fan activity.)  No matter what I try, I cannot get the screen to turn on.  The only thing I can do is to hit the power button, let the system power down (normal system shutdown), and then power the system back up -- then the screen will be "visible" again.

I do not know where to start, or HOW to start debugging.  I have run Linux before, not Ubuntu Linux, but I have run Red Hat (various versions), Mandrake, Debian, and Slackware.

Any help will be appreciated.

Thank you.

Cameron

---

### Post by DancingSun on 2005-08-12
This might have to do with the laptop going into sleep/hibernate mode and having trouble waking up again.  Perhaps you should investigate in that direction?

---

### Post by cninham on 2005-08-12
Thank you for the reply.  

My main problem in with determining the cause of the problem: I cannot see or read anything the screen, I cannot debug anything as I cannot "see" what is going on.  I know that if I close my laptop lid for as short as a minute or two minutes, it will "freeze" and lock up, go blank.

Cameron

---

### Post by DancingSun on 2005-08-12
Well, lets see. Your screen is working, just that when you close the laptop lid, it goes black, and is not able to come back on.

This is likely that when you close the lid, the laptop when into power saving mode, either sleep mode or hibernate mode.  Try disabling these modes in Ubuntu.  Unfortunately I'm not a laptop user, so I can't give you specific directions on how to do that.  You'll need to look that up yourself.

Now, after disabling sleep/hibernate mode, try closing the lid again, and re-open it later to see if the screen is still blacked out.  If the screen came back on, then that means something is wrong with the sleep/hibernate settings.  I'm sorry to say that I have no idea about these settings, so I can only take you this far.  But at least you will have been able to narrow down the problem area.

If the screen is still blacked-out after disabling sleep/hibernate mode...then at least we will have eliminated that as the source of the problem.

---

### Post by PeP on 2005-08-12
I agree with the parent poster, 
acpi scripts are in /etc/acpi
just try to replace lid.sh with an empty script;
cd /etc/acpi
sudo mv lid.sh lidback.sh

(just move the other way around to restore it ...)

you might find usefull infos in /var/log/acpid

if you have another box, just use  ssh !

---

### Post by cninham on 2005-08-13
PeP and DancingSun; thank you for your reply.  I have tried renaming the /etc/acpi/lid.sh file, but it did not seem to resolve my problem.  When I close my laptop lid and open it back up the screen still remains blank.  I have returned the lid.sh file back to its original name.

I have uploaded some of my log files -- see the **attached file: logs.tar.gz**.  Can someone have a look at the logs and hopefully direct me to the source of my issue, please?

Thank you,

Cameron

---

### Post by s_p_a_r_k_y on 2005-08-13
cninham

maybe you need to tell it which screen to go back to? Try closing the lid and then after a minute open it. Press alt-F7 which should be the first X instance. My laptop did that until I changed the behavior.

---

### Post by cninham on 2005-08-13
Sparky,

Thank you for your suggestion.  I have tried using Ctrl+Alt+F7, or any other combination of Ctrl+Alt+F1 through Ctrl+Alt+F7, etc., but none of these brought the screen back again -- it remained blank.

Cameron

---

### Post by s_p_a_r_k_y on 2005-08-13
can you login remotely via SSH or with VNC?

---

### Post by aveline on 2005-08-13
[QUOTE=s_p_a_r_k_y]can you login remotely via SSH or with VNC?[/QUOTE]
 when you boot up, try hitting ESC at the grub countdown screen, then follow directions on the bottom of the screen on how to edit the file, edit the kernel line & at the end put this:

... noacpi noapm noapic

try them one at a time, and if it doesn't work, try a few in combinations with each other & see what happens.  Did you disable powermanagement in the bios?  That may be doing it too.  Also look on [www.linuxonlaptops.com](www.linuxonlaptops.com) *I think is the link* for your model/brand & see what others have come up with.

aveline

---

### Post by ils_systems on 2005-09-30
I am running Breezy on Dell Inspiron 1200.  My display also didn't come back on after closing the lid.  I was getting an error message about the $DISPLAY variable not being set in /var/log/acpid.  To fix this problem, I edited the file /etc/acpi/lid.sh and added "-display :0.0" to xset and xscreensaver-command.  Now after I open the lid, the screen comes back on and asks me to enter my password.  Hope this helps.

Here is the output for lid.sh
#!/bin/sh

. /usr/share/acpi-support/power-funcs

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

getXuser;

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        . /usr/share/acpi-support/screenblank
else
        grep -q off-line /proc/acpi/ac_adapter/*/state
        if [ $? = 1 ]
        then
                su $user -c "xscreensaver-command -unthrottle"
        fi
        su $user -c "xscreensaver-command -display :0.0 -deactivate"
        su $user -c "xset -display :0.0 dpms force on"
fi

[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

---

### Post by Panthios on 2005-09-30
> **ils_systems]I am running Breezy on Dell Inspiron 1200.  My display also didn't come back on after closing the lid.  I was getting an error message about the $DISPLAY variable not being set in /var/log/acpid.  To fix this problem, I edited the file /etc/acpi/lid.sh and added "-display :0.0" to xset and xscreensaver-command.  Now after I open the lid, the screen comes back on and asks me to enter my password.  Hope this helps.
Here is the output for lid.sh
#!/bin/sh
. /usr/share/acpi-support/power-funcs
[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre
getXuser said:**
> 
then
. /usr/share/acpi-support/screenblank
else
grep -q off-line /proc/acpi/ac_adapter/*/state
if [ $? = 1 ]
then
su $user -c "xscreensaver-command -unthrottle"
fi
su $user -c "xscreensaver-command -display :0.0 -deactivate"
su $user -c "xset -display :0.0 dpms force on"
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

Sticky!! That worked for me :)
I had that problem, that everytime I closed the lid and then opened it again, I had to press ctrl+alt+F7 to get back to X.
Not the biggest problem, I know, but it was annoying.

---

