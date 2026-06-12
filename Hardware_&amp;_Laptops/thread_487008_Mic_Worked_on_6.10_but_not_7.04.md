---
title: "Mic Worked on 6.10 but not 7.04"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by SkypeGal on 2007-06-28
Hi!

I need Skype to call from Finland to family in the U.S., but ever since I upgraded from Ubuntu 6.10, the mic hasn't been working. Before with 6.10, I could use alsamixer to get the settings right but that no longer seems to be enough. 

My sound card is Audigy 2. There's an onboard sound card that's partly broken but haven't been able to disable through BIOS (which seems to lack the option to do that). I'm trying to use ALSA. 

I'm at my wit's end with this. I've been searching for a solution but cannot find one. 

Is there anyone willing to give pointers and/or walk me through the installation? Thank you for taking the time to read this.

---

### Post by isaksen on 2007-06-28
In the  gnome-volume-control as for as my mic it was per default set to "no volume", you might see if there is another sound card in "File->change devices".

:rolleyes:
If this does not work i would suggest that you try out another kernel.
Can you modprobe the whatever kernel module for the card.

---

