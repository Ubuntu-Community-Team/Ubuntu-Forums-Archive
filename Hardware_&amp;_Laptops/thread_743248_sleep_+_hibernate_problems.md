---
title: "sleep + hibernate problems"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by fela on 2008-04-02
hi
when i try hibernating or suspending my computer (compaq evo D500 small form factor 1.8ghz P4), it works, except when i wake it up/restore from disk, the mouse doesn't work (if i restart X it doesn't detect my graphics card), and i can't type into the tty(s), so basically hard reset is required. does anyone else have my problem? :confused:

it's not a big deal, i would just like to be able to sleep my computer. Btw, i run Ubuntu 7.10 gutsy with latest updates (as of 18:26 GMT+1 2/april 2008 ) using linux-2.6.22-14-386, if any of that helps.

---

### Post by fela on 2008-04-02
has no one heard of this problem before? is it a software bug? or is it my hardware?

---

### Post by JustAboutRealJAR on 2008-04-02
I've experienced this bug before... however it doesn't happen anymore and I don't know what I did to change it

---

### Post by noahsark1126 on 2008-04-02
Do you have an ATI or nvidia card?  If you're using ATI with fglrx, you won't get it to work, period.  It's a bug with Gutsy, though it seems to work nicely in Hardy Beta.  If you've got nvidia, I would play around with some of the settings in /etc/default/acpi-support (back it up first).  I'm not sure which ones you should try, but you might have some luck, since it sounds like suspend/hibernate almost works.

---

### Post by fela on 2008-04-03
ok I have an nvidia so i'll try having a look in that file (and yes, it goes without saying that i would backup first ;))

---

### Post by fela on 2008-04-03
i changed ACPI_SLEEP_MODE=mem to ACPI_SLEEP_MODE=standby in /etc/default/acpi-support, but that only made it so when i woke the machine up again, it automatically restarted X and gave me the error of 'low graphics mode' etc. (luckily it wasn't permanent)

is there anything else i might change in that file to fix my problem? :)

---

### Post by noahsark1126 on 2008-04-03
I'm not really sure.  As I understand it, suspend/hibernate in ubuntu is basically a crapshoot.  It either works, or it doesn't.  My ATI card never evn came close to working under Gutsy, but now under Hardy Beta, it works like a charm.  My friend's got an nvidia laptop, and his suspend/hibernate under gutsy is completely broken.

Your best bet is probably to just make due for another 3 weeks and then Hardy will be stable.

---

### Post by Holy Cheater on 2008-04-16
I have the same problem. But only after 2nd supsend/hibernate.
So, the first time i supsend and wake up Ubuntu it works normally.
After the second time I supsend, computer shuts off, then wakes, whirres with fans, and shuts down again. And when I wake it up I have the same problem as **fela**: USB-devices don't work. X doesn't start. I can switch between tty's, but also can't type anything in it.


I have Asus P5B (Intel P965 chipset) motherboard, C2D E6300 processor and GF8800GT video card.
OS: Ubuntu 7.10 Gutsy.

---

### Post by fela on 2008-04-16
I upgraded to Hardy beta, and the suspend (sleep) now works. When i try _hibernating_ (ie. suspend to disk) it works until it shuts down, where, instead of keeping off like any well behaved computer will do, it just restarts back to the same state as i left it in, as if i had turned it back on myself. Weird.

---

### Post by movesandpepper on 2008-04-16
uhh, yeah I have that same problem except mine came out of nowhere. I upgraded to hardy 2.5 weeks ago but this started happening to me four or five days ago. wierd huh?

---

### Post by objbuilder on 2008-04-16
> **fela said:**
> I upgraded to Hardy beta, and the suspend (sleep) now works. When i try _hibernating_ (ie. suspend to disk) it works until it shuts down, where, instead of keeping off like any well behaved computer will do, it just restarts back to the same state as i left it in, as if i had turned it back on myself. Weird.

I've seen this behavior before.. it happens when a script I run from the init startup sequence is not killed before the computer begins to hibernate. Perhaps that will help.

---

### Post by fela on 2008-04-16
> **objbuilder said:**
> I've seen this behavior before.. it happens when a script I run from the init startup sequence is not killed before the computer begins to hibernate. Perhaps that will help.

What is that script and what does it do? Is it general, or is it your custom script? Is there away, no, what is the way to make it kill that process? (cause there's always a way with linux ;)) TIA

fela

---

