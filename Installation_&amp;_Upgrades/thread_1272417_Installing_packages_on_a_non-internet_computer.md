---
title: "Installing packages on a non-internet computer"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by Anthoni Gardner on 2009-09-22
Hello,

I have recently made the switch over to Ubuntu and loving every minute of it.
A friend of mine is also wanting to switch over because I have done nothing but rave about the new OS I am using. 

However he does not have an Internet connection so he can not do auto-upgrades etc. This means that is mainly up to me to download the stuff that he requires. So far I am doing the following
sudo apt-get -d <package-name> and then copying the packages over to a USB stick then installing that way. Thing is, this looks to see if I have the pre-installed packages first and if so does not download them, however he might have them installed on his computer etc.

Is there a better way to do this?

Regards
Anthoni

---

### Post by etnlIcarus on 2009-09-22
Somewhere, there's about 25GB of .isos, containing the complete Ubuntu repositories. Unfortunately, I can't remember what it's called. The most sensible option would be to either take a net connection to him or bring his PC to a net connection.

Edit: [This might be it](ftp://kambing.ui.edu/pub/ubuntu-repository/jaunty/).

---

### Post by AnimeFreak on 2009-09-22
> **etnlIcarus said:**
> The most sensible option would be to either take a net connection to him or bring his PC to a net connection.

or u could look online for the packs that your friend wants or needs and down load them that way thats what i did and it took no time till my friend was up to the same as me

---

### Post by etnlIcarus on 2009-09-22
> **Anthoni Gardner said:**
> So far I am doing the following
sudo apt-get -d <package-name> and then copying the packages over to a USB stick then installing that way. Thing is, this looks to see if I have the pre-installed packages first and if so does not download them, however he might have them installed on his computer etc.

Is there a better way to do this?

> **AnimeFreak said:**
> or u could look online for the packs that your friend wants or needs and down load them that way thats what i did and it took no time till my friend was up to the same as me

"The message you have entered is too short. Please lengthen your message to at least 1 characters."

---

### Post by Partyboi2 on 2009-09-22
Hi, you can use one of these to install the packages on the offline machine. [[COLOR=Blue]aptoncd[/COLOR]]("http://aptoncd.sourceforge.net/") , [[COLOR=Blue]Keryx[/COLOR]]("http://keryxproject.org/") , [[COLOR=Blue]Synaptic Package Manager Download Script[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript").

---

### Post by konqueror7 on 2009-09-22
APTonCD would still require you to install the packages, so not an option. Keryx seems to be the most flexible and appropriate tool for the job.

---

### Post by Anthoni Gardner on 2009-09-23
> **etnlIcarus said:**
> Somewhere, there's about 25GB of .isos, containing the complete Ubuntu repositories. Unfortunately, I can't remember what it's called. The most sensible option would be to either take a net connection to him or bring his PC to a net connection.

Edit: [This might be it]("ftp://kambing.ui.edu/pub/ubuntu-repository/jaunty/").

Thank you, between that and the Keryx Project it seems like I will have the full repository (more or less) to help him install what he needs.

Taking his computer to an internet line is a no-go unfortunately, as don't fancy lugging around his tower.

Thanks for the help, much appreciated.

Regards
Anthoni

---

