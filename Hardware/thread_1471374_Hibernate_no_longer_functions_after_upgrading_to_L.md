---
title: "Hibernate no longer functions after upgrading to Lucid"
date: 2010-05-03
forum: Hardware
---

### Post by Alvin Chiu on 2010-05-03
Hi everyone,

I have an ThinkPad T43 which was able to suspend and hibernate without problems in Karmic.  After upgrading to Lucid, suspend still works fine, but hibernate no longer works.
What happens is that if I click on Hibernate from the shut down dialog, it will cut to screensaver, the sleeping LED light on my laptop will flash as if preparing to hibernate, the screen will blank for a second, and then it will just go back to the screensaver/password prompt.  Basically the computer never turns off when I tell it to hibernate.  

I'm thinking of doing a clean reinstall of Lucid since I only did the upgrade from Karmic.  Does anyone have this problem with a clean installation?

---

### Post by Alvin Chiu on 2010-05-03
Just an update,

I tried a clean install of Lucid and tested hibernation.  Surprise, surprise, it still has the same problem.  :confused:  The swap space is large enough to handle hibernation, so I'm stumped.

---

### Post by antiram on 2010-05-03
does kernel hibernate work as root from a terminal?
sync; echo -n 4 >/proc/acpi/sleep

does it work with the script from package pm-utils from a terminal?
/usr/sbin/pm-hibernate

messages in /var/log/messages?

---

### Post by themusicwave on 2010-05-03
I too have hibernate issues after upgrading to lucid.  Mine is manifesting differently though.  My machine will hibernate, but it won;t come out of hibernation right.

When I try to bring it back up, I see the password screen and then suddenly I get a complete black screen with a blinking _ cursor.  At this point it will not wake up at all.  I then have to hard reboot the machine.  However, if I don't go into recovery mode it will once again show the password dialog and then go to the blinking _.

If I start in recovery mode it comes up fine.  I can then reboot in normal mode and it comes up.

Not sure if mine issue is related, I certainly don;t want to hijack the thread if it isn't.

---

### Post by gambetti on 2010-05-04
Hi, 
I have the same problem on a thinkpad 40p - docked and undocked.
thank you for the help

---

### Post by brice83 on 2010-05-04
i have a t400, and since karmic, the hbernation and suspend have not work well for me.sometime , it resume without problems but a most of time, the led of suspend and the led of batterie is on and nothing happen, i need to hardly reset the laptop and loose the work that i was doing.
i will be interest by any solution.
 thank 

NB: excuses for the poor english, i'm not a native english speaker

---

### Post by Alvin Chiu on 2010-05-04
> **antiram said:**
> does kernel hibernate work as root from a terminal?
sync; echo -n 4 >/proc/acpi/sleep

does it work with the script from package pm-utils from a terminal?
/usr/sbin/pm-hibernate

messages in /var/log/messages?

antiram,

Thanks, I tried both of your methods last night from the terminal, and hibernation worked successfully.  For some reason, the next day, I tested hibernation again and it now works  from the shut down dialog.  Strange. :-s

Keeping this thread open for the others having hibernation/suspend problems.

---

### Post by gambetti on 2010-05-05
hello Alvin Chiu and Antiram and everyone,

I've tried the commands from the terminal, and the first one gave me the following answer:
*bash: echo: write error: Cannot allocate memory*

pm-hibernate started hibernating (the "moon led" was blinking), but nothing happened besides that my internet connection has been interrupted for a short moment (as it were going to hibernate).

The problem isn't so big, because the start up of ubuntu is very fast, but it would be nice to have the function again.

Thank you

---

### Post by Alienhunter2010 on 2010-05-06
> **antiram said:**
> does kernel hibernate work as root from a terminal?
sync; echo -n 4 >/proc/acpi/sleep

does it work with the script from package pm-utils from a terminal?
/usr/sbin/pm-hibernate

messages in /var/log/messages?

I try it on my Aspire 6920.

[LIST]
[*]first command freeze the laptop, without turning off the video and sound card (that goes in loop!).
[*]second command turn off the video but, striking the keyboard or moving mouse, the laptop do not wakeup! Monitor is black but not really turned off: on the top left the text cursor  is blinking!
[/LIST]

Hibernation was working right on the previous ubuntu 9.10. I've done a fresh installation BUT I keep my home!

Thanks to all, Alex.

---

### Post by Alienhunter2010 on 2010-05-07
Additional info: when I ask to hibernate the session the screen fade to black, then retro light is turned on again and the monitor, on text mode, show the blinking cursor.

If I strike Ctrl+F1 I switch to the login of the text console, but keyboard does not accept any other keys. And I have to turn off the PC by the power button.

I would like to connect by another PC using an ssh shell, hoping to be able to see what dmesg says.

Thanks again, Alex.

---

