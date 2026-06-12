---
title: "After fresh install of 9.04, cannot open a root terminal"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Convert on 2009-04-28
Everyone,

Here is a new problem I have never seen before.  After doing a fresh install of Ubuntu 9.04, I cannot open a root terminal.

I am running the System Tools : Root Terminal menu item installed by the system.  The command it has in it is "gksu /usr/bin/x-terminal-emulator"

gksu runs in a normal terminal and /usr/bin/x-terminal-emulator runs in a normal terminal.

When I run the command gksu /usr/bin/x-terminal-emulator in a regular terminal, I get the error "Failed to contact the GConf daemon"

I get the same error when I run the command sudo /usr/bin/x-terminal-emulator.

When I run the su command (the command called by gksu) in a regular terminal, I get the error "su: Authentication failure"

However, to test the gksu/su commands I also ran gksu gedit, which works fine.

I don't see a process called GConf running on my computer but I do see a process called gconfd-2 running.  Also, according to Synaptic, I have a GConf2 installed but no GConf.

So what do I need to do to be able to run a root terminal?

---

### Post by shatterblast on 2009-04-28
Why not try gnome-terminal?  Usually, it is under:

Applications -> Accessories

I just put sudo in front of whatever command.  It basically does the same thing. Like:

sudo gedit my_cool_file_name_here_dude

---

### Post by Convert on 2009-04-28
> **shatterblast said:**
> Why not try gnome-terminal?  Usually, it is under:

Applications -> Accessories

I just put sudo in front of whatever command.  It basically does the same thing. Like:

sudo gedit my_cool_file_name_here_dude

Thanks for the suggestion.  I tried gksu gnome-terminal and sudo gnome-terminal and both give the same error "Failed to contact the GConf daemon".  I think the problem is that there should be some redirect of calls going to GConf to be passed to GConf2 instead but it's not on my computer (and I don't know how to add it myself).

---

### Post by shatterblast on 2009-04-28
My apologies.  "Sudo" is only used once you are actually in the terminal screen.  Just use "gnome-terminal" if you are creating an icon for it.  As well, "gksu" can be used by itself as well.  The command "gksu gnome-terminal" does not execute for me either.  There are commands that work in a command shell that will not work in other areas.

---

### Post by Convert on 2009-04-28
> **shatterblast said:**
> My apologies.  "Sudo" is only used once you are actually in the terminal screen.  Just use "gnome-terminal" if you are creating an icon for it.  As well, "gksu" can be used by itself as well.

I can open a terminal with either gnome-terminal or x-terminal-emulator.  I just can't open them as root.  I need a root terminal in order to edit and delete config files that are not set up properly for my laptop.

Since starting this thread, I have found that I can start a root terminal by opening a regular terminal and then using the command sudo su or sudo -i.  However, I would like to understand why the method provided by the install no longer works (it worked in 8.04).

---

### Post by shatterblast on 2009-04-28
There might have been a slight policy change in relation to how the Debian version of the Linux kernel approaches security.  Debian in turn derives its version from the Linux foundation itself I think.  Since the software passes a lot of hands so to speak, it's difficult for me personally to tell who made the choice.  I haven't tested Red Hat Fedora to confirm the change, but Intrepid 8.10 seemed to have it.

---

### Post by xinix111 on 2009-06-01
i want to sort this out aswell !!

i am very surpriced there are not more people who want to get this working.

all the suggestions about just running commands with su/sudo/gksu i dont understand.  

The root terminal exists so we dont have to type sudo/gksu/su.
I quess the results are different too actually, even tho i am not sure of that.

But why would sudo be the same as su or gksu, if all 3 accomplish the same than 2 are useless and should be removed......

---

### Post by merlinus on 2009-06-01
Reading this may help:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by oldos2er on 2009-06-01
This is a known bug: [https://bugs.launchpad.net/ubuntu/+bug/326158](https://bugs.launchpad.net/ubuntu/+bug/326158)

 Just FYI, you can run **gksu /usr/bin/xterm** to get a working root terminal.

---

### Post by leftyfrizzell on 2009-06-13
> **oldos2er said:**
> This is a known bug: [https://bugs.launchpad.net/ubuntu/+bug/326158](https://bugs.launchpad.net/ubuntu/+bug/326158)

 Just FYI, you can run **gksu /usr/bin/xterm** to get a working root terminal.

Works like a charm...thanks.  This does what I need.:popcorn:

---

### Post by punkybouy on 2009-06-17
I have the same problem.  The fix presented here works fine but still need to find out if the lack of a root terminal is a bug.
Thanks for the fix!!!!

---

