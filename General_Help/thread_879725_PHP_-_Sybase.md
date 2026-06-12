---
title: "PHP - Sybase"
date: 2008-08-04
forum: General Help
---

### Post by odie015 on 2008-08-04
I'm running Apache with PHP5 on Hardy and trying to connect to a Sybase DB running on a Unix host on the same network. 

Does anyone know how to setup the PHP - Sybase connection?

---

### Post by dodden on 2009-01-07
In your php.ini file, there is a sybase interfaces reference such as
```
sybase.interface_file = "/opt/sybase/interfaces"
```

You will need to know how to connect to Sybase, either through the sybase drivers, or with an addition of FreeTDS.

---

