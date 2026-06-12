---
title: "install 2 versions of the same lib"
date: 2008-09-08
forum: General Help
---

### Post by wbloos on 2008-09-08
Hi,

Is it possible to install two versions of the same library?
For example GEOS 2.2.3 and GEOS 3.0.0 ?

thx

WBL

---

### Post by zvacet on 2008-09-08
That is not a problem.problem is (if that is a real problem) that you can not run both if that is what you have in mind.You will allways run newer version.

---

### Post by wbloos on 2008-09-09
So how do i do it?
Do i have to compile from source? I don't think apt-get will allow me to install 2 different versions of the same lib..
Then (if i have to compile from source) i'd need to install double versions of the dependencies too, which in turn have their own dependencies. All in double versions, so no apt-get. 

Is that true?


Running both IS what i had in mind (why else install both). As far as i know i can run a different version of an executable by specifying the correct path. I guess at compile time i can't do that for the libraries to be used. All the latest versions would be used, so i'd have to install or compile the oldest version first. Then i can use both libs because i compiled them into the executables.

Is that right?

thanks!
WBL

---

### Post by wbloos on 2008-10-06
any thoughts on that?

---

### Post by Calmatory on 2008-10-06
Shouldn't it be possible if the package name and files are not the same?

E.g. 
libexample-2.7.8-4
libexample-3.0.0-rc1

Shouldn't that be possible if both packages are found and dependencies or filenames are not conflicting?

---

