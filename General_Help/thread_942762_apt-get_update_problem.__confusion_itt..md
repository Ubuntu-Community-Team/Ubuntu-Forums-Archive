---
title: "apt-get update problem.  confusion itt."
date: 2008-10-09
forum: General Help
---

### Post by ex.hav0k on 2008-10-09
I've been trying to install mplayer but i keep getting an error about some of the dependencies not being available to install, so i tried running
```
sudo apt-get update
```

and i get this:

```
Failed to fetch http://packages.medibuntu.org/dists/hardy/Release  rename failed, No such file or directory (/var/lib/apt/lists/partial/packages.medibuntu.org_dists_hardy_Release -> /var/lib/apt/lists/packages.medibuntu.org_dists_hardy_Release).
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2  rename failed, No such file or directory (/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages.decomp -> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages).
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2  rename failed, No such file or directory (/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_hardy_restricted_source_Sources.decomp -> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_restricted_source_Sources).
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2  rename failed, No such file or directory (/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_source_Sources.decomp -> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_source_Sources).
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2  rename failed, No such file or directory (/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages.decomp -> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages).
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2  rename failed, No such file or directory (/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages.decomp -> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages).
Some index files failed to download, they have been ignored, or old ones used instead.
```

I'm not an expert so this has me a bit confused as I've never run across this problem before.

I tried running
```
sudo apt-get clean
sudo apt-get update
```

but that didn't work.

if anyone knows what should happen now in my path for fixing my ubuntu system, post now or forever let me rot with this inconvenient mess.  :confused:

---

### Post by phidia on 2008-10-09
That "Failed to fetch" message for each of your repos is a clue.
Either the repositories are busy or your internet connection wasn't working.

Make sure you are connected and try the update command again.

---

### Post by Het Irv on 2008-10-09
You can rot if you really want to, but for right now try switching mirrors.

System-> Administration -> Software Sources
Change what ever is in the "Download From:" box to a mirror near you.

---

### Post by ex.hav0k on 2008-10-11
i changed the source under synamptic (because im using fluxbox and i didn't add software source to my menu) but it seems to work now.  it was just set on United States Server but i choose other and found a mirror close to me.

thanks for the help fellas :)

---

