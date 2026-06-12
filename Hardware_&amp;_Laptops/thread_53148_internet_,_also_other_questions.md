---
title: "internet ?, also other questions"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by dlw on 2005-07-30
Using  kubuntu 4.05
Compaq Pesario 2105US

New to ubuntu.
konquorer or Firefox will connect to usps.com but nothing else.
Not Google, ubntu, many, many other websites.

What gives?

Also, k3g is not in the start menu.
It will open in a konsole.
But says it needs 'cdrdao' to function.
'apt-get install cdrdao' says there are no programs dependant on cdrdao.

Ideas?

More to come.

dlw

---

### Post by bored2k on 2005-07-30
[QUOTE=dlw]Using  kubuntu 4.05
Compaq Pesario 2105US

New to ubuntu.
konquorer or Firefox will connect to usps.com but nothing else.
Not Google, ubntu, many, many other websites.

What gives?

Also, k3g is not in the start menu.
It will open in a konsole.
But says it needs 'cdrdao' to function.
'apt-get install cdrdao' says there are no programs dependant on cdrdao.

Ideas?

More to come.

dlw[/QUOTE]
 1. Execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
2. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
* By K3g I understand K3B the burner *
3. sudo apt-get update
4. sudo apt-get install cdrdao k3b --force-yes -y

And ?

---

### Post by dlw on 2005-07-30
Thank you for such a quick responce.

 1. Execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
** The above does not exist. There is no 'Applications' menu. I know about konsole however.

2. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
** 'No such file or directory' as user or root.
** Can't get there with either Firefox or Konquorer.
** It did work in Firefox in a W98 box.
** Must have something to do with DSL connection.
** I'll see what I can figure out.

* By K3g I understand K3B the burner *
** I apologize for the typo error.

3. sudo apt-get update
** This worked.

4. sudo apt-get install cdrdao k3b --force-yes -y
Couldn't find 'cdrdao'. Tried 3 times. I assume its
because #2 didn't work.

More to come ?.
I have DSL and want to create a network
between a laptop and 2 pc's.
Laptop is named ubuntu and has unbuntu 4.05.
My main box is named MAIN and has W98.
The pc upstairs is named UP and also has W98.
Workgroup is WORKGROUP.
How do I do that?
I've been playing with 'samba' but I think
all I did was screw it up. Probably not the right
way anyway.

dlw

---

### Post by bored2k on 2005-07-30
You forgot to mention you were on [KDE](http://kde.org/)  ... most of us are using [GNOME](http://gnome.org/) . They are both very different Display Managers. 

1. Execute the commands in Terminal mode (Konsole)
2. sudo kwrite /etc/apt/sources.list
* Replace _everything_ with the following lines:
```

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
```
3. sudo apt-get update
4. sudo apt-get install cdrdao k3b --force-yes -y
* Optional system update *
5. sudo apt-get dist-upgrade --force-yes -y

---

