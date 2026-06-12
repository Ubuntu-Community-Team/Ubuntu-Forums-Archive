---
title: "[SOLVED] Lynx and HTML Entities"
date: 2008-10-11
forum: General Help
---

### Post by Jesdisciple on 2008-10-11
I have a web page that I'm testing in Lynx 2.8.6, and it's being a bit odd.  In two places, I have an HTML entity, a space, and several printable characters.  For both instances, Lynx shows neither the entity nor the first printable character (not sure about the space)...  Why?  Or is this a bug that I should submit somewhere?

Thanks!!

---

### Post by Sam on 2008-10-11
Maybe it's an encoding problem. Make sure that your file is saved in UTF-8 and that the following line is present in the <head> section:
[html]<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />[/html]

---

### Post by Jesdisciple on 2008-10-11
According to Quanta Plus, it's saved as UTF-8.  I had an iso-8859-1 meta before, but the new one didn't change anything.

---

### Post by Sam on 2008-10-11
Do you have an URL or some HTML markup ?

---

### Post by Jesdisciple on 2008-10-11
Sorry I didn't think of that on my own.  This page validates:```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>Titled Document</title>
    </head>
    <body>
        <div>
            &copy; 2008<br>
            &times; close
        </div>
    </body>
</html>
```Lynx shows this:```
    008
    lose
```

---

### Post by Sam on 2008-10-11
Ok, I was in the wrong direction.

It's lynx who don't use UTF-8 as display charset. To change this, create/edit ~/.lynxrc and add/edit the following line:
```
character_set=UNICODE (UTF-8)
```

---

### Post by Jesdisciple on 2008-10-11
Oh, thanks...  I didn't know HTML entities were encoding-specific.  :shrug:

---

### Post by Sam on 2008-10-11
> **Jesdisciple said:**
> Oh, thanks...  I didn't know HTML entities were encoding-specific.  *shrug*

No, the "character_set=UNICODE (UTF-8)" option tells lynx that your terminal is UTF-8 compliant. Otherwise it strips non valid characters from output.

---

