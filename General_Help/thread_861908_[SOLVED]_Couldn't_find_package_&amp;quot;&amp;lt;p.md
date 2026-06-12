---
title: "[SOLVED] Couldn't find package &amp;quot;&amp;lt;program&amp;gt;&amp;quot;"
date: 2008-07-17
forum: General Help
---

### Post by Shunsuke_01 on 2008-07-17
Whenever I try to install a program from the terminal, it tells me it cannot find the package. Also, if I search for it in Synaptic Package Manager it doesn't find anything. 

This happens with numerous programs I've tried to install such as VLC, Amarok, Grip etc.

I have completely reinstalled Ubuntu, so I think there is something I'm missing.


Any help would be appreciated.

---

### Post by Rocket2DMn on 2008-07-17
Have you enabled the correcty repos in System->Administration->Software Sources ?
You can also run
```
sudo apt-get update
```
to download the lists of the available packages.  You may need to enable the universe/multiverse repos to get the pckages you are looking for.

---

### Post by jonian_g on 2008-07-17
Go to Synaptic package manager and on the window that appears click Settings>Repositories and on the first tab check all the checkboxes and uncheck "Cdrom with Ubuntu....". On the second tab check the two checkboxes. Press close and then refresh add you will see the programs you want.

---

### Post by Shunsuke_01 on 2008-07-17
> **Rocket2DMn said:**
> Have you enabled the correcty repos in System->Administration->Software Sources ?
You can also run
```
sudo apt-get update
```
to download the lists of the available packages.  You may need to enable the universe/multiverse repos to get the pckages you are looking for.

If you mean the options under the "Ubuntu Software" tab (System > Administration > Software Sources) then yes, I've got all of them enabled. I'm not sure if I've done it right though, so please explain what should have been done.

OK, I'm currently updating the things you told me to. I'll be back with my results. :)

Edit: OK, thanks. That seems to have fixed the problem. ^_^

---

### Post by jonian_g on 2008-07-17
Nice... Don't forget to mark the thread as [SOLVED].:)

EDIT: Didn't saw you already did.

---

