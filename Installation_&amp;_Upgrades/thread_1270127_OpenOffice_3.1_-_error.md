---
title: "OpenOffice 3.1 - error"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by mr.suchy on 2009-09-19
Hi,

This time I have another problem. I install OpenOffice 3.1 from .deb next I install  extension like menus. When I want run Writer or Calc I  can't. Every time I must get back lost document, when I recover document it's happen again :( I run system log but I don't know what search. Sorry for my language and grateful for any help.

Regards!:)

---

### Post by hal10000 on 2009-09-19
You may want to try openoffice from the ppa repositories.
First remove your current openoffice:
```

sudo apt-get remove openoffice.org

```
then put the repository into your sources.list:
```

sudo -s
echo 'deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main' |cat >>/etc/apt/sources.list
exit

```
Now import the gpg-key:
```
gpg --keyserver subkeys.pgp.net --recv 247D1CFF && gpg --export --armor 247D1CFF  | sudo apt-key add
```

Then:
```

sudo apt-get update
sudo apt-get install openoffice.org

```

If you start openoffice and you get a somehow "damaged" entry window and/or mising toolbar icons then (re-)install your openoffice.org-style-XXXX packages

If you still get the file-recovery window on startup, then you should delete the directory [COLOR="Red"]/home/your_name/.openoffice.org[/COLOR] directory:
```

rm -r /home/your_name/.openoffice.org

```
But take in mind that in this case you will loose all your user-settings you have made to openoffice.

Hope it helps.

---

### Post by Hagar Delest on 2009-09-19
Before trying the PPA version, I would try to [reset the OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by mr.suchy on 2009-09-20
> **hal10000 said:**
> 
```

rm -r /home/your_name/.openoffice.org

```

This fix my problem! Thanks very much :P

---

