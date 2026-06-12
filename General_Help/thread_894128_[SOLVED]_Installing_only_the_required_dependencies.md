---
title: "[SOLVED] Installing only the required dependencies with Aptitude"
date: 2008-08-19
forum: General Help
---

### Post by dstein on 2008-08-19
I am trying to install Amarok using Aptitude. Using Synaptic, I see that the Amarok package suggests and recommends a bunch of files I don't want (KDE applications). I know that Qt and other packages are required, but is there any way to use Aptitude to install Amarok without automatically installing the suggested and recommended packages? Thanks.

---

### Post by jualin on 2008-08-19
Try running > sudo apt-get -f install amarokHowever without the reccomended dependencies Amarok may not work.

---

### Post by IvoLucien on 2008-08-19
aptitude's [FONT="Courier New"]**--without-recommends**[/FONT] option should do at least some of what you need.

[FONT="Courier New"]sudo aptitude --without-recommends install amarok[/FONT]

I ran a simulated amarok install on my machine and got about 1/3rd less cruft with that option, compared to a plain install.

You could also use the -d option to just download the various packages, but that's hardly better than doing the whole thing manually, and can be more error prone.

---

### Post by dstein on 2008-08-19
Thanks, '--without-recommends' worked for me. I had another minor problem that was resolved after a quick search on the internet. I had to change the owner of my ~/.kde folder from root to myself.

It seems that some of my album covers are not viewable in Amarok. They worked fine in iTunes and on my ipod. Any ideas why they would not be viewable in Amarok. Also, in iTunes, there is a may to mark a track/album's ID3 tag as 'compilation'. Is there any way to do this using Amarok or any other Linux utilities. I ask so that they can be added to the 'compilations' folder after being transferred to my ipod.

Thanks again.

---

### Post by IvoLucien on 2008-08-20
Sadly I know nothing of Amarok. You'll probably get the best response by posting this as a new thread. Best of luck, and thanks for the thanks.  ^_^

---

