---
title: "version upgrade 7.10 to 8.04 trouble, grub choices"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2009-02-02
I did a version upgrade from 7.10 to 8.04 and at restart it did not finish up well at all. It was left to run over the weekend and on restart I did some cleaning up and (not sure exactly now) I found that I could boot up successfully if I chose a lower number kernel in the grub menu. 

If I choose the top grub kernel offering I find the boot up splash progress bar just continued endlessly. This is now happening for the top two grub kernel choices. The successful grub choice is 2.6.22-15, more recent ones (two of them) dont work.

During the endless progress bar, if I use ctr alt F1 I see 
'Loading please wait'
then  typically
'[96.348251] ata.00: revalidation failed (errno=5)'
(the numbers increment, each new line, slowly, some exceptions stated)

during this slow line incrementing, if I use 'ctrl c' i see displayed:
initramfs
the incrementing lines then again slowly continue

Any suggestions please?

---

