---
title: "Ubuntu Karmic Koala froze and now won't boot at startup!!!"
date: 2009-11-14
forum: Hardware
---

### Post by XProflmfao on 2009-11-14
My laptop won't load now!!! Okay, so it all happened last night. I was using Mozilla Firefox and surfing the web as usual, when all of a sudden Firefox stops responding. Then, I try to close the program by clicking alt-F2. It didn't close. So then I right clicked on the Firefox tab on the bottom taskbar. The menu popped-up, and I tried to click Close. Nothing responded, and now the menu was frozen on my screen too. And then I tried to restart the computer by pressing on the top taskbar. It wouldn't respond, and no that taskbar was frozen too!!! In the end, I had to shut my computer by closing the laptop lid. I know this means that I never really shut down the computer, but I just put it to sleep. I think that's what caused the whole messup.

But anyway, after waiting a few minutes, I try to open my computer again. Everything is normal, the system's booting up, but then the Ubuntu icon stays on my screen a little bit too long. Usually when I boot up Ubuntu, my hard drive is flashing a LOT once I get to the Ubuntu icon part, just before it goes into the log in menu. But then this Ubuntu icon stays there for 15 seconds, and my hard drive isn't flashing at ALL during this stage. Afterwards, I get a blank screen. So I wait for a few minutes and see if anything happens, and still that black screen is still there. Afterwards, I decide to shut down the computer manually by pressing the power button for about 5 seconds.

Can anyone help me on this issue? I have no clue what happened because I was just minding my own business while surfing the web when all of a sudden my system crashes and now it won't boot!!

---

### Post by Diffusr on 2009-11-15
I had a very similar thing happen. Last night.
I had just started watching a youtube vid on Karmic/firefox when the headphones, at full volume started making repetitive screeches and bleeps and the screen had froze - as though I had been hacked by some e.t. in a ufo above the house.
The only way to get out of it was to hit the power button for a hard reset.
The laptop now will not boot. It sometimes gets to the login screen and then freezes solid.
If I try again right after i get a blank screen. If I wait a while I get a partial boot.
What is this?

---

### Post by ankman on 2009-11-15
> **XProflmfao said:**
> My laptop won't load now!!! Okay, so it all happened last night. I was using Mozilla Firefox and surfing the web as usual, when all of a sudden Firefox stops responding. Then, I try to close the program by clicking alt-F2. It didn't close. So then I right clicked on the Firefox tab on the bottom taskbar. The menu popped-up, and I tried to click Close. Nothing responded, and now the menu was frozen on my screen too. And then I tried to restart the computer by pressing on the top taskbar. It wouldn't respond, and no that taskbar was frozen too!!! In the end, I had to shut my computer by closing the laptop lid. I know this means that I never really shut down the computer, but I just put it to sleep. I think that's what caused the whole messup.

But anyway, after waiting a few minutes, I try to open my computer again. Everything is normal, the system's booting up, but then the Ubuntu icon stays on my screen a little bit too long. Usually when I boot up Ubuntu, my hard drive is flashing a LOT once I get to the Ubuntu icon part, just before it goes into the log in menu. But then this Ubuntu icon stays there for 15 seconds, and my hard drive isn't flashing at ALL during this stage. Afterwards, I get a blank screen. So I wait for a few minutes and see if anything happens, and still that black screen is still there. Afterwards, I decide to shut down the computer manually by pressing the power button for about 5 seconds.

Can anyone help me on this issue? I have no clue what happened because I was just minding my own business while surfing the web when all of a sudden my system crashes and now it won't boot!!

See if you can press CTRL-ALT-F2 and get a shell. Log in as root. If this works do a 

less /var/log/messages

and scroll down to see if there is any hint what could had caused this.

---

### Post by marcdutonkin on 2009-11-15
To restart your laptop, these are these rules :

- first, go into the Grub2 menu and select recovery. In the case where the menu does not appear, you have to press ESC when the message "Grub loading" appears.

- then, if you cannot boot successfully, eg. the system blocks, you should apply a specific closing procedure (magic phrase) before trying to boot again, in french "Savoir Eteindre Intégralement Ubuntu Brusquement": 
  + Alt SysReq s to synchonize your hard disks
  + Alt SysReq e to close ubuntu processes
  + Alt SysReq i to kill all remaining ubuntu processes
  + Alt SysReq u to unmount hard disks
  + Alt SysReq b to restart

My own laptop doesn't always boot successfully, since Karmic sometimes tells me that there are EXT4_FS errors on my USB hard disk(bug???). With the previous rules applied, i have always recovered my session.

---

### Post by XProflmfao on 2009-11-15
> **marcdutonkin said:**
> To restart your laptop, these are these rules :

- first, go into the Grub2 menu and select recovery. In the case where the menu does not appear, you have to press ESC when the message "Grub loading" appears.

- then, if you cannot boot successfully, eg. the system blocks, you should apply a specific closing procedure (magic phrase) before trying to boot again, in french "Savoir Eteindre Intégralement Ubuntu Brusquement": 
  + Alt SysReq s to synchonize your hard disks
  + Alt SysReq e to close ubuntu processes
  + Alt SysReq i to kill all remaining ubuntu processes
  + Alt SysReq u to unmount hard disks
  + Alt SysReq b to restart

My own laptop doesn't always boot successfully, since Karmic sometimes tells me that there are EXT4_FS errors on my USB hard disk(bug???). With the previous rules applied, i have always recovered my session.

Hey, I tried doing your method but whenever I close ubuntu processes or kill all remaining ubuntu processes it gives me this:

[FONT="Courier New"]Gave up waiting for root device. Common problems:
- Boot Args (cat /proc/cmdline)
[INDENT]- Check rootdelay= (Did the system wait too long?)[/INDENT]
[INDENT]- Check root= (Did the system wait for the right device?)[/INDENT]
- Missing Modules (cat /proc/modules; ls /dev)
ALERT! dev/disk/by-uuid/c76c998cb-370c-4aa2-9249-822368fd30bb does not exist. Dropping to a shell![/FONT]

And also, after following all of your directions and restarting the computer, my system still comes to a standstill and the screen becomes blank after the ubuntu icon appears for 15 seconds. Is there something wrong with the system? Because everytime I try your method, that thing keeps popping up.

---

### Post by XProflmfao on 2009-11-16
> **XProflmfao said:**
> Hey, I tried doing your method but whenever I close ubuntu processes or kill all remaining ubuntu processes it gives me this:

[FONT=Courier New]Gave up waiting for root device. Common problems:
- Boot Args (cat /proc/cmdline)[INDENT]- Check rootdelay= (Did the system wait too long?)[/INDENT][INDENT]- Check root= (Did the system wait for the right device?)[/INDENT]- Missing Modules (cat /proc/modules; ls /dev)
ALERT! dev/disk/by-uuid/c76c998cb-370c-4aa2-9249-822368fd30bb does not exist. Dropping to a shell![/FONT]

And also, after following all of your directions and restarting the computer, my system still comes to a standstill and the screen becomes blank after the ubuntu icon appears for 15 seconds. Is there something wrong with the system? Because everytime I try your method, that thing keeps popping up.

Okay, so I just decided to do a clean install on my computer, since I really don't keep any of my important files on my computer (pictures are also on my camera, important documents and stuff for school in a usb flash drive) Thank you everyone for helping me through this bothersome annoyance that plagued my ubuntu pc.

---

