---
title: "so confused.. gnome display wont initialize on reboot"
date: 2008-09-06
forum: General Help
---

### Post by esaruoho on 2008-09-06
hi. yesterday evening, i was browsing away, and firefox crashed. i tried to restart firefox3, but it said it was already running. well, that's normal for firefox3 (that it doesnt show up in top after crashing, and wont start after a "proper" crash). i took out my konqueror, and browsed around with that. after a while tho, i decided to restart the machine.

i restart the machine, and it gives me the ubuntu progress bar on load, the screen blanks and turns into the "soon theres a circle on the center with a few pixels rotating" "wait-sign", but instead of graphical user logon (i guess this is GDM), i instead get a big STOP sign and a window pops up that just says [][][][][][][][][][][][][][][][][][][][][][][][][][][][][] at me. this apparently signifies that the font for the warning is broken. so i click enter on it a gazillion times, and eventually get a blue screen that says that 
*The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display:0*

needless to say, i was totally stumped. i was fooling around and pressed ctrl-alt-f1 and logged on as the user, and did a "startx". i was back in business. but the ubuntu 7.14 would still give me grief  on reboot, and that STOP / broken font window. i tried with the recovery mode.. - to no avail. then i decided to log on as root and upgrade to ubuntu 8. it took a while, and i restarted, and i still got the same STOP button.

after that i've been flittering away, doing a gdmsetup here (set from "run xclient script" to "gnome" or "gnome secure", no difference). i've been "startx" as root and as my normal username, and both seem to work, except that my usbsticks are only accessible in root mode. probably because i was clever enough to install ubuntu8 not as a user but as the root. 
the sticks complain this: 
[I]cannot mount volume
Error org.freedesktop.DBus.Error.AccessDenied
Details
A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")[/i]

anyway, i'd really appreciate it if any of you could please advise me how to get back to the graphical logonscreen, i dont know which log to read to see what the problem is (im guessing theres a log that logs the error that that window with the broken fonts gives, but i dont know how to get to it).

i also cannot use "dpkg repair" in the recovery mode, because it complains that i am not online (even tho i am - but apparently not in the  boot recovery mode. i tried pressing "pump" in root  to get internet working  before the "dpkg repair", but that didnt do anything either.

so, uh, how do i get the gdm to let me log in graphically and back to business as usual, please?

i even tried "sudo dpkg-reconfigure -phigh xserver-xorg" that some x11 problem thread mentioned, cos i was feeling like giving it a shot.

another (im not sure if its related) thing i get on the alt-ctrl-f1 flitterings is:
[I]"kinit: name_to_dev_t(/dev/disk/by-uuid/685f503b-462f-45a2-8a8d-4fe6244f6251=
sda5(8,5)
kinit: trying to resume from
/dev/disk/by-uuid/685f503b-462f-45a2-8a8d-4fe6244f6251
kinit: No resume image, doing normal boot..."[/i]

could this somehow be related to the issue?

the main issue is that i have no idea if ive messed up myself or if i've been taken over somehow. im pretty clueless now, as you can see.

any ideas?


so um, what exactly can i do


demands. at first i thought everything was broken and i gotta install a new version of ubuntu or something, or someone took me over or something, but then i realized that ctrl-alt-Fx keys allow me to log in. so what i did was (i had used a 7.0.4 or something for quite some time) i logged on as root, started startx and did an upgrade to 8.0.4 or something.
before that, i tried to see if the boot selection menu's "recovery" mode would load up, but bumped into the same block-stop-window popups (no matter how many times i click on "ok" (i guess its ok, it looks like [][]), it still waits for a while and then sends me onto another one)))
when i was doing the upgrade to version 8, it kept saying that it cant initialize the display. well, i hoped that upon reboot, 8 would just work and that'd be it, but here i am back again with startx running.. things would be semi-ok (i could instruct my gf to do this thing to get online) but unfortunately i cannot seem to get any usb-sticks to be mounted.
when i do slap in a usbstick, a popup comes in and says

[I]cannot mount volume
Error org.freedesktop.DBus.Error.AccessDenied
Details
A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")[/I]


it was a major win for me to at least be able to start another instance of x (or something). i tried apt-get installing metacity but it didnt do anything. (i was working under the impression that maybe gnome/gtk/metacity had somehow corrupted. im probably not using the right terms).

i dont have an empty cdr right now to burn the 8.0.4 hardy heron live cd, but i do have the .iso stashed now (was in a panic). so, erm, how do i recover my "close machine, turn machine on, ubuntu boots and lets me log on, then gives me usbsticks and a functioning x" status?:)

---

### Post by esaruoho on 2008-09-06
deleted

---

### Post by esaruoho on 2008-09-06
deleted

---

### Post by esaruoho on 2008-09-06
deleted

---

### Post by esaruoho on 2008-09-06
deleted

---

### Post by esaruoho on 2008-09-06
deleted

---

### Post by esaruoho on 2008-09-07
deleted

---

### Post by esaruoho on 2008-09-07
ive reinstalled usplash, reinstalled gnome, tried to reinstall gdm.. the broken font window's "button highlight" doesnt say anything to any letter i can input to it.. and i dont know how to read the log or to find the log that contains the error the broken-font window gives.

---

### Post by esaruoho on 2008-09-07
deleted

---

### Post by esaruoho on 2008-09-07
i was instructed to remove gdm and reinstall it 
sudo apt-get install gdm

but it didnt do any good.. ohwell, :confused:

now i have set gdmsetup to load KDE, lets see what happens:)

---

