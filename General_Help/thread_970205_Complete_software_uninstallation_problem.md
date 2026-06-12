---
title: "Complete software uninstallation problem"
date: 2008-11-04
forum: General Help
---

### Post by Velvet Ghost on 2008-11-04
I installed the audacious media player a few days back. While installing I noted that 15 packages were downloaded and installed. I didn't note down the names of these packages. Now I have been able to run the media player of my choice (foobar2000) under wine, and don't need audacious any more. 

The Add/Remove program told me that additional programs depended on audacious so I needed to use the Synaptic package manager to remove it. I fired up Synaptic and marked the main package (audacious) for removal. It told me that audacious-plugins and audacious-plugins-extra would also be removed. But I clearly remember that many more packages were installed. Won't these packages now remain on my system if I go ahead with the removal?

Since this is the case with most software, won't my system become very bloated with unneeded packages over a period of time? Is there someway to remove a software COMPLETELY, or some kind of log file mentioning the packages that were installed, so that I can remove them all?

Sorry for the newbie question, thanks in advance.

---

### Post by mdurham on 2008-11-04
Run Synaptic, then look in File->History to see all the things that were installed at a certain time/date.

---

### Post by dcstar on 2008-11-04
> **Velvet Ghost said:**
> 
.........
Since this is the case with most software, won't my system become very bloated with unneeded packages over a period of time? Is there someway to remove a software COMPLETELY, or some kind of log file mentioning the packages that were installed, so that I can remove them all?

Sorry for the newbie question, thanks in advance.

Install the **gtkorphan** package.

---

### Post by Velvet Ghost on 2008-11-04
Thanks. I was able to completely remove audacious using the synaptic history and gtkorphan. Isn't it strange that Ubuntu doesn't properly provide something as basic as clean software uninstallation?

---

### Post by KeyserSoze93 on 2008-11-04
It does, with aptitude.

If open a terminal and run "sudo aptitude remove audacious", that should take care of it.

---

