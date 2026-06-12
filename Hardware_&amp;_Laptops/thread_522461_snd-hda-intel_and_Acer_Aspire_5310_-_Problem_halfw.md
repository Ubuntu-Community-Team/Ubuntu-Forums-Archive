---
title: "snd-hda-intel and Acer Aspire 5310 - Problem halfway solved"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by Pixman on 2007-08-10
Hello folks,

I already found similar threads to laptops, using the hda-intel module.
The problem resolved up to the point, where I found out, that I could activate my sound card (actually, it was activated but didn't put out any sound... but the card was detected, driver loaded etc.) by putting acpi =off into my grub boot line.

But after I rebooted, I recognized a slight change: The Wireless Lan didn't work anymore and sveral functions like my audio-volume button, too.

Ok, it's of course understandable, that the button doesn't work anymore when putting out acpi.
But why the wireless card?
I am at the moment bound to the options:
a) Having sound but no internet access and several missing functions
b) Having everything but sound.

Anyone knows how to merge these two somehow?

Thanks a lot,
Michael

---

### Post by moore.bryan on 2007-08-10
*acpi=off may not let your card function because it needs acpi... i don't mean to insult your intelligence in any way, but did you check to see if the sound was just muted before?*

---

### Post by Pixman on 2007-08-11
Haha, it's ok to ask that question. :)

It wasn't muted, I've checked that before and knew, that this could be the problem before.

I've read about every thread and tried nearly everything there was listed.
I'm clueless about this.

---

### Post by moore.bryan on 2007-08-11
*okay... try taking acpi=off out of your kernel line and when ubuntu starts, type ```
alsamixergui
``` in the cli; is everything unmuted?*

---

### Post by Pixman on 2007-08-13
I did tell you, that my sounds works when ACPI is off?
But everything else  will not work.

I found out, that the driver lacks support for Realtek ID 268 (of which type my card is, actually).

It should be barely included in the current version of alsa x.x.14, but I guess it still doesn't work completely.

Everything could be so wonderful if this fault wasn't... anyone knows, if somebody is onto this? There are some patches for alsa in the bug tracking system, but nothing works, even after recompiling it.

Kind of sad, the implementation of the card should be very simple.
[B]
And I don't want to repeat myself, EVERYTHING IS COMPLETELY UNMUTED![/B]
It's a driver problem, that will hopefully be finally fixed in the next Ubuntu release. It's one of those little glitches, that don't do it.. if I was into sound-programming, I'd do it myself, but my coding skills are limited to other things.

So, anyone found a solution 'bout this? Or some place where I can write to, to ask someone to write a driver for this?

Thanks a lot for your help.

---

### Post by Pixman on 2007-08-13
I just wanted to say, that I'm coming near to the solution!

I just recompiled alsa-driver from the HG repository and now I got a lot of new controls in my audio mixer.

Seems like every port is indicated.

But I still get no sound. Loading the snd-hda-intel module with acer, 3stack and auto didn't do it for me. Too bad. :(

Any idea?


I can feel it, support for ALC268 is soon to be implemented in ALSA OR IS already.. but I don't get it to run.

The mixers not muted, checked twice. ;) ALSA nor OSS.

---

### Post by Pixman on 2007-08-16
I've got a solution.

I finally recompiled from the ALSA mercurial repository and compiled the snd-hda-intel driver.
Well, what can I say, it works now.

It chooses 3stack as the model, dmesg tells me.

I needed one option in /etc/modprobe.d/alsa-base:
options snd-hda-intel  model=auto

BUT I think it works without it, since the driver usually does model=auto as standard.

Good luck... and try the new 2.6.22 kernel if it still won't work.

I'm happy to say, that now everything works perfectly on my notebook.

---

### Post by moore.bryan on 2007-08-16
[I]glad to hear you got it working, pixman... 

happy ubuntu-ing.[/I]

---

### Post by dominik_ap on 2008-01-21
> **Pixman said:**
> I've got a solution.

I finally recompiled from the ALSA mercurial repository and compiled the snd-hda-intel driver.
Well, what can I say, it works now.

It chooses 3stack as the model, dmesg tells me.

I needed one option in /etc/modprobe.d/alsa-base:
options snd-hda-intel  model=auto

BUT I think it works without it, since the driver usually does model=auto as standard.

Good luck... and try the new 2.6.22 kernel if it still won't work.

I'm happy to say, that now everything works perfectly on my notebook.

Hey can i ask about the guide how to recompile from the ALSA mercurial repository and then compile the snd-hda-intel driver?

Can somebody write me some hints in console what to write? Thank you really

Dominik F.

---

### Post by dominik_ap on 2008-02-10
Hm my sound is working when i start system with acpi=off but i still cant use the "buttons" for the sound

like: FN + F8, FN+home,pgup,pgdn,end ---> all these keys should control somehow the sound system on my laptop Acer Aspire 5310, but it doesnt work.

Do you have any idea how to again turn on these keys?


Thanks

---

### Post by Pixman on 2008-02-10
Welcome to your personal computer hell.

I had the  very same as  you but now I'm more than happy with my low-cost acer. The machine is very cost-effective.

When I used Breezy, the problem came up on me too.


The only thing that helped me , was to recompile the ALSA from the  current development sources (mercurial).
Google for mercurial alsa  recomile etc.
And maybe the name of your sound chip  (ALCxxx or something).

After recompilaton and reboot, my audio (and the rest went very well).

The only thign I had to had was an entry in some famous   file   (it's   named in this thread) and ad  to set the sound driver option to  "acer".

Wemt  perfectly by then!

Google, read this forum ( I wrote a lot about it) or   get one of the newer disribtions/releases of Ubuntu.
The problm never reappeared when I upgraded to gutsy... even the onboard wireless chip works now natively.


Kudos  to the developpers :)

Good luck.

---

