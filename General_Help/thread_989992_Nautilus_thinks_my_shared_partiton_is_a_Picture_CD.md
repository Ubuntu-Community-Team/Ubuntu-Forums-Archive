---
title: "Nautilus thinks my shared partiton is a Picture CD..."
date: 2008-11-22
forum: General Help
---

### Post by marshall.robert on 2008-11-22
Hi,

Nautilus is annoying me.. it keeps showing that stupid bar at the top telling me my shared partition is a "Picture CD".

I uninstalled F-Spot to see if that stopped it, but it now tells me to use Brasero.

How do I stop this?

Thanks in advance

-Rob


EDIT: its just suddenly stopped doing it....

---

### Post by marshall.robert on 2009-01-07
OH GOD ITS DOING IT AGAIN! PLEASE MAKE IT STOP!

(ps sorry, i have had too much sugar today)

---

### Post by phisher1 on 2009-01-07
Do you have a directory named Pictures in the root of that drive?

---

### Post by marshall.robert on 2009-01-07
I think it did for a short while.. but it doesnt at the moment. it has a folder called pictures, maybe that is triggering it.

ideally i would like a way to disable this functionality all together.

---

### Post by phisher1 on 2009-01-07
Well, rename the directory temporarily.. may be a work around for now.. 

You can also try to open up Nautilus.. goto Edit => Preferences => Media => Photos => Do Nothing

---

### Post by marshall.robert on 2009-01-07
renaming doesnt give an immediate fix.

and since i dont have fspot installed the Photos section in the media tab is greyed out...

thanks for your help so far :)

---

### Post by phisher1 on 2009-01-07
I don't have Fspot installed either and my media tab is not greyed out..

---

### Post by marshall.robert on 2009-01-07
> **phisher1 said:**
> I don't have Fspot installed either and my media tab is not greyed out..

> **marshall.robert said:**
> the Photos section in the media tab is greyed out...

and i have restarted nautilus using ```
killall nautilus
``` and its still being annoying...

i even set the gconf key of /apps/nautilus/preferences/media_autorun_x_content_ignore to "x-content/*" and nothing happened...

---

### Post by marshall.robert on 2009-01-08
I have restarted the computer and it's still doing it D:

---

