---
title: "How do I get rid of KDE?!?"
date: 2005-11-25
forum: General Help
---

### Post by Mosey on 2005-11-25
So I took the advice of various open-source gurus on this board and installed both desktops so as to find one I like.

I like GNOME. It's far superior in every way I care to contemplate.

So, how do I get rid of KDE? It's not the obvious 'sudo apt-get remove kde-desktop' as that only removes 32kbs of something.

I need to get rid of this. It's a liability.

How do I completely purge my system of all KDE files and packages?!

---

### Post by Ruso on 2005-11-25
I think using synaptic u can get rid of KDE completly.

Run synaptic and use search to find the KDE components.

---

### Post by Xian on 2005-11-25
Remove kdelibs and the rest will follow.

---

### Post by matthew on 2005-11-25
I second the recommendation. Use Synaptic and search "kde." Also, look in the full listing in the section of programs that begin with the letter k for lots of kde apps. If removing a certain one makes you nervous, leave it for now. You can go back later.

You can also look at things named kde* (like kde-base) and this will get most, if not all.

---

### Post by Xian on 2005-11-25
Personally, I'd just install a Ubuntu-only system again. By the time you dig about, and play around with removing this and that, you could have reinstalled what you want anyway several times over. Just do it right the first time.

---

### Post by Ruso on 2005-11-25
Xian it is all depend on ur Computer CD-ROM and HD speed. For example to install Ubuntu in my laptop it takes me about 1 hour and a half. Also If u want a clean installation u might want to backup the data to be able toformat the HD.

And anyways reinstalling the OS has to be the **last last last** step to do.

---

### Post by Xian on 2005-11-25
[QUOTE=Ruso]And anyways reinstalling the OS has to be the **last last last** step to do.[/QUOTE]
Obviously it's not the desirable thing to do, but you know how it is--to each his own. In my case I would rather just do it right the first time and not worry about it any further. A person could chase their tail for quite a while on this type of removal scenario, and still not be certain they ended up with the system they initially desired. 

But like I said, if you take out kdelibs it should pull down most of the house with that one brick. A person could also go over to the Ubuntu Packages website, do a search for 'kubuntu-desktop' and cross-reference the listed kde deps for that meta-pkg with what remains on their system.

---

### Post by Kuolio on 2005-11-25
Hmm, I'd recommend that you just search kde packages using Synaptic and do "remove completely" to purge them out of your system. I've tried out few DE's and WM's like xfce, KDE and some *boxes, but really nothing beats ubuntu-gnome atm. The integrations of applications, the special tools, look and feel and the general integration and polishing is just awesome.

When I uninstalled KDE, or XFCE, I just searched packages with synaptic (luckily it has it's own KDE section..) and purged all I could find. When you remove the *-base and *library stuff, you usually get rid most of the DE packages and some KDE spesific software, if they are depending on those libraries. Like amaroK and K3b. Getting rid of the app's was the part that took the longest but still it took only 20 minutes. Way faster then re-installing the whole system.

---

### Post by mcduck on 2005-11-25
After all that it might be a good idea to install deborphan. It might help in removing useless KDE packages..

You can use it with synaptic. just make a new filter to show only orphaned packets.

---

### Post by Randy Sparks on 2005-11-25
Personally I don't see why you want to get rid of KDE. I'd keep it around in case you install any software in future that relies on its libraries (there are quite a few handy KDE items in the 5.10 software repositories). Unless you're really short on disk space, having it around will do no harm.

---

### Post by xristos on 2005-11-25
Try removing the kubuntu-desktop packet

---

### Post by Schmots on 2005-11-25
You can have the qt libraries and the core kde libs with out having all of kde, and I suggest you do.. k3b for example is one of the best burn frontends I have ever seen.

On the front of rebuilding your system and that being a "last resort"

I like to play with distros.  I run about 4 on all my systems at any given time.  Here is what I started doing years ago, its simple but its great.  Make /home its own partition.  Now when you rebuild, change distro etc.. you just don't format that partition, ust use your installer or edit your /etc/fstab file to point to that partition for /home and boom, all your home files are back, just make sure to use the same username you used last time.  You might find that some file aren't readable or editable but thats easy to fix.  See in linux permissions are tied to a number in /etc/passwd and /etc/group and your # may change during rebuilds, so all you need to do after your have your old /home mounted is as your users

chown -R username:username(or users or what ever other group you use as your default, username: will also suffice) *     From with in your ~ so for me t looks like this

chown -R david:david *

Hope that makes it easy for you and lets you play with lots of stuff ,just remember to manuely edit your partition tables and not let an auto program do it or it will most likely format your home.

---

