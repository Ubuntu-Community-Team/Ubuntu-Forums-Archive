---
title: "Installing mono-2.2 on Ubuntu 8.10"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by Aga^^ on 2009-03-07
hi everybody,
i want to build c# (console and windows app.) and asp.net applications on ubuntu 8.10. I have mono-2.2, libgdiplus-2.2, gtk-sharp-2.12.6 and webkit-sharp-0.2 files.I did something like installing mono, libgdiplus and gtk-sharp but i couldnt find how can i run the mono and building (incorrect installation may be) applications. I especially want GUI applications. Can anyone explain me how can i install and run the mono?

---

### Post by directhex on 2009-03-07
Don't.

You'll break things if you try to use a non-package Mono as your main Mono.

8.10 comes with Mono 1.9.1

---

### Post by Aga^^ on 2009-03-08
ok thanks for your help, i installed mono from writing

apt:mono-2.0-devel

to the browser. But i couldnt find how to run the mono?

---

### Post by directhex on 2009-03-08
> **Aga^^ said:**
> ok thanks for your help, i installed mono from writing

apt:mono-2.0-devel

to the browser. But i couldnt find how to run the mono?

"how to run the mono"?

What exactly are you trying to do?

Use "mono assemblyname.exe" to run an assembly with Mono. Run F-Spot or Tomboy to see example Mono apps

---

### Post by Aga^^ on 2009-03-08
i could not find any shortcut for mono on the desktop and applications bar.Where is the F-Spot or tomboy? can you explain please?( i do not use linux for 3 years and i just turn back linux 2 days ago)

---

### Post by directhex on 2009-03-08
> **Aga^^ said:**
> i could not find any shortcut for mono on the desktop and applications bar.Where is the F-Spot or tomboy? can you explain please?( i do not use linux for 3 years and i just turn back linux 2 days ago)

Mono isn't an app, it's a framework. What would a desktop icon give you? It's like asking for a desktop icon for "Microsoft .NET Framework". Mono is used to run apps, or to provide compilers - it doesn't do anything of use in isolation.

F-Spot is part of a standard Ubuntu desktop install, in the Graphics section. It's a Mono-based app. Tomboy is under Accessories, same deal - default install.

---

### Post by Aga^^ on 2009-03-08
hmmm i was thinking wrong.Now i need a compiler like Microsoft Visual Studio, does Linux have a compiler like this?

---

### Post by directhex on 2009-03-08
> **Aga^^ said:**
> hmmm i was thinking wrong.Now i need a compiler like Microsoft Visual Studio, does Linux have a compiler like this?

Yes. *mono-2.0-devel* package, use "gmcs" to compile things.

Or install *monodevelop* if you want a GUI IDE

---

### Post by cb951303 on 2009-03-08
I installed mono 2.2 from PPA few weeks ago. nothing is broken. tomboy, f-spot, banshee and gnome-do works as they should.

---

### Post by Aga^^ on 2009-03-08
i downloaded monodevelop-1.0 and tried to install it but i couldnt 
there was a warning 
No package 'gtksourceview-sharp-2.0' found
then i downloaded libgtksourceview2.0-cil_0.12-3_all but i didnt understand what can i do with that?

---

### Post by Aga^^ on 2009-03-08
cb951303 i installed mono-2.2 and Tomboy,F-spot are not working how can i fix it?

---

### Post by directhex on 2009-03-08
> **Aga^^ said:**
> i downloaded monodevelop-1.0 and tried to install it but i couldnt 
there was a warning 
No package 'gtksourceview-sharp-2.0' found
then i downloaded libgtksourceview2.0-cil_0.12-3_all but i didnt understand what can i do with that?

Why not use the package manager, exactly? Tick the box in SYnaptic ot Add/Remove Programs, don't try to force .deb files

---

### Post by directhex on 2009-03-08
> **cb951303 said:**
> I installed mono 2.2 from PPA few weeks ago. nothing is broken. tomboy, f-spot, banshee and gnome-do works as they should.

Package building will be broken for you, as are a few apps which don't work with 2.2

The pkg-mono team is skipping 2.2, it was a bad release

---

### Post by cb951303 on 2009-03-08
> **directhex said:**
> Package building will be broken for you, as are a few apps which don't work with 2.2

The pkg-mono team is skipping 2.2, it was a bad release

just realised I got 2.0 :) sorry for the confusion

---

### Post by Aga^^ on 2009-03-08
when i clicked the libgtksourceview2.0-cil_0.12-3_all there was an error "Dependency is satisfiable: libglib2.0-cil".
i think it depends installing mono-2.2
how can i remove the mono-2.2 from my system?

---

### Post by directhex on 2009-03-08
> **Aga^^ said:**
> when i clicked the libgtksourceview2.0-cil_0.12-3_all there was an error "Dependency is satisfiable: libglib2.0-cil".
i think it depends installing mono-2.2
how can i remove the mono-2.2 from my system?

You tell me. I'm pretty sure I warned you not to do it, saying "You'll break things if you try to use a non-package Mono as your main Mono."

---

### Post by Neo_The_User on 2009-03-08
Use winetricks to install Mono + GTK on Ubuntu.

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by cb951303 on 2009-03-09
> **Aga^^ said:**
> when i clicked the libgtksourceview2.0-cil_0.12-3_all there was an error "Dependency is satisfiable: libglib2.0-cil".
i think it depends installing mono-2.2
how can i remove the mono-2.2 from my system?

ah I feel responsible for this

remove every mono related package with the option "--purge" to get rid of config files if there are any.
remove the repo entry for mono 2.2 (if you added them), update and reinstall mono
that should do it :popcorn:

---

### Post by Aga^^ on 2009-03-09
cb951303 how can i use the "--purge" command?

---

### Post by Neo_The_User on 2009-03-09
Did I not say winetricks?

---

### Post by Aga^^ on 2009-03-09
cb951303 how can i use the "--purge" command?

---

### Post by Neo_The_User on 2009-03-09
Wow. It's as if I don't exist.

---

### Post by directhex on 2009-03-09
> **Neo_The_User said:**
> Did I not say winetricks?

How does Wine help, exactly?

---

### Post by Aga^^ on 2009-03-09
if i use winetricks, it can delete the mono-2.2 and then i can install mono-1.9.1 so everything will be allright?

---

### Post by Aga^^ on 2009-03-09
i downloaded winetricks, but it does not include mono-1.9.1 and also i could not run it by typing "sh winetricks"?
i must delete mono-2.2 from my system.Do you have any other idea?

---

