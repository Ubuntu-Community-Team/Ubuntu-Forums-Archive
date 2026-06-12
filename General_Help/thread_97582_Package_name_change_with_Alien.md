---
title: "Package name change with Alien ?"
date: 2005-12-01
forum: General Help
---

### Post by Bachstelze on 2005-12-01
I'm using alien to convert a Fedora VLC .rpm build into a .deb. Everything works fine but when I install the .deb file, the name of the installed package is videolan-client, so I cannot install the wxvlc frontend. Is there a way to "rename" my package to vlc ?

---

### Post by Bachstelze on 2005-12-01
Bump :d

---

### Post by tlc on 2005-12-01
Can you not simply rename it?

"mv videolan-client vlc" in a console or do it with whatever file browser you use.

Aplogies if I'm missing the point or being dense...

---

### Post by Bachstelze on 2005-12-01
[QUOTE=tlc]Can you not simply rename it?

"mv videolan-client vlc" in a console or do it with whatever file browser you use.

Aplogies if I'm missing the point or being dense...[/QUOTE]

I should have made myself clearer. The point is that when I want to to run the "videolan-lient" package (the command to run it is still 'vlc'), it doesn't want to run, complaining that wvlc is not istalled. Fair enough, I go into Synaptic ant try to install wxvlc but it wants to install the vlc package to resolve the dependencies. And of course that fails, because both packages use the same files. So my question is : how can I make Synaptic use my "videolan-client" package instead of the "vlc" one ?

---

### Post by tlc on 2005-12-01
Rename/delete your existing videolan-client, go ahead and let synaptic install its version, delete it, and rename back or reinstall your version?

Bear in mind though that I am an idiot... ;)

edit: what's wrong with the vlc that synaptic installs anyway?

---

### Post by Bandit on 2005-12-01
very simple..
"$ alien thefilename.rpm"
It will spit out the deb for you.
Bare in mind.. They somtimes want install after you convert them becuase they are still designed for diferent distros..
Cheers,
Joey

---

### Post by Bachstelze on 2005-12-01
I think you didn't read carefully. The package works fine, all I want is Synaptic to use it insead of the repo's vlc to solve wxvlc's dependencies.

---

### Post by Bandit on 2005-12-01
[QUOTE=HymnToLife]I think you didn't read carefully. The package works fine, all I want is Synaptic to use it insead of the repo's vlc to solve wxvlc's dependencies.[/QUOTE]
My bad.. I have ADD...
Make a directory in your home folder, then add that location to /etc/apt/sources.list
Then save and run sudo apt-get upate.
It **should** see it as a newer file and try to use the newest version.
Hope this is the info you was looking for :)
Cheers,
Joey

---

### Post by Bachstelze on 2005-12-01
[QUOTE=Bandit]My bad.. I have ADD...
Make a directory in your home folder, then add that location to /etc/apt/sources.list
Then save and run sudo apt-get upate.
It **should** see it as a newer file and try to use the newest version.
Hope this is the info you was looking for :)
Cheers,
Joey[/QUOTE]

Yeah, that's what I want. BUT the problem is that the package I want to install is named "videolan-client" instead of "vlc", so Synaptic just sees another package, though it's the same app. So I wanted to know if there is a way to change the name synaptic uses for a pakage. (No, changing the package filename doesn't work)

---

### Post by Bandit on 2005-12-01
You will have to use dpkg and extract the pack and then edit the control file found in the folder DEBIAN directory within the deb. Change the name to from videolan-lient to vlc and then rebuild the package.
read this as well it has more info then I can explain.
man dpkg-deb
Cheers,
Joey

---

### Post by Bachstelze on 2005-12-01
Thanks, I finally got it working the way I want :)

---

