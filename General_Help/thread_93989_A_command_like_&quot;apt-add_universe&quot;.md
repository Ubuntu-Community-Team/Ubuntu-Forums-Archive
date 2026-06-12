---
title: "A command like &quot;apt-add universe&quot; ???"
date: 2005-11-23
forum: General Help
---

### Post by daller on 2005-11-23
Hi There,

Is there a command to uncomment universe in sources.list?

...And maybe an easy command for upgrading to the present release? ("sudo perl -pi.bak -e 's|breezy|dapper|g' /etc/apt/sources.list" is quite hard for newbies!)

Maybe a "stable" like in debian?

---

### Post by bonzodog on 2005-11-23
As in a command to do it without opening sources.list in an editor?
I don't know of a way of editing a text file in linux without opening the document. It's just easier to get people to do a 'sudo (editor) etc/apt/sources.list.
It's debians nature that means that at present there is no other way of changing the sources.list - It's a good idea for anyone coming to linux to learn a little bit of the CLI - after all, thats where linux's power really lies. People tend to forget that the X-windows system is just a program on top of a Unix-like operating system, that provides a friendly interface. Remember: all GUI programs are just interfaces to the CLI.

---

### Post by Wolki on 2005-11-23
Original question: There is no such command that i know of, but you could create a command that does it... It would probably look similar to the one you mentioned for upgrading, though.

[QUOTE=bonzodog]It's debians nature that means that at present there is no other way of changing the sources.list - It's a good idea for anyone coming to linux to learn a little bit of the CLI[/QUOTE]

Um, there's synaptic, It's a quite fullfeatured GUI sources.list editor.

---

### Post by bonzodog on 2005-11-23
synaptic gives you an option to add repositories, but not to uncomment existing lines - thus the only real way to do it is to edit the sources.list directly. Also, as I discovered, if you remove a repository it only removes it in synaptic - not in the actual file, so it doesn't directly edit the sources.list

---

### Post by daller on 2005-11-23
Well, I could use:

"sudo perl -pi.bak -e 's|#deb|deb|g' /etc/apt/sources.list"

...but it's not my point!

In debian the installer asked whether or not to use non-free software!
Wouldn't it be nice with something similar, asking about universe, and maybe multiverse?

About the upgrade thing:

Why aren't the releases concidered as "stable", "testing", "unstable" and "experimental" ???

In debian, I could dist-upgrade just like that! (without editing anything!)

---

### Post by ranf on 2005-11-23
[QUOTE=bonzodog]synaptic gives you an option to add repositories, but not to uncomment existing lines [/QUOTE]
Synaptic can be setup to do that. 
Settings -> Repositories -> [Settings] -> [X] Show disabled software sources

Then you get a check box in front of the entries.

---

### Post by bonzodog on 2005-11-23
/me learns something new... :)

---

### Post by Burning Bronx on 2005-11-23
[QUOTE=daller]...
Wouldn't it be nice with something similar, asking about universe, and maybe multiverse?

About the upgrade thing:

Why aren't the releases concidered as "stable", "testing", "unstable" and "experimental" ???
In debian, I could dist-upgrade just like that! (without editing anything!)[/QUOTE]
Non-free software repos are the Universe and Multiverse. So that's exactly what the installer is asking.
About the upgrade release. If you really want to dist-upgrade you shouldn't have any problems changing the repos to the newest version (just change the codename for each repo) and sudo apt-get dist upgrade. There are backports which I think (not sure) should be refered as testing software and all unstable/experimental stuff is in the currently developped release (currently dapper) repos.

---

### Post by daller on 2005-11-23
>So that's exactly what the installer is asking.
That was the Debian installer - The ubuntu installer doesn't ask that... 

>(just change the codename for each repo) 
Change it into what? (stable?) 

I debian I could use "stable" instead of "sarge" - Why is that not possible with ubuntu?

---

### Post by Burning Bronx on 2005-11-23
That's an easy question! It's not possible cause Ubuntu's not Debian :P
Sorry, but I really don't understand what's so hard about uncommenting a few lines  in sources.list (or changing the distro name for a dist-upgrade)... maybe it would be better for new users and if that's your point I agree it may be a nice addition to ask if they want universe and/or multiverse enabled. As for the upgrade I think an upgrade to an unstable distro shouldn't be done by newbies to linux/ubuntu (we don't want to screw their first experience do we?) and therefore is not needed at all.

Anyway... To not go off topic, I think that the "apt-add universe/multiverse" command you suggested is not necessary. I mean if you would be comfortable using the command line, editing the sources.list either with synaptic or the old-fashion way is just as easy or even easier. A choice, wether you want universe or multiverse enabled, integrated in the installer is cool tho.

---

### Post by Wolki on 2005-11-23
[QUOTE=daller]>So that's exactly what the installer is asking.
That was the Debian installer - The ubuntu installer doesn't ask that... [/quote]

I'm not sure this is a good idea. Installation should be easier with UbuntuExpress, but I still think the installer should ask as few questions as possible. If you want such a question, I think it would be better as a post-install question, like when the user starts synaptic for the first time.

> >(just change the codename for each repo) 
Change it into what? (stable?) 
I debian I could use "stable" instead of "sarge" - Why is that not possible with ubuntu?

I guess, since Ubuntu upgrades can (sometimes) be a bit more painful than Debian upgrades are supposed to be, they don't want automatic upgrading yet.

---

### Post by tomski on 2005-11-23
[QUOTE=bonzodog]synaptic gives you an option to add repositories, but not to uncomment existing lines [/QUOTE]

this option was in the hoary version in synaptic as i found very helpfull,
but i think the creators of synaptic decided to remove this small feature as a majority of people would rather edit the file than use gui


[ED]
sorry i went blind and failed to see the post after the one i quoted please feel free to ignore this post whoops!!
[ED]

---

