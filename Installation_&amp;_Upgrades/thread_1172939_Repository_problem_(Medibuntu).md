---
title: "Repository problem (Medibuntu)"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Outolempi on 2009-05-29
Hi

I can't reach the programs in third-party repositories.

I added Medibuntu to the list of my third-party repositories as told in [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) 

First I added Medibuntu to the sources.list as instructed (for Ubuntu 9.04 "**Jaunty** Jackalope"):
[I]sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
[/I]
and then I added the GPG key as instructed:
 *[FONT=Courier New]sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update[/FONT]*

Now, when I go to System > Administration > Software Sources and choose the Third-Party Repositories tab I see the original "jaunty partner" and newly added "Medibuntu". And in the Authentication tab both are listed. Should work, shouldn't it?

But when I go to "Add/remove programs" the Third-Party category is empty. What happened? I've tried to uncheck Medibuntu from the repositories in Software Sources. So, when there's only jaunty partner checked, the Third-party category in "Add/remove programs" is still empty!

I don't know what else to try?

Tohtori Outolempi

---

### Post by Outolempi on 2009-06-01
I tried the Synaptic packet manager and it doesn't have any problem showing the third-party repositories! So, now I'm using that instead of Add/remove programs.

Still, this is only a workaround. I'd be happy to know how to get the Add/remove programs to show the programs available in third-party repositories, because I prefer to use it.

---

### Post by oldos2er on 2009-06-01
Once you add a repository, you need to update your sources.list
```
sudo apt-get update
```

---

### Post by Muskegman on 2009-06-01
Hi I had the same problem and this is what i did to correct it.
[http://ubuntuforums.org/showthread.php?t=1147414](http://ubuntuforums.org/showthread.php?t=1147414)

---

### Post by Outolempi on 2009-06-02
Hi,

Thank's for advice, but unfortunately they didn't help.

I tried again *sudo apt-get update, *no difference.

I also tried the instructions
[I]gpg --keyserver keyserver.ubuntu.com --recv 2836CB0A8AC93F7A
gpg --export --armor 2836CB0A8AC93F7A  | sudo apt-key add -
[/I]without difference. 
And just to be shure after the gpg instructions I did *sudo apt-get update* again.

For example, I can find Google Earth using Synaptic, but not Add/remove programs. Well, I'll just use Synaptic for now.

---

