---
title: "Grub on flash card?"
date: 2008-11-04
forum: General Help
---

### Post by Auraomega on 2008-11-04
I'm looking to partition my HDD and to install Ubuntu to one partition, and WinXP on the other. I'll mainly be using Ubuntu and I would like to boot straight into Ubuntu, and not the run through Grub. For times when I'd need recovery, and/or to load XP, I'll like to be able to boot Grub from a flash card. I'm just wondering if thats possible?

-Aura

---

### Post by caljohnsmith on 2008-11-04
Yes, you could boot Grub through your flash card, assuming your BIOS supports booting from USB devices. I think it might be simpler though if you just set the Grub menu timeout to maybe 3 seconds, and turn on "hiddenmenu" in the menu.lst so you won't see the Grub menu on start up unless you press ESC. Then if you set Ubuntu to be the default OS to boot, you'll always boot into Ubuntu on start up unless you press ESC. Would that maybe work for you?

---

### Post by Auraomega on 2008-11-04
Thanks for the reply.

I'd already done this in the past on my previous WinXP/Ubuntu machine, what I disliked though was the text coming up on the screen... only a little thing but it bugged me, the laptop I'm getting supports booting from SD, and I have a spare SD card thats never going to get used for anything else.

If there was any way I could disable the text on the screen, (the countdown + press 'ESC' to enter menu bit) then I'd stick to using Grub on the HDD, but otherwise I'll go ahead and do the SD setup.

Thanks.
-Aura

---

### Post by DGortze380 on 2008-11-04
> **Auraomega said:**
> Thanks for the reply.

I'd already done this in the past on my previous WinXP/Ubuntu machine, what I disliked though was the text coming up on the screen... only a little thing but it bugged me, the laptop I'm getting supports booting from SD, and I have a spare SD card thats never going to get used for anything else.

If there was any way I could disable the text on the screen, (the countdown + press 'ESC' to enter menu bit) then I'd stick to using Grub on the HDD, but otherwise I'll go ahead and do the SD setup.

Thanks.
-Aura

You need some kind of boot loader. You can't just go from from BIOS to Ubuntu. Maybe look into LILO instead of GRUB? Don't know if it offers some addition configurations, I know it can be set to .1 seconds instead of GRUBs 1 second minimum.

---

### Post by caljohnsmith on 2008-11-04
One way you could do it would be to set the "timeout" to 0 seconds so you don't see the Grub menu at all or any text saying "Press ESC to see Grub menu", and of course have the default Grub entry set to boot Ubuntu. Then you could install Grub to your flash card like you were thinking, and have that Grub offer you the choice to boot Windows (and Ubuntu if you want that too). 

Or another option would be to simply replace the "Press `ESC' to enter the menu..." text string in the Grub stage2 file with spaces so you don't see that text on start up; you could easily do that with a HEX editor. That way you wouldn't need to mess with Grub on your flash card, but it's up to you.

---

### Post by Auraomega on 2008-11-04
I definatly like the sound of using 0 second delay to boot straight into Ubuntu, and I'll probably made the SD card setup instead, for the simple fact it would be easier and less problematic (I say now, I'll probably take it back soon) than me and my hex editors... we sort of have a love/hate relationship.

As for LiLo, I've never actually used it but I read somewhere that Grub far surpasses LiLo in terms of configuration so I never bothered with it, I'll take a look around though and see if I can find any info on it, as its sort of a simple thing I want and may be covered.

-Aura

---

