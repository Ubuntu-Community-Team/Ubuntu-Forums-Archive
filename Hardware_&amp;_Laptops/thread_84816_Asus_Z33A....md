---
title: "Asus Z33A..."
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by jonzep on 2005-11-01
has anybody had any luck running breezy on the asus z33a?

---

### Post by m0biu5 on 2005-11-13
I tried the live CD and it seemed to do pretty well. I am going to try to upgrade over thanksgiving I think...

---

### Post by pgf on 2005-12-14
i've installed breezy 5.10 on ours.  tried debian sarge first, but of course it doesn't have a lot of newer features, esp. for laptops.

the only serious problem i'm having with breezy (which worked fine with sarge) is no sound.  the mixers look like they're working, cat'ing to /dev/dsp seems to take the right amount of time, things are unmuted, but, no sound.

if anyone has a winning combination of drivers (i didn't save the lsmod lists from the sarge install :-(  ) i'd love to see it.

hybernate worked once, (though wireless firmware wasn't reloaded) but it's hung on restart every time since.

the function keys mostly work.  the touchpad disabler does not.

it's a nice laptop.  looking forward to getting it working completely.

paul

---

### Post by pgf on 2005-12-14
okay, sleep mode now works.  if i can figure
out where to report this, i will.

in /usr/share/acpi-support/ASUSTeK Computer Inc..config , add
a case for:
[FONT="Courier New"]
 [INDENT]       "M5A"*)                       
[INDENT]                ACPI_SLEEP=true[/INDENT]
        ;;[/INDENT]
[/FONT]

and in /usr/share/acpi-support/device-funcs , change three instances of:                    [FONT="Courier New"]
[INDENT]      s/*$//[/INDENT]
[/FONT]
to:
[FONT="Courier New"]
[INDENT]     s/ *$//[/INDENT]
[/FONT]
(i.e., add a space character before the asterisk)

i also uncommented the "DOUBLE_CONSOLE_SWITCH=true"
line in /etc/default/acpi-support .

---

### Post by m0biu5 on 2005-12-20
Alright, so I upgraded to Breezy a few days ago finally. 

I had sound working on Hoary by compiling the latest alsa drivers. Now, the sound doesn't work; we should work on figuring that out. 

As for the sleep: I made the changes you posted about and the sleep button works, but I am not sure how to get it to resume. How do you use your acpi functions? Does your lid sleep your laptop?

---

### Post by pgf on 2005-12-20
> **m0biu5]
I had sound working on Hoary by compiling the latest alsa drivers. Now, the sound doesn't work said:**
> 
i'm thinking i might just wait for dapper, with the alsa 1.10 drivers, and hope that that helps.  it seems to have a lot of fixes for this codec.
[QUOTE=m0biu5]
As for the sleep: I made the changes you posted about and the sleep button works, but I am not sure how to get it to resume. How do you use your acpi functions? Does your lid sleep your laptop?

hmm.  ours resumes by hitting any key, or the power button.  i assume that doesn't work for you?
i don't _think_ i had to anything else, but i can double check.

(btw -- sorry about the delay.  i've enabled email notification now.)
paul

---

### Post by m0biu5 on 2005-12-21
Yeah, I've got the e-mail notifcations on now as well.

Double check on the sleep thing for me, I can't seem to get it to work. Do your power lights blink while its sleeping?

Also, how long does your battery last. Any tricks besides screen dimming for power saving?

---

### Post by pgf on 2005-12-21
okay -- i'll doublecheck.  yes, the lights blink while sleeping.  i wonder if there's a difference in how the machines are configured -- is there bios access on this thing?  mine was set up by the dealer (with debian sarge, which i've replaced) so never really had to deal with bios types of config.

i'm afraid i can't answer the battery question -- haven't used it that much on battery, but it's well over an hour.  and it lasts longer than that while sleeping, so i guess it's doing something.  :-)

---

### Post by pgf on 2005-12-21
the only other thing that i can think that i might have changed to affect sleep operation is that i might have installed fresher acpi code.  i currently have acpi 0.09-1, acpi-support 0.46ubuntu1,  and acpid 1.0.4-1ubuntu8.  i think all i added to sources.list in order to get up to this level was "universe".

paul

---

