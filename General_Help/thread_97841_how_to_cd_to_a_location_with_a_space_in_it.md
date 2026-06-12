---
title: "how to cd to a location with a space in it?"
date: 2005-12-01
forum: General Help
---

### Post by Greeface on 2005-12-01
How do you navigate to a directory that has a space in it, because if you type "cd /a place" it will say that "a" is not a folder.

Thanks,
~Greeface

---

### Post by cgjones on 2005-12-01
Either use tab completion, or type the name in quotes.

---

### Post by invalid on 2005-12-01
You can put the directory in quotes "".
You can also use the \ escape character before the character.

Cheers
Cb

---

### Post by RAOF on 2005-12-01
You can either "escape" the space character with a backslash, like so:
```
cd /this\ directory\ has\ spaces\ in\ it
```
or just put quotes around it, like so:
```
cd "/this directory has spaces in it"
```

---

### Post by tman_ubuntu on 2005-12-01
[QUOTE=Greeface]How do you navigate to a directory that has a space in it, because if you type "cd /a place" it will say that "a" is not a folder.

Thanks,
~Greeface[/QUOTE]

You can use the escape character "\".  So for example you want to navigate to "/home/user_name/My Documents", it would be this:

```

cd /home/user_name/My\ Documents

```

the space right after the "\" character is viewed as part of the word.

---

