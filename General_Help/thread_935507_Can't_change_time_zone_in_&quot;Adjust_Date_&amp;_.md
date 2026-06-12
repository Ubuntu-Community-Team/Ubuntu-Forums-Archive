---
title: "Can't change time zone in &quot;Adjust Date &amp; Time&quot;"
date: 2008-10-01
forum: General Help
---

### Post by Charles.Strahan on 2008-10-01
Hello!  I'm having some trouble changing the time zone in Ubuntu.  I have the configuration set to manual and I when I select a time zone (on the world map), it gets reset when I click close.  This is my fourth day or so using Ubuntu, so I'm definitely a noob (be easy on me! :D).

Anywho, any advice would be great!  Is there any way to see a list of exceptions (GUI or non-GUI)?  There have been several times that something would not work as expected, and I'd look into it and find that a dependency wasn't installed, and yet I wouldn't get an error message.

I don't know if this is applicable, but here's some more info -
I saw a page somewhere that mentioned that you can use NTP - so I went about installing ntpdate, had some issues, then decided to uninstall it, and left ntpd installed.  Also, I noticed that ntp.ubuntu.com was not listed, as it supposedly should be. (I did all of this before I realized that "Adjust Date & Time" will atomically set this up).  Who knows how much I've jacked is up :).

Thanks guys!

EDIT:  "Synchronize now" is not working, either.  Perhaps I've dorked NTP?.. ntp.conf is empty, too...

---

### Post by kokkus on 2008-10-01
Turn on time synconizer and reboot.

---

### Post by Charles.Strahan on 2008-10-01
Update:  I looked at /etc/timezone, and it is in fact set to the correct timezone.  It looks like the clock on the gnome panel is just not showing correctly, nor updating the time when I click the resynch button.  Still no luck in figuring this out yet.

---

### Post by Charles.Strahan on 2008-10-01
> **kokkus said:**
> Turn on time synconizer and reboot.

Are you referring to the "Keep synchronized with internet servers" under "Configuration"?

---

### Post by Charles.Strahan on 2008-10-01
Thanks for the quick reply, but it's not working yet.  It's bizarre.  Not only does it show a different time zone than the one I have selected, but it also does not even synch the time to the time zone it thinks I'm in.

Is there anything that I should try reinstalling?

---

### Post by Charles.Strahan on 2008-10-01
Hmmm... Whenever I set the timezone to America/Shiprock, it get's reset back to America/Denver... But any other timezone will switch over correctly.

---

### Post by kokkus on 2008-10-01
> **Charles.Strahan said:**
> Are you referring to the "Keep synchronized with internet servers" under "Configuration"?
System > Administrator > Time and date.

If you change to syncornized clock, use your local ip and not a proxy server.

---

### Post by Charles.Strahan on 2008-10-01
Thanks!  I got it to work.  It turns out that ntpd only makes small corrections (I read that the threshold was something like 3600 seconds...).

I'm not sure if the resynch button ever worked, but what I really want is fixed.

Cheers!
-Charles

---

