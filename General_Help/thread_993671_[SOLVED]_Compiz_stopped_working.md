---
title: "[SOLVED] Compiz stopped working"
date: 2008-11-26
forum: General Help
---

### Post by sondosia on 2008-11-26
I'm running Ubuntu 8.10 on an HP laptop. My friend and I needed to connect my laptop to a projector, and we were forced to mess with screen resolution and such. But afterwards we set it back to the right resolution for my laptop.

Now compiz doens't work - when I try to enable to "extra" visual effects under Appearance, it just says "Desktop effects could not be enabled".

The output of the command compiz is:

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

I don't know what that means; hopefully someone else does...

Compiz has always worked perfectly on my laptop, even for Intrepid. I have no idea what got so screwed up. Please help!

---

### Post by CholericKoala on 2008-11-26
I had this happen once.  I didn't know what to do either, so I completely removed the package and reinstalled it through synaptic.

---

### Post by eternalnewbee on 2008-11-26
Try: ```
compiz --replace
```

---

### Post by sondosia on 2008-11-26
> I had this happen once. I didn't know what to do either, so I completely removed the package and reinstalled it through synaptic.

That's actually what I tried, and after I restarted everything worked again. Thanks. =)

---

### Post by jacob21 on 2010-07-15
> **eternalnewbee said:**
> Try: ```
compiz --replace
```

Worked great.

---

### Post by Kent- on 2010-10-16
> **eternalnewbee said:**
> Try: ```
compiz --replace
```

This helped me solve my problem!

---

### Post by Cronach on 2011-04-12
Awesome, thank you.

---

### Post by levancharly on 2011-04-12
Worked like charm Thanks

---

