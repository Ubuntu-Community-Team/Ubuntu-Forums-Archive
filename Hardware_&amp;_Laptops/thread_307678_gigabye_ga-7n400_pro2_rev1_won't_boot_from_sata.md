---
title: "gigabye ga-7n400 pro2 rev1 won't boot from sata"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by coln_panic on 2006-11-26
okay, i know this isn't an ubuntu specific question, but since the hard drives i am trying to get to boot have ubuntu on them i hope it is okay to post this here.

my situation:  i had ubuntu installed on a pair of sata drives in a software raid 0 that i am migrating to a different motherboard.  possibly not the best plan to try, but i don't see any reason it shouldn't work with a little effort.  the trouble is that my motherboard won't boot from the sata drives no matter what i try for settings in bios.  

the motherboard is a gigabyte ga-7n400 pro2 revision 1, and all i can find through google is other people that can't boot from sata either.  one place suggested flashing the bios with the revision 2 bios and claimed they got it to work, but i get an error after it tries to load it.  i may install windows on an ide hard drive so i can use the gigabyte live update tool to give it another go.

if anybody has been able to boot a sata drive on this board, please advise how you did it.  right now i am booted to an external usb drive, with the raid 0 mounted and it is surprisingly fast, but i would like to boot right to the raid array.  as a last resort, i may just put in an ide drive and install to and just use the array as storage, but... again, not ideal.  

summary:  bios is updated (to version F11, the latest for rev1), sata bios doesn't show at all, won't boot from sata drive or detect the sata in grub to use as root.  after booting(to external usb drive) the sata drive array is accessible.  i know my way around bios settings, and by all means it should boot sata, but there are a lot of others found through google with the same problem, and no solutions that i could find that worked.

any suggestions are very welcome (or hardware donations if you're going to suggest a new motherboard...:)) thanks in advance,

jay

---

### Post by coln_panic on 2006-12-02
so i tried a few things to get it to work.  first i tried to load a bios for the revision 2 board, but it gave a "bios id check error" so it must have some preventative measures against that.  then i tried just using the slightly older (F10 and F9) bios, but they didn't work either.  

however, after trying them, i booted from the backup bios because i thought as long as it's not going to boot from sata i might as well be running the newest bios.  well, whatever was in the backup claimed it was release 'FA' i think, which follows the naming scheme of the revision 2 boards (FH, FI, FJ, and FK being the latest releases) but FA is not listed on gigabyte's website anywhere under revision 2 or revision 1!  this apparently did not matter, since it detected and booted my sata drives with no further problems.  

after finals are over i will investigate this mysterious 'FA' bios further, and if it is older than most of the F5-F9 i'll try to figure out which bios update caused sata to stop booting.  in the meantime, if you're interested in the FA release i could make it available, or just try booting from your backup bios and maybe it's there (i got my board used, no clue when/how it got on there).

jay

---

