---
title: "Real quick question about soundblaster live 24-bit (ca-0106 chipset)"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by Antiparadigm on 2005-08-03
I just have a real quick question and maybe somebody will have a answer (Maybe even a laugh @ my expense  ;-) )

   I am working on a friends old HP Pavilion and have decided to replace win98 with Ubuntu (Which helped out a TON!).  I've had to toss in a new hard drive, and I've taken out the combination modem/soundcard and replaced it with a Soundblaster live 24-bit (Model: SB0410 Chipset: ca-0106)

   I have everything working good except for the soundcard.  The other night I installed alsa like the sticky post about broken sound says and it did not work.  I found that I used the emu10k1 chipset when I should have used ca-0106.

   So now, as I am sitting at work, I looked up the card on the alsa website (That's how I discovered I've installed the wrong drivers).  So as I'm reading up on how to install the card the instructions state in the section "Setting up modprobe and kmod support":

> [COLOR=Red]**Note to debian users:** You need to save this information into a file in the [FONT=Courier New]/etc/modutils/[/FONT] directory (Eg. [FONT=Courier New]/etc/modutils/alsa[/FONT]) and run *update-modules* [/COLOR]

My question is:
Since Ubuntu is a debian derivative, do we follow this along with or instead of the other instructions?

[Here is the link to the set of instructions.](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410,+P17&module=ca0106)

Any help is greatly appreciated!!

Thank you

---

### Post by sal on 2005-09-28
i just got this same card today and trying to get it to work as well. I hope we get responce on this soon.
so far all i was able to do was to get saound output but im really trying to get my mic working as some of my relations rely on a mic and skype.

if someone could help with this thanks.

---

