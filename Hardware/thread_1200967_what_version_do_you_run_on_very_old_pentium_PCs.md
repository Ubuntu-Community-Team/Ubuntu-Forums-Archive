---
title: "what version do you run on very old pentium PCs?"
date: 2009-06-30
forum: Hardware
---

### Post by djrakun on 2009-06-30
hi everyone,

I'm a bit of an Ubuntu evangelist and whenever I find someone who has a machine that they are going to scrap because it is 'too old and slow', I usually coax them into installing Ubuntu on it just to give it a try.  I have been very successful in getting people interested and comfortable with Ubuntu using their old hardware ( I even have a few converts that I can claim responsibility for!)

I have generally stayed away from xubuntu because the goal is to get people familiar with gnome to where they will put Ubuntu on their modern hardware.  I've had great success with Feisty and Gutsy on machines as old as Pentium II 366 mhz with 256mb of ram.  People just can't believe how much they can get out of their PCs that are older than their children!

I am in a bit of soup lately though:  I noticed on my old ancient hardware that Hardy is just a bit too much for pentium 2 and 3s.  With the repositories closed on gutsy as of April, I can't show people how 'easy' it is to download the software they are looking for with the 'add/remove programs' feature, which is a large part of my sales pitch.  I was wondering what the rest of you do when you have a dog of a machine nowadays.  Do you still use the 7s and somehow access a still-functioning repository or do you download the binaries and compile them ( that's what scares people off.  they don't like that scary 'make install' step for some reason ;) )  

In your experience what do you do to Ubuntu on old machines now that Gutsy is retired?  If anyone has some tips I can't wait to read them

Thanks!

---

### Post by LepeKaname on 2009-07-01
I'm running ubuntu-minimal (Intrepid) in my P2 400Mhz 256Mb ram.

---

### Post by BbUiDgZ on 2009-07-01
for lower spec machines i use [http://xubuntu.com/](http://xubuntu.com/)

---

### Post by djrakun on 2009-07-01
minimal intrepid sounds interesting.  

not long after I posted I found this thread from a few hours before

[http://ubuntuforums.org/showthread.php?t=1200764&highlight=feisty+repositories](http://ubuntuforums.org/showthread.php?t=1200764&highlight=feisty+repositories)

this will keep feisty and gutsy usable for the time being.  I will check out the intrepid minimal right now.  I thought that the minimal cd only made the cd smaller, and installed the same things as the typical installation except used the internet for all packages rather than the cd.  I just re-read the description of the minimal cd and it does say it only installs the minimum needed for the installation, which is cool.  

I guess my concern is that me and the community might have a different idea of what is 'minimal'.  Is intrepid minimal pretty functional without needing to install several additional packages?  I don't really care if it is missing openoffice or obvious packages, but if it is missing packages essential for basic function then I might be better off sticking with Feisty.  Still, having the later kernel installed would be an upgrade in itself, and I really dig the cellular broadband compatibility built in, rather than configuring wvdial on each machine I use my card on.

Thanks!

---

### Post by snowpine on 2009-07-01
I never recommend obsolete Ubuntu releases (7.10 or older) because they no longer receive security patches and bug fixes. Plus of course the repositories are closed and there will be no more updates.

On my older hardware, I've had good luck with Crunchbang (Ubuntu with Openbox instead of Gnome), SliTaz (a super-fast minimal distro), and Debian (the best compromise imho; basically Ubuntu without the brown bloated bunnies).

---

### Post by LepeKaname on 2009-07-01
So far I have that P2 server for my personal website and it works without any problem. Of course it doesn't come with a window manager, but as far you have aptitude, you can install what ever you need. Keeping it simple. 

Depending on your needs, you can then install openssh, ufw, LAMP, etc. I really like to start from that point as the installation size is around 10MB! and I don't have a bunch of software that I don't need. Network usually will be up and running with that installation.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Enjoy!

By the way... I use Xubuntu in my main desktop, and my computer is not old! I use Xubuntu because it just give me what I need, not just about performance. ;)

---

### Post by djrakun on 2009-07-02
> **snowpine said:**
> I never recommend obsolete Ubuntu releases (7.10 or older) because they no longer receive security patches and bug fixes. Plus of course the repositories are closed and there will be no more updates.

On my older hardware, I've had good luck with Crunchbang (Ubuntu with Openbox instead of Gnome), SliTaz (a super-fast minimal distro), and Debian (the best compromise imho; basically Ubuntu without the brown bloated bunnies).


Wow, very much enjoying #!.  Super light and very usable.  This will be great for me, but for my Avon lady work I'm worried that the window interface is too dissimilar to Windows.  The lack of an application bar will be a turn-off.  Also I haven't found the 'add/remove programs' app.  Synaptic is there and just as good, but not as cute.  That window is a great way to show people how 'easy' apt-get really is, and is usually the deal-sealer in turning someone over to the nix side.

With some more nav time I might figure out how to add these two things and then I have a winner.  I'll be trying SliTaz next

---

### Post by djrakun on 2009-07-02
> **djrakun said:**
> The lack of an application bar will be a turn-off.  

yes, i dont think this will take any time at all.  the theme confused my small brain and i didn't realize that there WAS a menu bar at the base of the screen, as black as the background ( d'oh)  I added a few icons to it and now it looks like good ol' ubuntu.

Add/Remove Progs probably soon to follow.  cheers!

---

### Post by snowpine on 2009-07-02
> **djrakun said:**
> WAlso I haven't found the 'add/remove programs' app.  Synaptic is there and just as good, but not as cute.  That window is a great way to show people how 'easy' apt-get really is, and is usually the deal-sealer in turning someone over to the nix side.

```
sudo apt-get install gnome-app-install
gksu gnome-app-install
```

---

