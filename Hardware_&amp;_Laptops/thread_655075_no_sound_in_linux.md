---
title: "no sound in linux"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by kristian_gjengedal on 2007-12-31
i don't get any sounds in linux i have enabled all the options in the volume mixer i have tried with both my x-fi extreme audio and the integrated sound card in my mother board. specs in sig

i found out that there are no drivers for the x-fi card, but i don't get the sound to work with my integrated card, any help welcome.

---

### Post by Yellow Pasque on 2007-12-31
The 64-bit version of Ubuntu has X-fi support IIRC. Are you running the amd64 or x86 version of gutsy? If you're unsure:
```
uname -a
```

---

### Post by kristian_gjengedal on 2008-01-01
i have amd64 version

---

### Post by kristian_gjengedal on 2008-01-01
bump.

i tried mandriva one 2008 before and the sound worked fine there but i would rather use ubuntu, anyone know a way to get the sound working?

---

### Post by mmb1 on 2008-01-01
Type  "alsamixer" in the terminal and post the output, please

---

### Post by kristian_gjengedal on 2008-01-01
here is the output:

---

### Post by kristian_gjengedal on 2008-01-01
bump

---

### Post by mmb1 on 2008-01-01
Sorry, that I wasn't available for a bit, but now I'm back.  It would appear that ubuntu recognizes your sound card, but not your chip, did your sound work properly before ubuntu?

---

### Post by kristian_gjengedal on 2008-01-01
it worked in mandriva one 2008 and works fine in xp and vista

---

### Post by mmb1 on 2008-01-01
And you've been unable to find any drivers, correct?

---

### Post by kristian_gjengedal on 2008-01-01
that is correct, at least not on the companies sites only xp and vista drivers.

---

### Post by kristian_gjengedal on 2008-01-01
found a beta 64 bit driver at their site [http://us.creative.com]("http://us.creative.com/support/downloads/download.asp?searchString=XFiDrv_Linux") but i couldn't install it.

---

### Post by mmb1 on 2008-01-02
Try searching through synaptic for drivers, or using the restricted driver tool.

---

### Post by kristian_gjengedal on 2008-01-02
found nothing in the restricted driver tools other then for my geforce 8800gts,

i decided to go back to using mandriva one 2008 for now.

---

### Post by Yellow Pasque on 2008-01-02
Before you switch (if you haven't already) the other option is try out OSSv4 (see my sig). It won't get the X-fi working, but it should at least get the onboard working.

---

### Post by kristian_gjengedal on 2008-01-06
i noticed the onboard sound didn't work on windows either (haven't used it before) and found out i had to update the bios, so i tried ubuntu again and this time i got the sound working at least with the onboard sound card.

---

