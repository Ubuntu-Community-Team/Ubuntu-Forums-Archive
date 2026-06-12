---
title: "Xine dvd play problem"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by wxm505 on 2005-03-24
Hi I am new to Ubuntu. I  was using Fedora core for a while.
The Xine and totem worked well for playing dvd under Fedora.
But when I use Xine under Ubuntu to play dvd
It player about 15 seconds then pop up a error message : 
Error reading NAV packet.

Then I tired it with Totem. The player closed unexpectly.

error message pop up:

An error occured
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

I did installed the libdvdcss.
So I do not know how to solve it out
Any help???
Cheers

---

### Post by cory-79 on 2005-03-24
[QUOTE=wxm505]

Then I tired it with Totem. The player closed unexpectly.

error message pop up:

An error occured
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

I did installed the libdvdcss.
So I do not know how to solve it out
Any help???
Cheers[/QUOTE]

Try to open the totem.conf file in your /home/.gnome/ directory, there will be a line quoted, referring to libdvdcss2, unquote this line

Sorry for my english :P

---

### Post by wxm505 on 2005-03-24
Problem solved !!
hehe, cheers mate.   :D

---

### Post by wxm505 on 2005-03-24
Another stupid problem is about system tray icon.
I chose something by mistake . Then when I minimise gaim or skype
They did not go to the panel bar on the top ,
in opposite they went to panel bar at the bottom as the other windows
such as terminal. 
I have already set up the system tray plugin of gaim.
it still did not work.
I tried with another user .It worked well.
I thouhgt there must be some configure about the gnome about this.
But I do not know how to do it.
any help , cheers!!

---

### Post by jdodson on 2005-03-24
stop duplicating posts.  i have PM'ed you on this issue.  you have been warned.

---

### Post by ~zoey~ on 2005-03-25
I am also having problems playing a dvd.  I tried to install libdvdcss and I get the message from apt-get that it doesn't exist.

Could someone please give me the correct command to install it?

Thanks, zoey

---

### Post by wbeck85 on 2005-03-25
I have DVDs running in xine (Well, totem and Kaffiene technically) but the comptuer really chugs to render video at full screen and I get very choppy video, at full screen. (1680X1050 if thats importnat) Windoes never had this trouble, so i Know tis not a problem with my hardware capabilities. I have a Mobile Radeon 9700, which seems to run everything else fine (including Unreal 2004). I have turned on that DMA thing, but i do no think it is the drive's fault. I wonder if the comptuer is trying to render video using software. It would be nice if the video card would render it, i bet I would get better framerates. Any insight?

---

### Post by wxm505 on 2005-03-26
[QUOTE=jdodson]stop duplicating posts.  i have PM'ed you on this issue.  you have been warned.[/QUOTE]
I am sorry. I am new here. how to delete them??

---

