---
title: "Unable to install Ubuntu with ATI driver"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by techpops on 2009-05-03
Just installed latest version of Ubuntu. Tried to do so a few years ago and failed miserably. Being on a new PC now i thought I'd try again. I got it installed, into ubuntu desktop, tried to enable the fancy effects and that failed. so I presumed I'd need a better graphics driver. Going into the device section a suitable ATI driver was presented to me. I installed it, rebooted as prompted and now Ubuntu wont start up. I get the loading logo then a black screen.

Tried various ways of getting past this like hitting escape on load and using the options there but nothing worked.

Mostly I'm depressed this failed so miserably again for me when I hear people talking so highly about Ubuntu.

I'm back on XP now but wondering would it worth another attempt. Anything I should do differently?

My specs: Athlon X2 4400, 4GB ram, ATI Radeon HD3850. ASROCK AM2NF3-VSTA motherboard. System runs Windows very well without issues.

---

### Post by alphacrucis2 on 2009-05-03
> **techpops said:**
> Just installed latest version of Ubuntu. Tried to do so a few years ago and failed miserably. Being on a new PC now i thought I'd try again. I got it installed, into ubuntu desktop, tried to enable the fancy effects and that failed. so I presumed I'd need a better graphics driver. Going into the device section a suitable ATI driver was presented to me. I installed it, rebooted as prompted and now Ubuntu wont start up. I get the loading logo then a black screen.

Tried various ways of getting past this like hitting escape on load and using the options there but nothing worked.

Mostly I'm depressed this failed so miserably again for me when I hear people talking so highly about Ubuntu.

I'm back on XP now but wondering would it worth another attempt. Anything I should do differently?

My specs: Athlon X2 4400, 4GB ram, ATI Radeon HD3850. ASROCK AM2NF3-VSTA motherboard. System runs Windows very well without issues.

Try selecting the recovery line on the grub boot menu. Once it boot it should display the recovery menu. Arrow down to the line that says root prompt & hit enter. Then type the following command:

```
aticonfig --initial -f
```

Worked for me anyway.

---

### Post by techpops on 2009-05-03
> **alphacrucis2 said:**
> Try selecting the recovery line on the grub boot menu. Once it boot it should display the recovery menu. Arrow down to the line that says root prompt & hit enter. Then type the following command:

```
aticonfig --initial -f
```Worked for me anyway.

Thanks, I'll give it another shot, try that and post back the results

---

### Post by techpops on 2009-05-03
Ok tried what you said and got back into Ubuntu with all effects enabled. Was very happy for a few minutes until everything slowed down to a crawl. I logged off and on and all was well again. 

Aside from that I get resets while starting up Ubuntu or the loading just stops. If i hit enter it either continues and everything is ok or doesn't continue and just resets. Most odd behaviour.

I think I can live with those things for now. At least I've got into Ubuntu and fired up Firefox, had a bit of a surf and can now say I've "used" linux and be all boasty about it hehe.

I'll work on the glitches later. Thanks again for the help.

---

