---
title: "Mysterious Broken Dependancies!"
date: 2008-09-04
forum: General Help
---

### Post by jayde_drag0n on 2008-09-04
rather than posting the typical question.. which will leave me to repeat a lot of things.. i will post the conversation i had about this problem.. so you can see everything that was done.. results and pastebins from questions

so here you go!

Jayde: i've got a broken package, but i can't seem to repair it
Leo: What did you break?
Jayde: "The following packages have unmet dependencies:
  libpq5: Depends: libldap2 (>= 2.1.17-1) but it is not installable
E: Broken packages
"
Leo: Sudo apt-get install -f.
Leo: See if that works.
Jayde: already did that "sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
"
Leo: What were you doing when you got that unmet dependencies error?
Jayde: well i've been staring at the update manager for a while now and for that while libpq5 has been in there to upgrade but has been uncheckable.. so i decided to do it thru terminal this time.. and thats what i got
Leo: Try this: sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y 
Leo: That should upgrade every package there is to upgrade.
Jayde: and i just now tried to go thru synaptics for libldap2 and found this error "Package libldap2 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list"
Jayde: since it said there was a dependancy for libpq5 for it
Leo: Do you have non official repos in your sources.list?
Jayde: in third-party software in the repos under synaptics?
Leo: Yeah.
Leo: I guess... I never use synaptics.
Jayde: do you want me to list what i have checked or take a screenshot for you?
Jayde: or do it thru terminal and use pastebin?
Leo: Pastebin your /etc/apt/sources.list.
Leo: What if you try manually installing libpq5 ?
Jayde: [http://pastebin.com/m485c71be](http://pastebin.com/m485c71be)
Jayde: using terminal.. thats what i did.. sudo apt-get install libpq5
Jayde: i'll pastebin the whole response
Leo: Ok.
Leo: What are these for?
Leo: Deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy maindeb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy maindeb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main universe.
Jayde: [http://pastebin.com/d1cea340a](http://pastebin.com/d1cea340a)
Jayde: LOL i don't remember.. somethingor other i installed or tried to install at some point
Jayde: i follow directions really well.. problem is i don't usually know what said directions do or mean LOL
Leo: Those repos might be interfering with your packages.
Leo: Checking...
Jayde: ahHA blognux is for easycam
Leo: I'm more interested in the launchpad one.
Leo: Usually those are packages somebody is proposing.
Jayde: i'm trying to see what it is. but i can't find any names of stuff
Leo: Do apt-cache seach libldap.
Jayde: just packages and sources
Leo: What version do you get when you search for libldap?
Jayde: "libldap-ocaml-dev - LDAP bindings for OCaml
libldap-ruby1.8 - OpenLDAP library binding for Ruby 1.8
libldap-2.4-2 - OpenLDAP libraries
libldap-2.4-2-dbg - Debugging information for OpenLDAP libraries
libldap2-dev - OpenLDAP development libraries
'
Leo:  sudo apt-get install libldap-2.4-2 
Jayde: "libldap-2.4-2 is already the newest version.
libldap-2.4-2 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
"
Leo: That's so weird.
Leo:  libpq5: Depends: libldap2 (>= 2.1.17-1)
Jayde: OH okay that launchpad is for screenlets
Leo: But you have libldap-2.4-2 already installed.
Leo: 2.4-2 >= 2.1.17-1
Leo: That doesn't make any sense.
Jayde: i'm famous for weird problems
Leo: Haha.
Jayde: i have a freaked out mouse problem i've never been able to solve
Leo: This problem is beyond me

---

### Post by zvacet on 2008-09-04
Try in **synaptic>edit tab>fix broken packages**.You can look [here]("http://packages.ubuntu.com/hardy/libpq5") to see all dependencies for libpq5.Check that you have them installed.

---

### Post by jayde_drag0n on 2008-09-04
tried that.. nothing showed up or happened when i clicked "fix broken packages"  when i tried to organize by broken packages.. again nothing happened.   i went to [http://packages.ubuntu.com/hardy/libpq5](http://packages.ubuntu.com/hardy/libpq5)  and downloaded the deb directly and tried to install it.. i got "Error: a later version is already installed"

---

### Post by jayde_drag0n on 2008-09-04
also went thru and directly tried to install each file that was associated..

"jayde@MASTER:~$ sudo apt-get install libc6
[sudo] password for jayde: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jayde@MASTER:~$ sudo apt-get install libcomerr2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcomerr2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jayde@MASTER:~$ sudo apt-get install libkrb53
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libkrb53 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jayde@MASTER:~$ sudo apt-get install libssl0.9.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libssl0.9.8 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jayde@MASTER:~$ sudo apt-get install libldap-2.4-2
Reading package lists... Done
Building dependency tree        
Reading state information... Done
libldap-2.4-2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by zvacet on 2008-09-04
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by jayde_drag0n on 2008-09-04
still no "2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded."

the 1 not upgraded.. is libpq5

---

### Post by jayde_drag0n on 2008-09-04
"The following packages have been kept back:
  libpq5
The following packages will be upgraded:
  language-pack-en language-pack-gnome-en
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded."

---

### Post by David Oxland on 2008-09-04
I'm in a similar situation; mine came from an attempt to install Amarok through Synaptic and the libpq5 came through shown as "libpq5 will not be installed".
Through a different thread on these forums I read to try aptitude install Amarok and it did install then.
Today when updates came libpq5 was among 14 offered but the box wouldn't allow itself to be checked while the others did.

---

### Post by stoneage on 2008-09-04
Just a shot in the dark, but try setting the manually installed one to Automatically installed; I think it is under 'Package' in Synaptic.

```
Leo: sudo apt-get install libldap-2.4-2
Jayde: "libldap-2.4-2 is already the newest version.
libldap-2.4-2 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by jayde_drag0n on 2008-09-04
i think i may have figured out whats going on with libpq5  but i need someone knowledgable to tell me wether i'm on the right path.. the libpq5 is at a higher version than what is currently available.. which is why it can't upgrade.. because its ALREADY upgraded

"installed version 8.3.3-0"
"latest version 8.3.3-1"

if i try to "force" it under packages.. it says  "to be downgraded"

so what i need to know... should i force the downgrade.. or leave it be, and is that my answer as to why it keeps showing up in the update thingy and can't be checked?

---

### Post by David Oxland on 2008-09-04
I hope you don't mind me piggybacking here.

I went to Synaptic and see that after my Amarok install, libpq5 shows 
as present with a yellow star indicating that it can be upgraded, I think.  Right clicking offers to upgrade or remove or remove completely.  


Selecting up grade brings the following.

Don't know where to go from here

---

### Post by Cheesehead on 2008-09-04
> **jayde_drag0n said:**
> the libpq5 is at a higher version than what is currently available.. which is why it can't upgrade.. because its ALREADY upgraded

"installed version 8.3.3-0"
"latest version 8.3.3-1"

if i try to "force" it under packages.. it says  "to be downgraded"


Your assessment is correct. It's already upgraded.

If you wait until the update is available through Update Manager then all the dependencies will be satisfied and you will avoid borking your system in this way.

If you ride the bleeding edge of 'the latest version' of your favorite apps, this is the risk you run. If you want a 'stable' system, you must be willing to wait until all the pieces are in place for an upgrade.

Your Options:
1) If your system is working just fine, then wait six short weeks (or so) for 8.10, and do your normal dist-upgrade then.

2) If your system is unusable, then downgrade the package.

---

### Post by g1nsu on 2008-09-15
I had a similar problem upgrading libpq5 and it was keeping me from upgrading to the QT4 libs. libpq5 has a dependency on libldap2. If you are using Hardy and try to install libldap2, it says it has been replaced by slapd and libldap2.4-2. Installing slapd and libldap2.4-2 does not satisfy the dependency. Simply enough, I grabbed the libldap2 package from the Gutsy repository ( [http://packages.ubuntu.com/gutsy/libldap2](http://packages.ubuntu.com/gutsy/libldap2) ), it's not available in the backports repo, installed it and then I was able to upgrade libpq5 and the QT4 libs.

I know this is a bit different from the forum post but it's the first place I found when trying to solve my issue. Hopefully this helps someone.

---

### Post by katatonic289 on 2008-09-24
> **g1nsu said:**
> I had a similar problem upgrading libpq5 and it was keeping me from upgrading to the QT4 libs. libpq5 has a dependency on libldap2. If you are using Hardy and try to install libldap2, it says it has been replaced by slapd and libldap2.4-2. Installing slapd and libldap2.4-2 does not satisfy the dependency. Simply enough, I grabbed the libldap2 package from the Gutsy repository ( [http://packages.ubuntu.com/gutsy/libldap2](http://packages.ubuntu.com/gutsy/libldap2) ), it's not available in the backports repo, installed it and then I was able to upgrade libpq5 and the QT4 libs.

I know this is a bit different from the forum post but it's the first place I found when trying to solve my issue. Hopefully this helps someone.
You, sir, are a legend. This Ubuntu newbie bows down to you.
=D>

---

