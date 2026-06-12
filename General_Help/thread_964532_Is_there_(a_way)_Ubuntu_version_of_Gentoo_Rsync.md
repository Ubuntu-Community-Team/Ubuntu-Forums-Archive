---
title: "Is there (a way) Ubuntu version of Gentoo Rsync??"
date: 2008-10-31
forum: General Help
---

### Post by alienprdkt on 2008-10-31
Many users run Gentoo on several machines and need to sync the portage trees on all of them. Using public mirrors is simply a waste of bandwidth at both ends. Syncing only one machine against a public mirror and all others against that computer would save resources on Gentoo mirrors and save users' bandwidth. 
  The same holds true for organizations who would like to control the rsync mirror their servers and workstations sync against. Of course, they usually also want to save on bandwidth and traffic costs. 



Is there a way to do this on Ubuntu? 

and if so what is it called and is there a how to or walk through on how to do it?

---

### Post by Aearenda on 2008-10-31
I use apt-cacher for this - [http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)

You can also create your own repository mirror. But apt-cacher doesn't bring down stuff you don't use, at the price of a delay on the first use of things you do use!

EDIT: I'm assuming here that you don't mean, you want to create a Gentoo portage tree on an Ubuntu machine, but rather, you want a crowd of Ubuntu machines to download their changes just once as you have done with Gentoo.

---

### Post by alienprdkt on 2008-10-31
thanks, pretty sure this is what I wanted:D also thanx for the fast reply!! this will give me something to do tomorrow. 
I have 4 Ubuntu pcs so I will save them Ubuntu servers (and myself) a little bit anyways.

---

