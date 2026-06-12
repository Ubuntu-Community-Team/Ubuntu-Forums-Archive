---
title: "Very Slow ISO creation speeds"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by beefcurry on 2006-12-02
Have anyone noticed this except for me? using the nautilus to create iso's from DVD's are slow, extremely slow, almost 5x slower then on windows.

I ripped the same DVD using powerISO on windows in 8 minutes when it took over 40 on Ubuntu Edgy, i have dma enabled, or at least i think i do:

after sudo hdparm -d1 /dev/cdrom:

 setting using_dma to 1 (on)
 using_dma    =  1 (on)

If that bit where it says "on" is tricking me please do tell me. Playback of DVD's have no problem so i believe it is not due to the dma. but then i could be wrong.

I would want to try powerISO in Linux rarther then than the nautilus iso creator but unfortunately the PowerISO in Linux dosnt create images...i wonder why??? it converts, lists and extracts.. =.=);

If anyone know of some way to speed this process up please tell me :D thanks.

---

### Post by zgornel on 2006-12-02
Try the simplest way of creating an iso: *sudo dd if=/dev/cdrom of=/cd.iso bs=XXXX*. Varying bs will increase/decrease performance. I get 2MB/s for bs =1024, 4.3 MB/s with bs=4096 (bs specifies how many bytes are read/written at the same time).

---

### Post by beefcurry on 2006-12-03
and how would you find out the best byte size? or is it completely trial and error.

---

### Post by 8bit on 2006-12-03
If I burn a 4.4GB ISO and I'm not running many applications; only Firefox and  maybe xmms. It takes around 8 or 9 minutes to burn. This is in Dapper, using a Plextor IDE burner with dma enabled.

The speed of the burn can vary quite a bit depending on the number of active applications and their HD usage.

That's been my experience. Lately though for some reason, I can no longer burn at 16x but at 12x in Nautilus. If I choose 16x, I get a yard disc almost everytime. 

I'm pretty sure that in Linux, your burns will be slower than in Windows and the actual selected burn speed may or may not correctly affect your true burn speed. Either way, I can live with it over spyware ,viruses and over-priced CSS anyday!

My 2 cents.

---

### Post by beefcurry on 2006-12-03
yea, thanks for the reply, but my problem lies in the absurdly slow image ripping seeds. Its become way faster to boot in windows, create image, boot back in linux then just create a image in linux. There must be a reason for this.. and if we find the reason we can solve it :D

---

### Post by zgornel on 2006-12-03
> **beefcurry said:**
> and how would you find out the best byte size? or is it completely trial and error.
Sort of... It dependens on the CD/DVD unit and DVD itself.

---

