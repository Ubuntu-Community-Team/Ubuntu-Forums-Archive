---
title: "apt-build install installs precomiled binary instead"
date: 2008-07-14
forum: General Help
---

### Post by darkaudit on 2008-07-14
I wanted to try apt-build, so I did sudo apt-build install pan to compile and install the pan newsreader. When it finished the compile and cleanup, apt turned around and downloaded and installed the regular binary off the main repository instead.

I double-checked /etc/apt/sources.list, and my directory for locally compiled packages wasn't there. There's an apt-build file in /etc/apt/sources.list.d that includes deb file:/var/cache/apt-build/repository apt-build main but it didn't show up in synaptic until I added the line to sources.list.

Even after I did that, purging pan, and purging the downloaded package cache, when I tried sudo apt-build install again, apt downloaded and installed from the main repository once again. I had to manually install my compiled package to get it installed.

What have I missed here? Shouldn't the compiled package install when it's done instead of going to the regular repositories?

(edit: Problem was a combination of RTFM and a bug. Dpkg put the deb line in for sources.list, but it was both in the wrong spot, and not in the proper format. It was placed in a spot that contradicted apt-build's README. The README is right, dpkg is wrong.) :roll:

---

### Post by darkaudit on 2008-07-15
bump

---

### Post by darkaudit on 2008-07-15
The only thing I've come up with so far is that my local folder has the same precedence as the remote repository. Even then, No one has been able to confirm or deny that that would be a problem.

When apt-build was installed, I chose the Athlon 64 as the processor. I have an Athlon 64 x2 4200+ CPU. The original install only asked for the optimization level (I chose medium) and the processor when it was configured. Only when I did dkpg-reconfigure apt-build did it ask about the line in sources.list. Even then, it ignored my instruction to add the line.

So, what is happening is apt-build will gather all the materials necessary to compile a package, compile it, then throw all that work away and download the precompiled binary off the remote repositories anyway. I wind up with the compiled package in the proper folder, but if I want to install *that* one, I have to do it manually. Apt won't do it.

---

### Post by darkaudit on 2008-07-15
bump and additional...

When dpkg set up the repository entry for apt.build in /etc/apt/sources.list.d, it made the file apt-build. All the other entries for repos like Medibuntu and WINE had the .list extension. Apt could not see my build repository. When I copied apt-build to apt-build.list, apt could now see the repository.

I'm trying again to build pan instead of using the precompiled version. Even with the repository in the list, apt does not want the locally built version.

This is the result from apt-cache policy pan:

> pan:
  Installed: 0.132-2ubuntu2
  Candidate: 0.132-2ubuntu2
  Version table:
 *** 0.132-2ubuntu2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
        100 /var/lib/dpkg/status
     0.132-2ubuntu2 0
        500 file: apt-build/main Packages

---

### Post by darkaudit on 2008-07-15
I must've missed *something*, here. But what? I tried setting this up as my /etc/apt/preferences:

> Package: *
Pin: release o=apt-build
Pin-Priority: 990


It didn't help. any package I build with apt-build install is still ignored in favor of the regular repositories.

How about the result of apt-cache policy:

> Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages
     release o=winehq,a=hardy,l=winehq,c=main
     origin wine.budgetdedicated.com
 500 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
     release v=8.04,o=Medibuntu,a=hardy,l=Medibuntu,c=non-free
     origin packages.medibuntu.org
 500 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
     release v=8.04,o=Medibuntu,a=hardy,l=Medibuntu,c=free
     origin packages.medibuntu.org
 500 file: apt-build/main Packages
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
     release v=8.04,o=Ubuntu,a=hardy-updates,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
     release v=8.04,o=Ubuntu,a=hardy-updates,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
     release v=8.04,o=Ubuntu,a=hardy-updates,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
    release v=8.04,o=Ubuntu,a=hardy-updates,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
     release v=8.04,o=Ubuntu,a=hardy-security,l=Ubuntu,c=restricted
     origin security.ubuntu.com
 500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
     release v=8.04,o=Ubuntu,a=hardy-security,l=Ubuntu,c=multiverse
     origin security.ubuntu.com
 500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
     release v=8.04,o=Ubuntu,a=hardy-security,l=Ubuntu,c=main
     origin security.ubuntu.com
 500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
     release v=8.04,o=Ubuntu,a=hardy-security,l=Ubuntu,c=universe
     origin security.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
     release v=8.04,o=Ubuntu,a=hardy,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
     release v=8.04,o=Ubuntu,a=hardy,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
     release v=8.04,o=Ubuntu,a=hardy,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
     release v=8.04,o=Ubuntu,a=hardy,l=Ubuntu,c=main
     origin us.archive.ubuntu.com

Something somewhere must ring a bell with someone. Anyone?

---

### Post by darkaudit on 2008-07-16
Bump.

As it is right now, without manually setting something that *I don't know what is it yet*, apt-build install is a completely useless command out of the box. It's not setting the directory correctly in /etc/apt/sources.list.d (bug filed), and it will ignore the just built package in favor of the precompiled one *with the exact same version number*.

If I'm wrong that apt-build install is meant to install the just-compiled package like that, TELL ME. Someone, anyone. I've just been throwing up text here and in #ubuntu and #kubuntu and I haven't heard a word from *anyone* at all. They're not saying I'm right, they're not saying I'm wrong. NOTHING. Dead silence. I'm flying blind here and want this to work.

WHAT HAVE I MISSED??

---

### Post by darkaudit on 2008-07-16
I did a rebuild of pan, firefox, and xine-ui over the last couple of days, and installed those packages manually from /var/cache/apt-build/repository. Now update manager sees updates for those packages, when the remote version number is *exactly the same*, as confirmed by apt-cache policy.

Either something is broken, or I goofed. Which is it?

---

### Post by darkaudit on 2008-07-17
Bump. Again.

I've posted bug reports for apt-build [here]("https://bugs.launchpad.net/ubuntu/+source/apt-build"). If I was wrong or worse, certainly someone there would see the bug and respond accordingly. Nope. After 2 days I can't tell if anyone else has even looked at it.

I would understand if someone, anyone at all, let me know that I was taking the wrong path, but I've hit nothing but *silence* on all fronts. That's extremely frustrating.

---

### Post by darkaudit on 2008-07-17
Thanks to Planet Ubuntu and mouz! I found out about a bug-squashing day, and reported forthwith to #ubuntu-bugs. I reported the bugs I had on launchpad, and a fix was found, as shown [here]("https://bugs.launchpad.net/ubuntu/+source/apt-build/+bug/248787").

(/me puts RTFM sticker on top of monitor. The part about having the deb line at the top of sources.list was in /usr/share/doc/apt-build/README.Debian :p )

---

