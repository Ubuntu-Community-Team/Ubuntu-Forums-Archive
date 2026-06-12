---
title: "Wine Doors - DirectX does not install"
date: 2008-09-10
forum: General Help
---

### Post by gmxgeek on 2008-09-10
I have been trying to install directx 9 through wine-doors.
It downloads fine, and extracts fine, but then hangs on "Executing Installer"

When run through the terminal, it outputs
```

$ wine-doors 
Started logging session
Error: Error changing process name.  Please file a bug report at 
                 http://www.wine-doors.org/trac/newticket. Include OS name and version.
Checking wine drive: /home/fieldsm/.wine/
Resolving dependencies for DirectX 
Executing queue
Installing Application: DirectX version 9
Warning: MD5 sum not found

```

Can anyone provide insight to the problem, or a workaround for installing dx9?

Thank you in advance.

---

### Post by wirelessmonkey on 2008-09-10
Wine does not support DirectX 9.

---

### Post by gmxgeek on 2008-09-11
> **wirelessmonkey said:**
> Wine does not support DirectX 9.

Then why is dx9 in wine-doors, and why did it install fine several times before?

---

### Post by wirelessmonkey on 2008-09-12
I apologize, somehow I missed the news... I'm not sure regarding your specific isssue, but here's a link that may be useful

[http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html)

---

