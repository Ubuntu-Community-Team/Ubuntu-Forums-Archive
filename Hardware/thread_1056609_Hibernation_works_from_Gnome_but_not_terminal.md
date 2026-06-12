---
title: "Hibernation works from Gnome but not terminal"
date: 2009-01-31
forum: Hardware
---

### Post by tC_Crazy on 2009-01-31
Hey all. As the title says, my laptop (HP tx2500z) hibernates fine when using the power icon from Gnome in Intrepid. However, I use compiz, and that messes up hibernation. In order to fix that problem, I wrote a quick bash script:

```

#!/bin/bash
metacity --replace
sh /etc/acpi/hibernate.sh
```

This works fine, but when I return from hibernation, my keyboard and mouse don't work. Additionally, it doesn't prompt for a login screen, as it usually does. Does anyone know what exactly happens when you click "Hibernate" from Gnome?

---

### Post by Aearenda on 2009-01-31
I don't know exactly what happens in Gnome, but I think you should try calling pm-hibernate which uses the power management subsystem rather than the ACPI hibernate command.

---

