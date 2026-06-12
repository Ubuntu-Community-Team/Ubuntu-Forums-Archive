---
title: "Searching for a PDA to sync with evolution and have wifi plus bluetooth"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by André on 2006-01-08
Hi everybody,

i think the title says it all. Could you suggest a nice PDA which syncs with evolution and has wlan and bluetooth capabilities?

These are the things which are important to me. Your own experience (if you own such a PDA or something) would really (!) be appreciated.

Thanks in advance for any answers
André

---

### Post by Amon_Re on 2006-01-08
[QUOTE=André]Hi everybody,

i think the title says it all. Could you suggest a nice PDA which syncs with evolution and has wlan and bluetooth capabilities?

These are the things which are important to me. Your own experience (if you own such a PDA or something) would really (!) be appreciated.

Thanks in advance for any answers
André[/QUOTE]

I use an iPaq 1940 wich is synced with synce & multisync with evolution.
The syncing from the PDA to Evolution is flawless sofar, from evolution to the PDA however, has quirks (missing appointments sometimes)

Never tried syncing over wifi or bluetooth with linux, however, it should work, you would need to define a bluetooth serial port (a tty device) and use that instead of the ttyUSB0 device you get over usb.

---

### Post by André on 2006-01-08
Hi,

did you try the gnome-pilot stuff in evolution?

It is in -> edit -> synchroniationoptions (or something).

Greetings
André

---

### Post by Amon_Re on 2006-01-08
[QUOTE=André]Hi,

did you try the gnome-pilot stuff in evolution?

It is in -> edit -> synchroniationoptions (or something).

Greetings
André[/QUOTE]

Who? Me? Nope, i don't own a palm

---

### Post by André on 2006-01-09
Hi,

sorry, i am very new to PDAs.

I did not know that the gnome-pilot does only work with Palms.

Greetings
André

---

### Post by ajmoncrief on 2006-03-03
My Palm T|X (or TX) (bluetooth and 802.11b) works great in ubuntu.  Works best with Evolution though (once I set it up correctly of course).  Jpilot works well with it too, but sometimes jpilot has a problem recognizing the pda if I boot my computer with it not connected.  I am actually in the process now of trying to figure out how to sync it over a bluetooth connection with evolution but I dont anticipate it being too big of a problem bc I have gotten bluetooth configured with it nicely.

The only problem I had was with malsync, which worked correctly for me 75% of the time.  It would suffer from graphical corruption and annoying little errors sometimes (both on the TX's side).  Never could figure out what was going on with it although I never tried too hard.

Overall I am happy with the TX.  It used to turn on all by itself the first week or two I had it, which would drain my battery if I last was using a program that disabled the palms autooff feature.  However, I have not experienced that problem with it here recently (going on about a month).

---

### Post by André on 2006-03-03
Hi ajmoncrief,

thanks for answering both of my threads ;-)

Your information is great and i think it will be a T|X for as soon as i can afford it (it so much sucks when you have to pay for the repair of your car as a student when you wanted to spend the money on a PDA ;-)).

Thanks for your posts again which were very helpful.
André

---

### Post by EKa on 2006-03-04
\\:d/

---

### Post by ajmoncrief on 2006-03-06
No prob.  Glad I could help, once you do get it.  Here is an article that wraps up how to sync with evolution and gnome-pilot.  Taken from: [http://schweeb.wordpress.com/](http://schweeb.wordpress.com/)






Linux Palm Sync
November 22nd, 2005 by schweeb

I just bought a Palm T|X PDA. Pretty neat little toy. It has both Wi-Fi and Bluetooth radios, and a nice color screen. So far, I have been able to connect it via bluetooth to my cell phone (Sony Ericsson S710a) VERY easily, and use the internet through the phone, which was neat.

As my primary OS is linux, I decided to see how well synching worked. I plugged the USB cable into the Palm and the PC, checked my dmesg output, and saw that the hotplug recognized it, and assigned it dev nodes.Â However, it assigned it both /dev/ttyUSB0 and /dev/ttyUSB1, which is something I’ve not seen before…. To get it working, I had to go to the gnome-pilot control panel, set it up to see my USB palm at /dev/ttyUSB1 with a speed of 115200 (you may also have to tinker with the timeout). I told it I had never synched before, and gnome-pilot created a sync profile with the palm. Next, all I had to do was select which DB’s I wanted to sync, fire up evo, and do a sync… it synched my contacts and tasks with little difficulty, much to my surprise.

Overall, this was a pretty easy process, but still not quite easy enough for a newbie to do.

Hopefully, whenever Mozilla comes out with the Lightning client, I hope I will be able to sync to that rather than Evo, as I quite dislike Evo.

I still haven’t figured out bluetooth synching, but I can send files back and forth from Linux.

---

