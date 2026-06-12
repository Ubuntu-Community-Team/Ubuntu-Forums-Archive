---
title: "[SOLVED] Amarok problems"
date: 2008-10-30
forum: General Help
---

### Post by Despot Despondency on 2008-10-30
Hi,
     I'm trying to install amarok, but when I run 'sudo aptitude install amarok' I get the following message

```

WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  libxine1-x libxine1-misc-plugins kdebase-bin-kde3 libxine1-ffmpeg 
  amarok-xine libxine1-plugins libxine1-console libxine1 

```

I've never had this message before when I've install amarok. Why am I getting it now? Do I need to worry about it? Cheers in advance

---

### Post by gjoellee on 2008-10-30
nothing dangerous about it, just install those packages...

---

### Post by Bakon Jarser on 2008-10-30
> **Despot Despondency said:**
> Hi,
     I'm trying to install amarok, but when I run 'sudo aptitude install amarok' I get the following message



I've always used

sudo apt-get install amarok

Is there any difference between the two?

---

### Post by Despot Despondency on 2008-10-30
Cool, thanks gjoellee. Do you know why they have started coming up all of a sudden?

Bakon Jarser, my understanding is that the aptitude command keeps the dependency database updated so that dependencies will be removed when the relevant package is removed. However, I don't think the apt-get command does the same thing. That's what I heard anyway, but I could be wrong.

---

### Post by fooman on 2008-10-30
> **Bakon Jarser said:**
> I've always used

sudo apt-get install amarok

Is there any difference between the two?

have a look:

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Despot Despondency on 2008-10-30
OK, so I've installed amarok. Now when I start it up I get the following errors

```

Will not save configuration.
Configuration file "/home/tfurmston/.kde/share/config/amarokrc" not writable.
Configuration file "/home/tfurmston/.kde/share/config/kdeglobals" not writable.
Please contact your system administrator.

```

and

```

Amarok could not find any sound-engine plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

```

Does anyone know anything about these errors? I'm confused, amarok has always installed straight away before :(.

---

### Post by skullmunky on 2008-10-30
I love that "Please Contact Your System Administrator" message.  I guess that would be Despot Despondency, wouldn't it ... ?  :)

I've never had that problem before, but check the files it's complaining about and make sure their permissions are ok - verify that your home directory is in fact /home/tfurmston/, and that the .kde folder and everything in it is owned by tfurmston.

---

### Post by Despot Despondency on 2008-10-31
Indeed I am the system administrator. changed the permissions to the relevant folders and amarok actually started which is progress. 

However, it then kept saying it could not talk to klauncher. I had a look around and found that if I ran kdeinit it should stop, which it did. 

Finally I have amarok running again. Still don't understand why I had so many issues this time when I never had any issues installing it before. Nevermind, fixed now.

---

