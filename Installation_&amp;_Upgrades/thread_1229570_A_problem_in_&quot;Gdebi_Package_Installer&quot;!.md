---
title: "A problem in &quot;Gdebi Package Installer&quot;!"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by Rami_961 on 2009-08-02
hello all, i have a problem in Gdebi Package Installer..about a month i had Ubuntu Jaunty
on my PC and when i wanted to install packages using Gdebi it will automatically give me what dependencies it required and download them from the net..
now i instaled Ubuntu Jaunty again but this time when i want to install packages it give me an error that dependencies is missing, so i have to download them manually..
how can i fix this (Sorry for my bad english)

---

### Post by oldos2er on 2009-08-02
Check System, Administration, Software Sources, and make sure all repositories are enabled.

---

### Post by Rami_961 on 2009-08-02
Thanks for the reply, but it didn't work still the same error:
'Error: Dependencies is now satisfiable:.....'

---

### Post by Partyboi2 on 2009-08-02
> **Rami_961 said:**
> Thanks for the reply, but it didn't work still the same error:
'Error: Dependencies is now satisfiable:.....'
What dependecies are not satistiable?

---

### Post by Rami_961 on 2009-08-03
I'm installing Kmess (it requires about 52), the first thing that popups is KDE-Runtime or something and when i downloaded it and reisntall Kmess some other dependencies is not satisfied it says too, and sometimes the dependencies that i download required it self another dependencies:confused:

---

### Post by Partyboi2 on 2009-08-03
If you have internet access with your Ubuntu machine you can open Synaptic (System>Admin>Synaptic) and search for the kmess package and install it, or from the terminal with
```
sudo apt-get install kmess
```If you machine is not connected to the internet you can use either [[COLOR=Blue]Keyrx [/COLOR]]("http://keryxproject.org/")or [[COLOR=Blue]Synaptic Package Download Script[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") to get kmess and all its dependencies from a machine that is connected to the Internet then take them back to your Ubuntu machine and install them.

---

### Post by Rami_961 on 2009-08-03
OK i'll do 
thanks for the help :)

---

