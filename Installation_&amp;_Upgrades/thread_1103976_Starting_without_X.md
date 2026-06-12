---
title: "Starting without X"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by ralphmerridew on 2009-03-23
I think an upgrade fouled up my X configuration.  How do I boot into character mode so I can fix it?

(Grub's recovery mode has an option to start a root shell, but it requires the root password to do so.  AFAICT, if you followed Ubuntu's advice of "You don't need a root password, you just need sudo!", you are screwed.)

---

### Post by albandy on 2009-03-23
after booting the system press ctrl+alt+f2
then a text terminal will appear type your user login and password
then you can use sudo to modify your configuration, the sudo password is your user password.

if you prefer to work directly with root you can type
sudo su -
this will open a root session

---

### Post by ralphmerridew on 2009-03-23
If I boot normally into messed-up X, Ctrl-Alt-F2 does nothing.

If I boot into recovery mode, Alt-F2 switches to a blank screen.

---

### Post by albandy on 2009-03-23
reboot
enter the grub menu
the first entry will be selected
type e (means edit)
select the 2nd option (starts with kernel)
delete silent and splash at the end of the line and type single
press enter and then b (means boot)

---

### Post by ralphmerridew on 2009-03-23
Didn't work.  Still boots into X.

(Annoyingly, if I hit ctrl-alt-delete while still in grub, it goes to an ordinary text login prompt.  If I try to log in, I get logged out a few seconds later.  After a minute or so, it reboots.)

---

### Post by albandy on 2009-03-23
ok, I'll make a video of how to edit grub during boot process, it will help you

---

### Post by ralphmerridew on 2009-03-23
I was able to edit the GRUB prompt, remove "quiet" and "splash", add "single".  It still booted into X, though.

---

### Post by albandy on 2009-03-23
> **ralphmerridew said:**
> I was able to edit the GRUB prompt, remove "quiet" and "splash", add "single".  It still booted into X, though.

ensure that the line was changed, when finishing editing press enter, then edit again to ensure it's changed, finally press enter again and then selecting the modified line press b

---

### Post by ralphmerridew on 2009-03-23
If I hit tab while in edit mode, it doesn't list "single" as one of the accepted options.

---

### Post by albandy on 2009-03-23
yes, this means to start the computer in runlevel 1 where you're logged as root without password prompt

---

### Post by ralphmerridew on 2009-03-23
"single" doesn't work.  Maybe it was the command to use with LILO, but GRUB apparently doesn't recognize it.

---

### Post by albandy on 2009-03-23
with grub works, I've tested it now
maybe I'm not explainig it well, so tomonrow morning I will make some screenshots.

---

### Post by ralphmerridew on 2009-03-23
I hit e.  I get a menu.

----
root (hd 0,3)
kernel /boot/vmlinux-2.8.28-9-generic root=UUID=... ro quiet splash
initrd /boot/initrd.img-2.8.28-9-generic
quiet
----
(UUID of my HD omitted.  Note:  "quiet", not "silent".)

I delete "quiet splash" and replace it with single and hit ESC.
I hit "e" again to make sure the change took.  It did.
I hit "b" to continue booting.  It goes into X.

How do I find out what version of GRUB I'm using?  (Specifically, is it GRUB Legacy or GRUB 2?)  

Albandy, are your instructions for GRUB Legacy or GRUB 2.0?

---

### Post by ralphmerridew on 2009-03-23
bump

---

### Post by albandy on 2009-03-24
don't hit esc, you must use "enter or intro" key, but are you using ubuntu?

---

### Post by albandy on 2009-03-24
A video showing the process
[http://www.linuxlleida.com/video/single_mode.ogv](http://www.linuxlleida.com/video/single_mode.ogv)

---

### Post by ralphmerridew on 2009-03-24
Well, I went through all that, at the end I got the same "recovery menu" as you did (same as the one I got whenever I chose recovery mode from GRUB, whether I put "single" in or not), and when I chose "root" at the end, it asked me for the root password.  Obviously there's something different set up in my system.  Maybe they decided to change this in JJ.

(I don't even need a root prompt directly.  I could do fine if I could get an ordinary login prompt, so long as it didn't start X first.)

---

### Post by albandy on 2009-03-24
try forcing vga=791 mode
edit grub in the same way but instead of putting single put vga=791
this will load the system in 1024x768 x 16 bit

---

### Post by ralphmerridew on 2009-03-24
Well, it at least recognized the option (text messages were still shown at the higher resolution), but it still tried starting up X at the end.

---

### Post by albandy on 2009-03-24
but now you have console access typing ctrl+alt+f2 ?

---

### Post by ralphmerridew on 2009-03-24
I don't know.  What did eventually work was burning a CD and using that as a rescue disk.

---

