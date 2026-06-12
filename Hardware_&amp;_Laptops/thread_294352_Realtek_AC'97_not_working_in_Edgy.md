---
title: "Realtek AC'97 not working in Edgy"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by Mithryn on 2006-11-06
Hi all,

i'm fairly new to the linux community, and have just reinstalled Ubuntu 6.1 over ubuntu 6.06 that i had installed on this laptop a month or so ago.  

my problem is that before i had upgraded, my sound worked fine, no problems at all.  But now that i have reinstalled, my sound hasn't worked, despite it being recognized when i lspci and check under the system > preferences > sound.

now, when i originally installed, i had to oem-configure, so i logged in as oem with my admin password, the sound worked then.  but as soon as i set up an actual user account, it no longer works.

any help would be greatly appreciated.
also remember, i'm a complete newbie so step by step would be a bonus.

---

### Post by ReaderRat on 2006-11-06
This may help -->
**[http://www.flaterco.com/kb/audio.html](http://www.flaterco.com/kb/audio.html)**
seems to be along that line.

---

### Post by Mithryn on 2006-11-06
checked out that link, but it seems that the sound already works.

I'm getting absolutely no sound at all.
i've checked alsamixer and have all the appropriate options turned up, but still to no avail.

i've checked on the sound config and tried to test the sound, and no sound is present when testing.

---

### Post by ReaderRat on 2006-11-06
I don't know what to say, other than, this seems to be a persistent problem with Edgy & upgrades. Hopefully someone will post the solution.

---

### Post by Mithryn on 2006-11-06
what i don't understand, is that before i had a profile, the sound worked when i was in logged into oem, including the drum roll when i booted up.  As soon as i made my profile, the sound stopped working.
Any ideas?

---

### Post by eegull on 2006-11-22
There is apparently a conflict between the Realtek AC97 driver and the ATI IXP modem driver.  I found discussions of similar issues way back in Fedora Core 4 and 3 over a year ago.  It turns out the fix was easy; uncomment the following line in /etc/modprobe.d/blacklist-modem:

blacklist snd-atiixp-modem

and reboot.  Now the sound works fine on my Toshiba Satellite A65.

My guess is that this file was changed between 6.06 and 6.10 -- anybody know?

---

### Post by oldskoolgamer on 2006-11-28
Well I have to say that I'm impressed, I was getting audio once every 3-4 reboots then it would quit again. I did this edit & now sound working every time. 8)

---

