---
title: "LaTeX package manager?"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by guyomarj on 2005-12-20
Hi,

Is there a front-end (GUI or text based) to manage LaTeX packages? Maybe something like "SynapTeX" :D

---

### Post by natman on 2005-12-20
hi, i am newbi but i use a program called KILE to write my latex stuff up in ubuntu, Its kinda like " WinEDT" a nice little GUI to make LaTeX that little easier.
> sudo apt-get install kile

I then go in kile and run the status wizard and see what type of packages i am missing.

---

### Post by guyomarj on 2005-12-20
Thx natman, I use Kile too and I like it.

I didn't find the "status wizard". I found a "System Check..." option under the "Settings" menu. Is that what you talk about?

---

### Post by natman on 2005-12-22
[QUOTE=guyomarj]Thx natman, I use Kile too and I like it.

I didn't find the "status wizard". I found a "System Check..." option under the "Settings" menu. Is that what you talk about?[/QUOTE]


Sorry your right, i meant the system check, run this and write down the name of all the things you are missing.
then close kile, go to synaptic and in the add stuff bit, just type the words ( that you wrote down ) in the search box, the get ubuntu to install ALL of the results ( it will take a while, and you probably will end up downloading some unwanted stuff ) but you should get what you want.

---

### Post by 18nikko on 2006-01-15
Hi,
I think guyomarj means packages that are on ctan but not in any ubuntu or debian repository. There are a great many packages like that. Maybe if some one 
would do something for linux tetex like miktex that would be nifty.

Nicholas

---

### Post by guyomarj on 2006-01-16
That's exactly what I meant :D Just a "tex-get" app like apt-get would be very nice...

---

### Post by dada1958 on 2006-02-01
[MiKTeX Tools]("http://www.miktex.org/unx/") is also available for Unix-like operating systems, though beta en tar.gz only at this moment.

---

### Post by frisket on 2006-11-19
There is no global TeX package manager for Unix versions of TeX.

The very neat one which comes built into the MIKTeX distro for Windows has been ported to Unix but is still experimental (but I believe it works OK).

The problems are the unbelievable tangle of non-standard directories used in some older TeX installations ](*,)  See ongoing discussions on this on comp.text.tex

In any case, I'm about to trash the horrible Debian implementation of tetex and install TeX Live 2005 from TUG's CD (or maybe burn the impending 2006 beta ISO). It means some pain with Ubuntu dependencies, but it means a clean, working, complete TeX/LaTeX.

Maybe one day someone will add to apt-get a feature to specify "dependency satisfied by external installation" :-D 

///Peter

---

