---
title: "Built-in Card-reader, SD Card, PDA?"
date: 2008-07-22
forum: General Help
---

### Post by moore.bryan on 2008-07-22
first, all the boring stuff:
i'm running ubuntu 8.04 (kernel 2.6.24-19-generic) with openbox (not gnome/kde) on a lenovo z61e thinkpad with a built-in card reader. i also have a dell axim x5 and an sd card.

now, i formatted the card in the thinkpad, was able to mount it, write to it, and use it as if it were another 1gb of space. today, i got the bright idea to try and use it on both my thinkpad AND the axim. big mistake. the axim complained it needed to format the card--no worries because i didn't have anything really important on there (no map of area 51, no documents detailing the real jfk assassin, etc.)--so i formatted it. mounted it on the thinkpad and, voila, nothing--which is what i expected. put some things on it, unmounted it, put it in the axim, file-browsed to the card, and... wtf? nothing; not a single one of the files i had already put on it.

so, i put it back into the thinkpad, remounted it, ls-ed the dir, and... wtf? nothing.

huh? i think my files may have drifted into neverneverland.

any ideas, my compatriots?

---

### Post by Potatoj316 on 2008-07-22
You did unmount it properly right?  You didnt just take it out, did you?

---

### Post by moore.bryan on 2008-07-22
correct, umounted properly. i even tried only pmounting/pumounting and no dice.

---

### Post by Potatoj316 on 2008-07-22
Do both of your computers use linux, or is one windows?  Also what did you format the card to? (filesystem wise)

---

### Post by moore.bryan on 2008-07-22
> Do both of your computers use linux, or is one windows?
lenovo z61e thinkpad: ubuntu 8.04
dell axim x5 is a pda running windows ce
> Also what did you format the card to? (filesystem wise)
fat32, but i tried fat16 as well.

---

### Post by Potatoj316 on 2008-07-22
did your pda format the card?  If not try that, but it sounds like you already did.  

Does the computer/pda that put the files on the card recognize them after you unmount then remount, or are they gone after an unmount?

---

### Post by moore.bryan on 2008-07-22
> did your pda format the card?  If not try that, but it sounds like you already did.
i've tried both ways; i.e. formatting the card via my laptop and formatting it via the pda.
> Does the computer/pda that put the files on the card recognize them after you unmount then remount, or are they gone after an unmount?
formatted via laptop: pmount sd, cp files, pumount sd, transfer sd to pda, no files, put sd back in laptop, pmount sd, files are there.
formatted via pda: copy files to sd, transfer sd to laptop, pmount sd, no files, put sd back in pda, explore files, no files.
huh?

---

### Post by Potatoj316 on 2008-07-22
It sounds like your PDA might be having trouble with the SD card because you dont see the files when you put them on with PDA.  Only the computer ever sees the files.

---

### Post by moore.bryan on 2008-07-22
i'll try this when i get a chance a report back; thanks!

---

