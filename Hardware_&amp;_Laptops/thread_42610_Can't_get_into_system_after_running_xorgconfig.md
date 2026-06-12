---
title: "Can't get into system after running xorgconfig"
date: 2005-06-18
forum: Hardware &amp; Laptops
---

### Post by alaithea on 2005-06-18
Hi,

I've been very happily using Hoary for the past couple of weeks. It's been my first real experience with Linux, except for a short period with Mandrake (which I thought was great until I saw Ubuntu).

I just now have had the privilege of really breaking my system for the first time.  :? I ran xorgconfig because I was having some screen refresh issues, and the screen resolution adjustment in Gnome wasn't giving me an option to put my LCD refresh higher than 60Hz, when it's supposed to allow 75. I went exactly by the specs in my monitor's manual when I ran xorgconfig, but part way through reboot it just says it can't start the X server, and asks me if I want to see the full output, yes or no. Problem is, my keyboard is dead, too. I have no way of getting past that screen.

The good news is that I backed up my xorg.conf file before I did this. I just don't know what to do to get in there and put the old one back in. Can anybody help? Thanks.

---

### Post by luca_linux on 2005-06-18
Yeah, don't worry. It's really simple. You haven't broken anything.
Just copy the old xorg.conf into /etc/X11 with root permission.

---

### Post by alaithea on 2005-06-18
Thanks for the reply. But how do I get to a command line? My system was configured to go straight to the graphical (GRUB?) login, which I now can't get to.

After the system throws me this error screen partway through bootup, I'm unable to do anything.

---

### Post by kb00heda on 2005-06-18
Is it possible to reboot and have GRUB launch the failsafe mode? (Press "ESC" in the beginning of the reboot and change the boot alternative.) 

If so, you should, eventually, arrive at a non-graphical login prompt. This would, despite the absence of happily hugging people, be great. It means you can login as root, using your ordinary UN and PW, and copy the old configuration file back, right from the terminal.

Let us know if it works! (The whole idea is to avoid starting X, and hopefully be able to repair the damage.)

---

### Post by alaithea on 2005-06-18
[QUOTE=kb00heda](Press "ESC" in the beginning of the reboot and change the boot alternative.)[/QUOTE]
It worked! I booted into recovery mode, and all is well now. Thanks so much.

---

### Post by kb00heda on 2005-06-18
Oh, it should have been "Recovery", and not "Failsafe". Anyway, glad it worked out! :)

---

