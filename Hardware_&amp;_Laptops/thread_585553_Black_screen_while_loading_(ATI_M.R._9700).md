---
title: "Black screen while loading (ATI M.R. 9700)"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by xipher-cdb on 2007-10-21
Hello. I have installed Ubuntu 7.10 on my Acer Aspire 1660, and I have a problem. Between the Grub screen and the username/password screen, the screen turns black by 5 mins. 

With the live cd I can see the boot screen and when the services where loading, so I think it can be fixed. 

Someone knows how?

And another thing: it takes soooo long loading (about 4:30~5 mins), is this normal (P4 2.8GHz-512MB DDR333 SDRAM)? Can I reduce this time?

Thanks and sorry for my english, I'm from Spain.

Greetings.

**[COLOR="Red"]EDIT:[/COLOR]** I forgot it, I have an ATI Mobility Radeon 9700 64 MB.

---

### Post by Meson on 2007-10-21
I am having the same problem with an ATI card.  I have been assuming it has something to do with the monitor detection, but I'm not positive.  I tried to add more explicit definitions to the xorg.conf, but it didn't help.

---

### Post by xipher-cdb on 2007-10-21
Uhm... I see. I think it would be much easier (this is my first linux). Well I will wait for news, I made all that I can (well... al that I found), and nothing works.

Thanks for answering and greetings.

---

### Post by teachop on 2007-10-21
My Acer w. ATI had this problem.  User dptxp in another thread posted a solution which worked for me to solve the super slow booting issue (but no pretty progress bar).  I don't know how to properly link the message so here it is pasted in...

QUOTE:

go to the terminal and type -

sudo gedit /boot/grub/menu.lst
...and enter your password

a big text file will open - you need to scroll right down to where it says ...


## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=79b1afc9-1898-45b2-a4e4-c53dd8e67db7 ro quiet splash


...or similar. just change 'splash' to 'nosplash' and save. reboot and celebrate!
cheers
roger

END QUOTE

---

### Post by xipher-cdb on 2007-10-24
Thanks teachop, it worked perfectly, now I can see all booting processes and it only takes 1 min, nor the 5 min that takes before.

:lolflag:

Bye bye.

---

### Post by misfitpierce on 2007-10-24
If you are referring to no splash at boot and it just hits black screen you can try this...

CTRL ALT F1 at black screen and it should start starting up and it will say no resume image..

Once inside do this in terminal
sudo gedit /etc/usplash.conf
Change the display to your native reso (ex. 1280by800 or 1440by900)

Then save and do this in terminal

sudo update-initramfs -u

Restart and should work.

---

### Post by Patriko_H on 2007-11-10
> **misfitpierce said:**
> If you are referring to no splash at boot and it just hits black screen you can try this...

CTRL ALT F1 at black screen and it should start starting up and it will say no resume image..

Once inside do this in terminal
sudo gedit /etc/usplash.conf
Change the display to your native reso (ex. 1280by800 or 1440by900)

Then save and do this in terminal

sudo update-initramfs -u

Restart and should work.
Thanks for posting this!  I have a laptop (Compaq Avo N620c) I just loaded "Gutsy" on. I've had a couple problems including the one described here; no splash during boot-up, long time loading.  Following these instructions I found the screen "Y" value wrong. Correcting it and doing the update-unintramfs thingy solved the problem

Thx,
Patrick \\:D/

---

### Post by Kev0r on 2007-11-11
Patrick, works like 5 charms out of 4 ;)

---

