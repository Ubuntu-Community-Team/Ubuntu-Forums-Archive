---
title: "Asus Eee/Gutsy - fan issues"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by tristan on 2007-12-04
Picked myself up one of these little babies a few days ago. The default Xandros install lasted about 20 minutes before I wiped it and put my favourite OS on, thanks to the great info on these forums for making this so painless.

So anyway the setup is now nearly perfect, except for the cooling fan. Basically the laptop does get pretty warm, and the fan kicks in after 5-10 minutes. It's not terribly noisy but it's definitely noticeable at night, and I think it hammers the battery too. The problem is that the fan never switches off again, even if I cool the Eee down by placing it on a gel pack from the fridge. If I suspend it, the fan stops and does not come back on until the Eee heats up again after waking up (doesn't come on at all if I keep the Eee on the gel pack after waking).

I never had the Xandros on long enough to work out if this problem occurred there too, so I can't tell if the problem is with the hardware or the software.

Anyone else experience this or have any ideas?

By the way, this really is an incredible little computer and I've had crowds of people oohing and aaahing at it at my work, astonished that it was so cheap! I'm sitting on the couch wirelessly surfing with it- nerd heaven!

---

### Post by mellowd on 2007-12-04
I want one of these but worried about the 7" screen. Is it usable?

---

### Post by tristan on 2007-12-04
The screen is just fine for me. It's very crisp, has a good viewing angle, and is certainly big enough for surfing (hit F11 to maximise Firefox viewing), writing etc. YMMV if you have poor eyesight.

---

### Post by mellowd on 2007-12-04
It's currently number 1 on the list of things I want. *waits for his tax rebate*

---

### Post by Bezdomny on 2007-12-05
Tristan, have you tried building the acpi components available from the [**ASUS**]("http://support.asus.com/download/Download.aspx?SLanguage=en-us") site?  Maybe that would help? I have ubuntu running but removed compiz and fallen back to metacity due to the overhead and also cut out the unnecessary services to keep the processor load down, this helps keep it running cooler but it does seem to average around 52-57 degrees during normal use.  Can't say I've noticed the fan much.  I'll have a go at compiling the asus sources this weekend and will leave feedback then.


Steve.

[eeebuntu]("http://www.eeebuntu.org")

---

### Post by pathiks on 2007-12-05
hey does Asus offer a xandros download if u want to install it again? or do u get a install cd with it?

---

### Post by Bezdomny on 2007-12-05
> **pathiks said:**
> hey does Asus offer a xandros download if u want to install it again? or do u get a install cd with it?

The eee comes with a restore DVD that resets to factory presets and reinstalls all of the default software including xandros.

---

### Post by tristan on 2007-12-05
Hi Steve, thanks for the on-topic reply :). I searched around on eeeforums and apparently the problem is hardware/bios related and can't be fixed in software.

I run my eeebuntu with xfce and minimal services, and it takes about 10 minutes to get over 55C and for the fan to start. If I physically stop the fan from spinning then the cpu  temperatures goes up to 58-59C, but the rest of teh case gets very hot. I think I'll learn to live with it until a bios update is released which allows the user to specify a temp at which the fan kicks in.



> **Bezdomny said:**
> Tristan, have you tried building the acpi components available from the [**ASUS**]("http://support.asus.com/download/Download.aspx?SLanguage=en-us") site?  Maybe that would help? I have ubuntu running but removed compiz and fallen back to metacity due to the overhead and also cut out the unnecessary services to keep the processor load down, this helps keep it running cooler but it does seem to average around 52-57 degrees during normal use.  Can't say I've noticed the fan much.  I'll have a go at compiling the asus sources this weekend and will leave feedback then.


Steve.

[eeebuntu]("http://www.eeebuntu.org")

---

