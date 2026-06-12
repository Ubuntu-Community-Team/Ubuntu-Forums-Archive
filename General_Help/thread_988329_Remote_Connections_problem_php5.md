---
title: "Remote Connections problem php5"
date: 2008-11-20
forum: General Help
---

### Post by dxlwebs on 2008-11-20
hey all im trying to get the joomlaworks FPSS to work on my site but i get this error

```

Warning: include() [function.include]: URL file-access is disabled in the server configuration in /includes/init.php(336) : eval()'d code on line 246

Warning: include(http://www.000000000.com/forum/modules/mod_fpslideshow.php) [function.include]: failed to open stream: no suitable wrapper could be found in /includes/init.php(336) : eval()'d code on line 246

Warning: include() [function.include]: Failed opening 'http://www.00000000.com/forum/modules/mod_fpslideshow.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /includes/init.php(336) : eval()'d code on line 246
```

i believe its because i can't have external connections through php5 i think but im not sure does anyone know what i can do to fix this error
thanks for helping

---

### Post by JDiss on 2008-11-20
> **dxlwebs said:**
> 
i believe its because i can't have external connections through php5 i think but im not sure does anyone know what i can do to fix this error
thanks for helping

Sounds about right.  Try this link and see if it helps;

[http://www.mattiasgeniar.be/php/url-file-access-is-disabled-in-the-server-configuration/](http://www.mattiasgeniar.be/php/url-file-access-is-disabled-in-the-server-configuration/)

---

### Post by dxlwebs on 2008-11-21
Hey i tried that but no luck does anyone know where in the php setup or in the server logs i can enable this and how i would go about doing it?

---

### Post by dxlwebs on 2008-11-22
does anyone have any ideas?

---

### Post by dxlwebs on 2008-11-24
really please  does no one know how to open the connections

---

