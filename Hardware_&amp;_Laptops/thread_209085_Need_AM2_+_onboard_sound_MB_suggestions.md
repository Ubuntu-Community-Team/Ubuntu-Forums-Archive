---
title: "Need AM2 + onboard sound MB suggestions"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by hotani on 2006-07-04
I'm building a system and looking for a motherboard. I have the [Asus  M2NPV-VM](http://www.newegg.com/Product/Product.asp?item=N82E16813131014) at the top right now, but can't find much mention of it here on the boards or elsewhere - except for [a discouraging thread about no sound](http://www.ubuntuforums.org/showthread.php?t=179322) when using this board - however, that thread is in the 'warty' section and I will be using the latest Dapper build.

I want to go with AM2 for the future-proofing and will need 5.1 sound. Sound is good. I like sound.

If not this board, is there another that will do the trick and work out-of-box with Dapper?

---

### Post by FenrisAbraxas on 2006-07-04
Does the mother board have an integradted 5.1 sound card? 

If it doesn't just check for compatibility of the sound card you are going to add.

Hope your sound works!

---

### Post by hotani on 2006-07-04
I'm only considering boards with integrated sound - 5.1 or 7.1 (although my speakers are 5.1). Trying to avoid having to get a separate card for sound.

---

### Post by ampes on 2006-07-04
I have built a new AM2 PC for my friend with this motherboard and would like to address some advices to you..I found the board has a RAM compatibility-I tried to stick 2GB(1GBx2) DDRII 667MHz and the BIOS sometimes stucked at POST screen.So brought it to the store and replace with other 533MHz Hynix chip..The onboard HD Audio is based on SoundMAX chip not Realtek,so check if ALSA supports it or not..

Check this [http://www.ubuntuforums.org/showthread.php?t=179322](http://www.ubuntuforums.org/showthread.php?t=179322)

---

### Post by hotani on 2006-07-05
Thanks for the info. I've read about RAM compatibility problems with the Asus AM2 boards, and there is a select few that will work with it. If I end up with this board I'll go with 2x1GB [Corsair RAM](http://www.newegg.com/product/product.asp?item=N82E16820145034) which seems to make it happy according to the user comments.

Now I'm looking at this [Gigabyte GA-M55](http://www.newegg.com/product/product.asp?item=N82E16813128010) board as well, but again can't figure out if the sound is going to cooperate or not. I'll see if I can find a good list of ALSA supported chips and post back if these boards *should* work, then when I get one I'll post back here on whether or not it actually does work.

EDIT: as far as I can tell, there is no mention of ANY of these on-board sound chips on the ALSA or OSS lists. Nor is there much feedback regarding their functionality in linux anywhere online. So I'll go with the old trial/error approach and see what happens. I ordered the Gigabyte board last night so hopefully I'll have some sound.

---

### Post by hotani on 2006-07-25
As mentioned above, I went with the Gigabyte board and it worked very well. The on-board sound works well in most cases, but is wonky at times. I'm wondering if it might be because i'm using 5.1 speakers with a 7.1 setup.

Anyway, anyone considering the Gigabyte M-55 AM2 board can consider it Ubuntu compatible. :)

---

