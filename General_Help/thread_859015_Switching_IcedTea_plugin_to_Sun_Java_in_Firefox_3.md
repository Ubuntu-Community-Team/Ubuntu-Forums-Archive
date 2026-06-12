---
title: "Switching IcedTea plugin to Sun Java in Firefox 3?"
date: 2008-07-14
forum: General Help
---

### Post by MightyMe on 2008-07-14
I need to exchange my JVM in Firefox 3 from IcedTea to Suns Java. I have both runtimes installed on my system (Hardy).

Can anyone help me how this is done the easiest way? 

Thanks.

---

### Post by NilsE on 2008-07-14
You should be able to just remove the 4 packages starting with icedtea in synaptic and let Sun take over. 

Make sure at least the bin, jre, and the plugin for java6 are installed then restart firefox.

---

### Post by MightyMe on 2008-07-15
Thanks. It worked nicely.

---

