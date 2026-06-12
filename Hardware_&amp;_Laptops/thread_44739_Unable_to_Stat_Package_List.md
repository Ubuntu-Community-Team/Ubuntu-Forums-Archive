---
title: "Unable to Stat Package List"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by pace_tua on 2005-06-27
I added extra repositories to my sources.list using the following instructions: [http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")

[color=Sienna][color=Black]Well, now I am recieving the following error when opening Synaptic:[/color]
[/color] ```
 W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
``` [color=Sienna]

[color=Black]And when I reload:[/color]
 [/color][]("http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:") ```
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:]("http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:") Sub-process bzip2 returned an error code (2)
``` [color=Sienna]
 
 [color=Black]Followed by:[/color]
[/color] ```
 W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com")
W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
``` [color=Sienna]
 
 [color=Black]Am I guessing right that this repository does not exsist anymore? :smile:[/color]
[/color]

---

### Post by dialate on 2005-06-27
Did you run "sudo apt-get update" in a terminal after you changed your repositories?

---

### Post by pace_tua on 2005-06-27
Weird. I just went back and re-copied everything, and now it works fine. I must have mispelled something the first time...

:???:

Thanks anyways.

---

