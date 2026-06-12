---
title: "[SOLVED] No Refresh #'s"
date: 2008-10-10
forum: General Help
---

### Post by DougieFresh4U on 2008-10-10
After playing around and messing up my system, I finally got my 'Screen Resolution ' back. But now the Refresh is empty. When I click to open, nothing drops down and so all I see is '0'
I tried to set it manually earlier but I didn't see my screen/monitor listed:
'KDS - Model 700P' and Product # k-72b. I **"sudo displayconfig-gtk"** and try to edit that to **intel 865** driver but it keeps going back to the vesa driver. 
What am I doing wrong? (using Intrepid)

---

### Post by DougieFresh4U on 2008-10-10
Please, any one have any kind of solution?

---

### Post by Sam on 2008-10-10
Is your screen TFT or CRT ?

If it's TFT, don't worry about refresh rates...

---

### Post by DougieFresh4U on 2008-10-10
> **Sam said:**
> Is your screen TFT or CRT ?

If it's TFT, don't worry about refresh rates...

honestly, I am not sure
KDS 17" Flat panel

---

### Post by Sam on 2008-10-10
Ok, flat = TFT (LCD).

In this case, you cannot change the refresh rate. With a CRT monitor (the big ones), you can physically change the refresh rate but with a TFT it's different.

---

