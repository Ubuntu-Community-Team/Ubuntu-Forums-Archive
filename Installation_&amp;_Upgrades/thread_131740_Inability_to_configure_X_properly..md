---
title: "Inability to configure X properly."
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by -Demosthenes- on 2006-02-17
I realize that I am a total newb at this; this is my third failed installation with three distros.  Try as I might, I can never get it to work properly.  My latest case:

Ubuntu Breezy Badger 5.10.

My difficulty is that both NICs in the machine are too old for Ubuntu to know what they are.  That isn't so much of a problem, and could be fixed, were it not for Ubuntu's obsession with DNS servers (from what I have read, my problem is caused by lack of one).

The command "X -configure" will not work because I do not have root priveleges.  The command "sudo" with any number of various arguments will not work, returning an error: "sudo: unable to lookup ubuntu via gethostname()".

Is there any way to get around this error without having to try to find, download, burn, mess around with, and perhaps install linux drivers for one or both NICs?  That probably wouldn't work anyway, because I imagine I would need root priveleges to install the drivers.

Quite a dilemma I have going.  Has anyone ever run into this before?  Any help would be appreciated.

Thanks in advance!

---

### Post by MrCheese on 2006-02-17
What are your NICs - make, chipset & bus type (ISA/EISA/PCI etc) ?

---

### Post by Mustard on 2006-02-17
I have a suspicion I know what is wrong with your sudo privileges.  It is very reminiscent of a misconfigured /etc/hosts file.  If you were to boot up in recovery mode from grub, that would put you at a root prompt and you could edit your /etc/hosts file and from there you should have superuser privileges, which should allow you some more latitude to use other configurations options for setting up xorg.conf.

Anyway, if your interested in trying that angle, I'll go into detail about what you need to do. :)

---

### Post by -Demosthenes- on 2006-02-17
One of the cards is either on EISA or ISA, probably the former (though I cannot remember now the differences 'twixt the two) and is a 3-com 3c509b-c.  The other is on the same bus, and I can't recall ever figuring out what it was.  This is pretty old hardware I'm dealing with, which makes it hard to find drivers.

That sounds interesting, Mustard.  I would like to hear those details, if you will.

---

### Post by Mustard on 2006-02-17
I'm just going to copy and paste the instructions I wrote out in another post. :)  If you feel like posting what the first line of your /etc/hosts file looks like, I'd be curious.  Anyway, here are the instructions as written out for a number of different people having your symptoms.....

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the recovery mode option from the grub menu at bootup.

When you get to a root prompt, open up the /etc/hosts file with this command.

```
nano /etc/hosts 
```

The /etc/hosts file normally looks something like this...

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What you need to do is to edit the first line so that it contains a hostname for your computer.  Mine is called 'slave' as you can see above.  You can choose any name you like.  The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```

---

### Post by -Demosthenes- on 2006-02-17
I have no GRUB bootup menu.  Something that looks vaguely like a menu flashes for a second or two before it goes to Ubuntu.  Before the prompt after Ubuntu fails to initialize X, there is no way to input, or no input echoes.  How do I enter recovery mode?

---

