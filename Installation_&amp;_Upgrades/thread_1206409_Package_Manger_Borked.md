---
title: "Package Manger Borked"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by pbeesley on 2009-07-07
for the love of god please help me :(

since install the ubuntuone-client I've had NOTHING but problems. The system crashed while installing and I now can't uninstall, reinstall or remove the offending item. When trying to run 'package manager' I get this error

```
E: The package ubuntuone-client needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

how helpful. :S

I get that same error when trying to reinstall the damn thing. sudo apt-get -f install fails with the same message and I'm going insane.........please help me :(

---

### Post by pbeesley on 2009-07-09
anyone :(

---

### Post by robert shearer on 2009-07-09
This may hold an answer....
[http://www.ubuntugeek.com/package-installation-error-and-solution.html](http://www.ubuntugeek.com/package-installation-error-and-solution.html)

---

### Post by prshah on 2009-07-09
> **pbeesley said:**
> 
```
E: The package ubuntuone-client needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```


[s]I'm guessing that this is because it cannot find the ubuntuone-client package in the repositories; how did you originally install it? If you used a .deb, use the following command to (re)install it```
sudo dpkg -i ubuntuone-client.deb
```

or try dumping the deb file in /var/cache/apt/archives/```
sudo cp -p ubuntuone-client.deb /var/cache/apt/archives/
``` and then using apt-get.[/s]

OK now I realise that you have to enable a custom PPA for the ubuntuone client, and then apt-get it. I assume this is the route you took. In that case, have you tried```
sudo apt-get install --reinstall ubuntuone-client
```?

---

