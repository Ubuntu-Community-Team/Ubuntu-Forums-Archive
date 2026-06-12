---
title: "Can't install adobe flash player 10"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by biggdawg on 2009-04-18
I'm new to linux but I've beenat this for a while now and I can't seem to get this to work. I hardly use this laptop because I can't get it set up. Can someone please explain how to install flash? I have downloaded the 64 bit version and extracted it and put it in the ~/mozilla/plugins directory and when I go to youtube for example, it says that I don't have flash installed. This is ridiculous.

---

### Post by Ericyzfr1 on 2009-04-18
If you go on a site that require the flash player you will get the option to install it automatically, no extraction required.

---

### Post by Puz on 2009-04-18
One of the easiest ways I've found is to got to Applications->Add/Remove
Then where it has Show: click on the drop down box and select "Third Party"
check the box for Adobe Flash Player 10.

---

### Post by acimmarusti on 2009-04-18
I strongly recommend that after fully updating you open up a terminal and type this:

```

sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread3/install-css.sh

```

That should give you, not only flash, but fonts, mp3 plugins and video codecs for several formats including DVDs. 

It's the easiest way to go

---

### Post by zvacet on 2009-04-19
I found [this]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install") for 64-bit users.

---

### Post by C Black on 2009-04-19
> **acimmarusti said:**
> I strongly recommend that after fully updating you open up a terminal and type this:

```

sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread3/install-css.sh

```

That should give you, not only flash, but fonts, mp3 plugins and video codecs for several formats including DVDs. 

It's the easiest way to go

thanks a lot for this, I just installed Ubuntu last night and this was very useful

---

### Post by k9michaels on 2009-04-19
when I type
```

 sudo apt-get install ubuntu-restricted-extras
```
I get

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

Then when I type

 ```
dpkg --configure -a
```

I get
```

dpkg: requested operation requires superuser privilege
```

please help:KS

---

### Post by Bucky Ball on 2009-04-19
```
**sudo** dpkg --configure -a
```

'sudo' gives you super-user privileges. 'Super-user do'.

---

### Post by oldos2er on 2009-04-19
> **Ericyzfr1 said:**
> If you go on a site that require the flash player you will get the option to install it automatically, no extraction required.

 This will only install the version of Flash in Ubuntu's repositories, not the 10.x 64-bit version.

 To the OP: Did you uninstall any previously installed versions of Flash?

---

### Post by k9michaels on 2009-04-19
.

---

### Post by k9michaels on 2009-04-19
now

```
sudo apt-get install ubuntu-restricted-extras
```

once I do that I get

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
kyle@kylelaptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

even when i enter 

```
apt-get -f install
```

i get

```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

please help agin
b

---

### Post by zvacet on 2009-04-19
Go to the synaptic and in search box type sun and you will find **sun-java6-jre package**.Mark it for reinstall and then accept licence agreement.That will install Java.

---

### Post by acimmarusti on 2009-04-19
If you have trouble with the command-line, then go to System > Administration > Synaptic Package Manager (it will prompt you for your super user password) and search for the package called "ubuntu-restricted-extras". Install it and then run the second line I instructed you to use in a terminal.

---

