---
title: "Recommendations for installing on a PII w/256 RAM?"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by JackD on 2005-12-13
I'm setting up a computer lab for an orphanage over Christmas ([http://www.nyumbani.org](http://www.nyumbani.org)) and their equipment is PIIs with 256 RAM (Dell Optiplex GXA).

Is it possible to streamline or minimize an Ubuntu/Edubuntu installation so that it will perform adequately?

Any experience running Ubuntu/Edubuntu on a P2?

Thanks

---

### Post by Swab on 2005-12-13
[QUOTE=JackD]I'm setting up a computer lab for an orphanage over Christmas ([http://www.nyumbani.org](http://www.nyumbani.org)) and their equipment is PIIs with 256 RAM (Dell Optiplex GXA).

Is it possible to streamline or minimize an Ubuntu/Edubuntu installation so that it will perform adequately?

Any experience running Ubuntu/Edubuntu on a P2?

Thanks[/QUOTE]

You could do a server install, then install xubuntu-desktop... leaving you with XFCE instead of gnome.. then install all the educational packages.

That orphanage looks like it's doing good work by the way!

---

### Post by az on 2005-12-13
[QUOTE=JackD]I'm setting up a computer lab for an orphanage over Christmas ([http://www.nyumbani.org](http://www.nyumbani.org)) and their equipment is PIIs with 256 RAM (Dell Optiplex GXA).[/QUOTE]

If you have limited (or no) internet conectivity, see this for help on getting custom cds for the extra packages you need.  This is also the kind of thing I had in mind to use up my box of older (but still useful) hardware. 

[http://fridge.ubuntu.com/node/159](http://fridge.ubuntu.com/node/159)
[https://wiki.ubuntu.com/forum/GiveAway](https://wiki.ubuntu.com/forum/GiveAway)


[QUOTE=JackD]

Is it possible to streamline or minimize an Ubuntu/Edubuntu installation so that it will perform adequately?

Any experience running Ubuntu/Edubuntu on a P2?

Thanks[/QUOTE]

An intel pentium II usually has a considerable cache (512k) which makes it perform really well in comparison to equvalent or faster celerons or durons.  

I find a pentium II 300Mhz fast enough to run the default Ubuntu desktop.  It really depends on what you are expecting, but it runs well enough.  256 Megs of ram is nice too, although 128 is the bare minimum I would subject the full Ubuntu desktop to.

How fast are your pentium IIs? 

You can install an alternate desktop environment like XFCE (Xubuntu-desktop) or icewm.  If you cannot connect to the internet or if downloading large ammounts of data is costly, you can have someone (like me) send you a cd or two full of extra packages from the Ubuntu archive.  See the link above.

Ubuntu (or Edubuntu) is excellent for the purpose you describe.  It is quite useable on older hardware.  You can even use a BadRam-patched kernel to use ram sticks with bad bits - That patched kernel can be told to just avoid using the bad bits.  You cannot do that with other operating systems.

---

### Post by peteyp666 on 2005-12-13
I have installed and used the default install of Ubuntu breezy on a PII GX1 which I believe was 500Mhz, and I had no problems.  I was also only using 192 mb of ram and it seemed fast enough to be usable to me.

---

### Post by factotum218 on 2005-12-13
Personaly I can't say either way with Ubuntu. My next system down is a 800mHz amd irongate, but after that system is a PentiumMMX at 166mHz with 32 megs of ram. The problem is that I have never attempted any install regarding Ubuntu or even Debian. I have however had luck with both Slackware and FreeBSD running blackbox and surfing the web with something like Dillo and use irsii for IRC, Gaim for IM etc. It seems to me that Ubuntu would be possible maybe through the 'SERVER' install option maybe. That way you can pick and choose what to install. I dont think Gnome would do very well on that. Maybe XFCE or Fluxbox??

---

### Post by JackD on 2005-12-13
Thanks, all, for your comments.

-I've tried to create the Xubuntu-desktop on a regular system (from an Edubuntu CD) to try it out (server install, modded /etc/apt/sources.list, run sudo apt-get update, and then udo apt-get install xubuntu-desktop). It takes about 45 minutes to download everything (610 M) over broadband. 
- Maybe I'm doing the Xubuntu-desktop installation wrong, but I can't imagine doing it on a P2 without broadband.
- There must be a simpler, more direct way to get the xubuntu-desktop installed. Any ideas?

- The Dell Optiplex GXAs we are using are anything from 233 MHz to 333 MHz. The RAM will be at least 256 or maxed out at 384 M. I won't know for sure until I arrive this Sunday.

- Maybe Edubuntu will work fine as is, and just be a little pokey. However, the comment about the archives looks good. So, when I look at, for example, [http://archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/](http://archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/) which is the one that I should grab?

# 3dchess_0.8.1-11.diff.gz
# 3dchess_0.8.1-11.dsc
# 3dchess_0.8.1-11_i386.deb
# 3dchess_0.8.1.orig.tar.gz

---

### Post by az on 2005-12-14
[QUOTE=JackD]Thanks, all, for your comments.

-I've tried to create the Xubuntu-desktop on a regular system (from an Edubuntu CD) to try it out (server install, modded /etc/apt/sources.list, run sudo apt-get update, and then udo apt-get install xubuntu-desktop). It takes about 45 minutes to download everything (610 M) over broadband. [/QUOTE]

If you leave the cdrom as a repository, it will take about 500 megs of that from the cd.  Xubuntu-desktop and it's dependancies are about 35 megs.  Xorg is another 35 or so.  You should not need to download that much.


[QUOTE=JackD]- Maybe I'm doing the Xubuntu-desktop installation wrong, but I can't imagine doing it on a P2 without broadband.[/QUOTE]

The P2 is not the factor as much as the internet connectivity.  See the page I referred to about having soneone making you a custim cd (or make it yoursel with the Apt-Move Howto in the wiki (see the page for the link)

[QUOTE=JackD]- There must be a simpler, more direct way to get the xubuntu-desktop installed. Any ideas?[/QUOTE]

With a cd full of extra packages from the repository, you can just install from the install cd, pop in the extra cd and add it as a repository and install the xubuntu stuff from there.

[QUOTE=JackD]- The Dell Optiplex GXAs we are using are anything from 233 MHz to 333 MHz. The RAM will be at least 256 or maxed out at 384 M. I won't know for sure until I arrive this Sunday.[/QUOTE]

I have a few faster PIIs hanging around.  I am pretty sure your's are slot 1, but do they need a funky heatsink?

[QUOTE=JackD]- Maybe Edubuntu will work fine as is, and just be a little pokey. However, the comment about the archives looks good. So, when I look at, for example, [http://archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/](http://archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/) which is the one that I should grab?

# 3dchess_0.8.1-11.diff.gz
# 3dchess_0.8.1-11.dsc
# 3dchess_0.8.1-11_i386.deb
# 3dchess_0.8.1.orig.tar.gz[/QUOTE]

The deb is the binay package that installs.  The diff, orig.tar.gx and dsc are the source packages for building debs.  You will have problems getting the debs by hand since you will not know what dependancies they have.  You can use apt to spit out a list of URIs to use to get the debs from a broadband-cennected machine.

---

### Post by bb002 on 2005-12-15
Well I used to run Mandriva 2005LE on my old Dell Demension XPS D266 (266Mhz P2) with 256MB Ram. I thought Mandriva ran very well and I have found Ubuntu to be faster than Mandriva. My only complaint is that load times are pretty long (boot-up, opening applications) on the p2 but once applications were loaded I thought they ran just fine, but your mileage may vary. btw I'd still be using my 266Mhz box as my main machine if it wasn't for my gaming addiction making the move to the pc. I ran Ubuntu on the 266Mhz box for about a week before I finish building my new box but it was long enough for me to trash my mandriva cds.

---

