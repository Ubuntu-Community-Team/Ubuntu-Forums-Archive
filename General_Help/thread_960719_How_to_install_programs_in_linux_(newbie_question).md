---
title: "How to install programs in linux (newbie question)"
date: 2008-10-27
forum: General Help
---

### Post by Oziyak on 2008-10-27
This probably sounds really bad but since moving to linux I've been confused some about how to install software.  I understand the whole package manager and how to get software from there... but what about installing from files downloaded from the web.

I've seen the following types:
RPM
DEB
TAR GZ
RUN

but not sure what they all mean and how to execute them as to install the software I want.

can someone please clarify for me on this?

really trying to make the move away from Microsoft.

thanks

---

### Post by Sam on 2008-10-27
.deb are Debian packages, the same format used in Ubuntu. If you cannot install something using Synaptic Package Manager, this is the best option.

.rpm, Red Hat package, another package format. To install them in Ubuntu you need to use the "alien" application.

.run, .bin, these are standalone binary executables

.tar.gz, an archive, will certainly contain source code that you'll need to compile.

---

### Post by Oziyak on 2008-10-27
thanks a lot man...
as far as compiling goes.... total newbie again...

is there a brief summary you can give me or point me to that could clear things up for me on that as well?

---

### Post by sdennie on 2008-10-27
If you are a self-professed "newbie", I would *highly* recommend sticking with either Applications->Add/Remove or System->Administration->Synaptic Package Manager.  Even for experienced users, installing something outside of those two places (or apt-get on the command line) can quickly break your system.

If you are coming from a Windows background, remember that adding/removing software is more tightly integrated with the system in Ubuntu.  Unless you absolutely must have the latest version of a piece of software, it's best to install what the above two places give you.  Almost anything you could want can be found using those two methods and it's trivial to install or uninstall.

---

### Post by Oziyak on 2008-10-27
well I'm definitely a newbie with linux/ubuntu... but am fairly intuitive when it comes to computing... and definitely not affraid to get my feet wet with ubuntu

I do appreciate your advice though...
there are some programs however that I'd like to try and/or require on ubuntu for myself and my parents that arn't in the add/remove menu.

---

### Post by Locke_99GS on 2008-10-27
Also, to get other softwares or newer versions installable from Synaptic, look for repositories from the company of the software you want to install.

For example, I stay up to date with the latest WINE by adding their repo to my sources list, and OOo from Core's PPA repo. The same goes for various other softwares.

---

### Post by 73ckn797 on 2008-10-27
If you download any Deb package you can right click and it will suggest opening with "GDebi Package Installer". It will take care of the rest.

---

### Post by sdennie on 2008-10-27
> **Oziyak said:**
> well I'm definitely a newbie with linux/ubuntu... but am fairly intuitive when it comes to computing... and definitely not affraid to get my feet wet with ubuntu

I do appreciate your advice though...
there are some programs however that I'd like to try and/or require on ubuntu for myself and my parents that arn't in the add/remove menu.

In that case, one piece of advice I'd give would be to learn how to use virtual machines and try all your experimentation there before taking it live to your system.  I use VirtualBox and always try potentially damaging things in an Ubuntu VM before trying them on my real machine.  If things go wrong, I just roll back the VM to a snapshot and I haven't done any damage to my system.

---

### Post by brandon88tube on 2008-10-27
Yeah, virtual machines are good use them on my windows desktop, but if you really could care less about your install then go at it.

---

### Post by Oziyak on 2008-10-27
thanks for all the tips guys.... much appreciated.... havn't had this much fun since learning DOS on my first 386 when I was 13 ;)

seems there is lots of helpful tools and people in ubuntu to keep your system running smooth :)

---

### Post by Yellow Pasque on 2008-10-27
> **Oziyak said:**
> well I'm definitely a newbie with linux/ubuntu... but am fairly intuitive when it comes to computing... and definitely not affraid to get my feet wet with ubuntu

I do appreciate your advice though...
there are some programs however that I'd like to try and/or require on ubuntu for myself and my parents that arn't in the add/remove menu.
Some tips for n00bs:

- Make sure all of your repositories (or at least main universe and multiverse) are enabled in System -> Administration -> Software Sources.

- If the program still isn't available in the Ubuntu repos, then search for a .deb on the web. Some sites I like for "3rd-party" .debs are [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas) (Personal Package Archives) and [http://www.getdeb.net/](http://www.getdeb.net/)

- If a .deb isn't available, then one can compile from source. Often, newer users will stumble because they lack the appropriate development libraries. One can sometimes figure out what lib**-dev packages they need from the README and/or INSTALL files, but unfortunately, this is not always true.

---

