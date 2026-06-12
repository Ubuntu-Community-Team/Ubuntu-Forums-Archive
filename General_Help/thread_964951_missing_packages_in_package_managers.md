---
title: "missing packages in package managers"
date: 2008-10-31
forum: General Help
---

### Post by vievie on 2008-10-31
HI, all,

Just switch back to ubuntu after using MDV 1.5 years because of the super freeze feisty/gutsy bug. But it seems ubuntu is still not perfect.

I am missing a lot of general packages in adept or synaptics ,such as gimp. conky (universe packages), not to mention "weather plasmoids".

I can find gimp and conky in command line, why won't they show up in GUI?

Why ubuntu have less packages than mandriva now? I just tried mandriva 2009, they have a lot of extra stuff available in the repos, for example the weather plasmoid I mentioned above.

Shouldn't ubuntu be the most supported distribution?

btw: i am using AMD64 Kubuntu / 8.10

Thank you.

---

### Post by metalphreak on 2008-11-29
sudo update-apt-xapian-index 

This fixed all the missing package problems for me. phpsysinfo/lots of the apache packages etc were all missing until I did that.

EDIT: I'm using Ubuntu 8.10 AMD64 alternate install

---

