---
title: "Update manager missing &quot;packages&quot;"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by nielsenworld on 2009-02-26
Hi, I accidently removed all packages from the update manager. 
I wanted the Xubuntu to only download Restricted drives, and i therefore unselected all the other 100+ updates. 

But when i run it again, it shows nothing. I clicked on the small icon in the top right hand corner, where i found the settings. But the icon doens't appear anymore :-(

Please help

BTW, I'm completyly new to Xubuntu!!

/Allan

---

### Post by Archmage on 2009-02-26
System -> Update-Manager

---

### Post by nielsenworld on 2009-02-26
> **Archmage said:**
> System -> Update-Manager

Yes, I did that, but it's just empty!

It shows nothing even though i click "Check"...

It's like the packages are gone.. It only checks for restricted drivers


And BTW, where do I find Restricted Drivers Manager?

---

### Post by nielsenworld on 2009-02-27
Anyone? :-)

---

### Post by Partyboi2 on 2009-02-27
Make sure you have updates enabled in Software Sources (System>Admin>Software Sources>Updates) check that the first 2 boxes are ticked.
Then try updating the package list from either synaptic or from the terminal
```
sudo apt-get update
```

---

