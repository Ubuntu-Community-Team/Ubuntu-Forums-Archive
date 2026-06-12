---
title: "Missing effects at ubuntu 8.10"
date: 2008-11-07
forum: General Help
---

### Post by Dr_Muscle on 2008-11-07
Hello Guys!
I just had upgrade my Ubuntu 8.4 to 8.10,at Ubuntu 8.4 I had use ccsm that was able me to make an a burn effect that now missed on 8.10 and some more effects too.
I just want to ask:What is going on? Where the all effects that gone after upgrade?
:confused:
Thank you very much!

---

### Post by eternalnewbee on 2008-11-07
You might have to reinstall compiz. And check first if your Hardware Driver is enabled

---

### Post by Dr_Muscle on 2008-11-07
I did remove program and install again.Drivers are fine and active...:confused:

---

### Post by eternalnewbee on 2008-11-07
Press ALT-F2, and enter ```
compiz --replace
```
Just cut and paste the code.

---

### Post by ellalan on 2008-11-07
You may need to enable "Animations addon" effect to get additional effects.HTH.

---

### Post by brown705 on 2008-11-12
> **Dr_Muscle said:**
> Hello Guys!
I just had upgrade my Ubuntu 8.4 to 8.10,at Ubuntu 8.4 I had use ccsm that was able me to make an a burn effect that now missed on 8.10 and some more effects too.
I just want to ask:What is going on? Where the all effects that gone after upgrade?
:confused:
Thank you very much!

@ Dr_Muscle:

I was having this issue too, but I figured it out.  Right after "Animations" in ccsm there is one called "Animations Add-on" that must be enabled.  I had to enable "Animations Add-on", close ccsm, re-open ccsm, then I could choose the extra animations such as Burn when editing "Animations".

Michael

---

