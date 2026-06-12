---
title: "[SOLVED] send a link from firefox to a bash script"
date: 2008-11-07
forum: General Help
---

### Post by lovinglinux on 2008-11-07
I have bash script that takes an ulr as variable do some stuff with it.

It works pretty fine when I run the following command on a terminal:

```
myscript http://www.foo.com
```

I need to know if it is possible and how to send the url to the script from Firefox?

---

### Post by lovinglinux on 2008-11-08
Nevermind. I figure it out myself, after a lot of searches, trials and errors, using the "send link" from the context menu.

This is what I did:

1 - Changed the default Mail Reader in [System >>> Preferences >>> Preferred Applications] to "Custom" and added the following command to it:

```
/home/me/bin/myscript %s
```

2 -  Added the following code to the bash script

```
URL=$(echo ''$1''| sed 's/mailto:?body=h/h/g' | sed 's/&subject=.*/ /g' | sed 's/%2F/\//g' | sed 's/%3A/:/g')
```

I will appreciate if someone could provide a better method, that do not cripple mailing capabilities.

---

