---
title: "voume control miscalibrated. Still have sound when &quot;muted&quot;"
date: 2008-11-06
forum: General Help
---

### Post by jimmy the saint on 2008-11-06
One common irritation for me has been the misalignment of the the volume controls with the actual output of my machines.  For example, in one of my laptops volume 0%-50% is silent, but 50%-100% adjusts very quickly, reducing the level of control I have.  In my tower, it is similarly screwy, but in a different, and far more irritating way.

The volume does not go low enough!!  When Ubuntu says the sound is muted, I still have audio.  It is merely turned down a lot.  Is there a way to calibrate the volume controls to actually match the sound output of my audio card?

Thanks
JTS

---

### Post by ajgreeny on 2008-11-06
Try adjusting the PCM level in your alsa-mixer or after double clicking the volume icon in the panel.  Each card seems to need to be set differently.  I have mine on 80% for a good sound; any more and it is distorted.

---

