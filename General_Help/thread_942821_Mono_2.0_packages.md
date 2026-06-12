---
title: "Mono 2.0 packages?"
date: 2008-10-09
forum: General Help
---

### Post by rogier.de.groot on 2008-10-09
Is there any repo containing mono 2.0 (and monodevelop 2.0) binary packages? The standard mono in hardy is way old, and even badgerports only has 1.9. Kind of weird, mono not supplying packages for the most popular (?) distro.

In similar vein: any repo for up to date java/netbeans packages? Got to do cross-platform development somehow, and java would be my second choice after c#.

TIA

---

### Post by ibuclaw on 2008-10-09
From what I've seen after a brief overview, you have 3 options.

[1) Compile from source]("http://ftp.novell.com/pub/mono/sources-stable/")

[2) See if you could use alien to convert one of the rpm-based packages to deb.]("http://ftp.novell.com/pub/mono/download-stable/openSUSE_11.0/")

[3) Use the Mono LiveCD/VM Image]("http://www.go-mono.com/mono-downloads/download.html")

I wouldn't mind opting for option 3...
Seems like the least hassle.

Regards
Iain

---

### Post by drubin on 2008-10-09
> **rogier.de.groot said:**
> Got to do cross-platform development somehow, and java would be my second choice after c#.
TIA

Why on earth would you pick C# as a cross-platform development lang? Its support in other OS's other then Windows is very very limited. 

Java would always be my first choice with cross-platform development, although I have heard some good things about Python.

---

### Post by Yellow Pasque on 2008-10-09
Is libmono2.0-cil  what you want?

EDIT: Nvm, I see you want monodevelop to be 2.0, but it's not even in the Intrepid repo [http://packages.ubuntu.com/search?keywords=monodevelop&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=monodevelop&searchon=names&suite=intrepid&section=all)

Bottom line: If Ubuntu/Debian can't provide it, build from source.

---

### Post by drubin on 2008-10-09
> **rogier.de.groot said:**
> In similar vein: any repo for up to date java/netbeans packages? 

For latest development stuff it is never going to be in the repositories because it wont have been tried and tested enough here are the download links for some java development tools that are totally up to date. Both are stable and I use both of them. 

[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/) 
[http://download.netbeans.org/netbeans/6.1/final/](http://download.netbeans.org/netbeans/6.1/final/) 

As for the latest Java version, see this thread my post.
[http://ubuntuforums.org/showthread.php?t=939336](http://ubuntuforums.org/showthread.php?t=939336)

---

### Post by rogier.de.groot on 2008-10-09
> **drubin said:**
> For latest development stuff it is never going to be in the repositories because it wont have been tried and tested enough

Couldn't they just add an 'untested' repo or something?

Anyway, how do I compile mono to a .deb file and then shove it into my apt-cacher cache, so I don't have to compile from source on every computer I have.

---

### Post by drubin on 2008-10-09
> **rogier.de.groot said:**
> Couldn't they just add an 'untested' repo or something?

Anyway, how do I compile mono to a .deb file and then shove it into my apt-cacher cache, so I don't have to compile from source on every computer I have.

NOTE I have never done this before I have heard it works but to what extent I do not know. Please wait for another member to comment on this before trying it. please.

[http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)

---

### Post by drubin on 2008-10-09
[http://www.getdeb.net/search.php?keywords=mono](http://www.getdeb.net/search.php?keywords=mono)  
^^^ Is this what you were looking for?

---

### Post by directhex on 2008-10-09
Don't use Alien. Please. I won't support it. Backport packages *WILL* appear, I can assure you of that, but not until the software has proven to be sufficiently stable and reliable that myself or anyone else within pkg-mono is happy to attach our names to it.

As for source... go ahead, but please read [http://mjhutchinson.com/journal/2007/11/08/how_not_break_mono](http://mjhutchinson.com/journal/2007/11/08/how_not_break_mono) first and foremost

---

### Post by drubin on 2008-10-09
> **directhex said:**
> Don't use Alien. Please. I won't support it. Backport packages *WILL* appear, I can assure you of that, but not until the software has proven to be sufficiently stable and reliable that myself or anyone else within pkg-mono is happy to attach our names to it.

As for source... go ahead, but please read [http://mjhutchinson.com/journal/2007/11/08/how_not_break_mono](http://mjhutchinson.com/journal/2007/11/08/how_not_break_mono) first and foremost

Firstly  like I said I have never used Alien and said before any one uses it please confirm.

Are you a developer of Mono? 

That website: 
> The page you are looking for is temporarily unavailable.
Please try again later. 

---

### Post by directhex on 2008-10-09
> **drubin said:**
> Firstly  like I said I have never used Alien and said before any one uses it please confirm.

tinivole suggested it before you did. It's still an idea that'll only end in disaster. Really, don't do it.

> Are you a developer of Mono?

I'm part of the mono packaging team, and I run a third party backports repository for Mono for hardy with about 10,000 users.

> That website:

So try it again later. The URL should give a hint about the content

---

### Post by pkc on 2008-10-11
Building mono is not a trivial task but the source is at [http://ftp.novell.com/pub/mono/sources-stable/](http://ftp.novell.com/pub/mono/sources-stable/).  Its easier to install vmware and dowload the VMware openSUSE distro with all the mono tools, examples, and web server settings setup.  I know it was just released on Oct 6th so hopefully mono 2.0 will be part of next major kubuntu release.  I have Kubuntu running vmware openSUSE and its pretty responsive (its also a great way to see a real world configuration if you do a hardy build from source).  Even though Mono 2.0 is only a subset of the real .NET 2.0, its faster and more powerful than Java.  The monodevelop IDE is also pretty good considering its new... think how long Netbeans and Eclipse have been around and still are not anywhere near the speed, maturity, and power of Visual Studio .NET.  Today is the day I officially gave up on Java after 12 years of patience and hope.

---

### Post by fd0man on 2008-10-13
I've created a script that will install a parallel Mono (Mono 2.0) in ${HOME}/opt.  It also installs MonoDevelop 2.0 Alpha 1 current from SVN.  See [the post on my blog]("http://www.trausch.us/2008/10/13/want-to-play-with-mono-20-so-do-i/") which talks about it and provides many, many more details.

Just to make sure it's well-known and understood, I'll repeat part of what I said there, here:  A few words about the script: ***This script is released under the terms of the GNU General Public License, Version 3. It is version 3 ONLY. There is NO SUPPORT for this software; I wrote it for myself, and it may change or it may stagnate. I provide it in the hope that it is useful to someone out there other than myself, but it is AS-IS, WITHOUT WARRANTY, UNSUPPORTED software. If it changes your dog’s gender, bursts your house into flames, destroys your whatchamacallermicroflobbermajag, do not come and yell at me.*** That having been said, I welcome any modifications (at least to view them). You can modify it for your own use, you can share it (in fact I expect you to!) and you can tinker with and tweak it. Suggestions? Welcome! Comments? Welcome! Flames? Hey, free speech is your right…

---

