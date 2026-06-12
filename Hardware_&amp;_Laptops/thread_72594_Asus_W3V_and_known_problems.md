---
title: "Asus W3V and known problems ?"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by Kaylord on 2005-10-06
Hi all! 
I'm pratically a newbie that is trying to understand something more on linux... :rolleyes: 
Well, I have a new laptop, an Asus W3470VLP, series W3V, and i wanna ask you about known problems with distros (and specifically with (K)Ubuntu) and relative solutions.
My problems, for now, and -sigh- very few solutions:
- audio won't work. The ICH6 chipset by Intel seems to be the cause of the problem, at least under alsa 1.0.8, distributed with Ubuntu Hoary. I tried to install alsa 1.0.9, but got a message telling that alsa is already built in in my kernel... I decided to give up in order to save my system and don't make a mess, even if i think a kernel recompilation at least will be necessary... (soo noob! :P).
- Asus ACPI problems: i solved - apparently - adding some mods on /usr/share/services/kded/kmilod.desktop, as described by this site: [http://de.wikibooks.org/wiki/Asus_W3N-Kompendium:_Kubuntu]("http://de.wikibooks.org/wiki/Asus_W3N-Kompendium:_Kubuntu")

Now... i'd like to get a solution for that audio problem, I "lurked" a lot but didn't find a solution (off course, probably because i'm noob! :D).
Also, i'd like to know if there are other relevant problems with Asus W3V series because i didn't try everything, and maybe if someone had the ability to use under Ubuntu the function keys and sleep/hibernate functions.
Thanks for your help!
Regards!
;-)

---

### Post by Kaylord on 2005-10-07
[QUOTE=Kaylord]Hi all! 
- audio won't work. The ICH6 chipset by Intel seems to be the cause of the problem, at least under alsa 1.0.8, distributed with Ubuntu Hoary. I tried to install alsa 1.0.9, but got a message telling that alsa is already built in in my kernel... I decided to give up in order to save my system and don't make a mess, even if i think a kernel recompilation at least will be necessary... (soo noob! :P).
[/QUOTE]

Auto answer: i finally got it. All i had to do was to download kernel sources, then configure them in the same way ubuntu inst did but deselecting ALSA built-in support. Then recompile... After that, I downloaded latest alsa driver & stuff from the alsa project site, just configuring in order to recognize hda_intel as audio card, and compile.
Last thing to do is just running alsaconf script and follow the instructions.
Since i'm very noob i don't know if this is a right and "clean" way to act... even if for me it's a big conquest! :D 

Another prob: no 3d acceleration for my Ati X600 card. I'll search for posts about the argument and eventually post if i solve this.
Anyway, any hint/suggestion/help will be appreciated! :D
The main prob according to me is still ACPI functions and functional keys not workin'.... but maybe someone could help in this.
Bye

EDIT: 3d acceleration is ok now. just install drivers that can be found on ATI website, and modify xorg.conf in order to have "fglrx". For contrast, i've noticed i got some probs with the dvd/cd-rw ... :(

EDIT #2 : Confirm that i cannot mount dvd/cd-rw optical device... anyone knows how to solve? I have really no idea since i'm a very newb in linux.... Is there a log or register to check in order to understand what is the incompatibility issue?
Thx! :)

---

