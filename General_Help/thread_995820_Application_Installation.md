---
title: "Application Installation"
date: 2008-11-28
forum: General Help
---

### Post by Immel on 2008-11-28
Hello all,

I am new to Ubuntu and Linux in general. I have a simple question concerning package installations. After installing packaged applications from synaptic where do they go?

Where do I find and how do I launch an application that I just installed? Is there a command line I can use?

Any help would be appreciated,
Regards,
Immel

---

### Post by nothingspecial on 2008-11-28
They usually go in /usr/bin (but not always)

You can start all of them in your terminal. The command is usually (but not always the name of the app)

So ```
firefox
```

```
deluge
``` 

etc etc

---

### Post by drs305 on 2008-11-28
You can usually learn the command to start an app by running the following command:
```

which <appname>

```
Example:
*which gimp*
Result:
/usr/bin/gimp

You can find where an app's files are installed by running:
```

*whereis <appname>*

```

---

