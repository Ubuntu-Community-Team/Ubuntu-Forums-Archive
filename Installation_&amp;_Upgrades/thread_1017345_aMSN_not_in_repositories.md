---
title: "aMSN not in repositories??"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by higashi on 2008-12-21
I just got back to ubuntu after being stuck with opensuse. I installed 8.04 and waited an hour for all the upgrades to download. I restart my computer, go into add/remove to find that aMSN isn't there. I tried synaptic, it's not there either. There are actually a lot of programs i used to use that arent in my repositories anymore and it's really bugging me. 
I preffer SVN (and i like having the repositories so that i dont have to go downloading a billion plugins)

---

### Post by infamous-online on 2008-12-21
Hmm, have you tried downloading the program from [http://www.amsn-project.net/](http://www.amsn-project.net/) ? The required dependencies are listed here [http://www.amsn-project.net/wiki/FAQ#What_do_I_need_to_run_aMSN.3F](http://www.amsn-project.net/wiki/FAQ#What_do_I_need_to_run_aMSN.3F)

hope this helps. :cool:

---

### Post by Partyboi2 on 2008-12-21
> **higashi said:**
> I just got back to ubuntu after being stuck with opensuse. I installed 8.04 and waited an hour for all the upgrades to download. I restart my computer, go into add/remove to find that aMSN isn't there. I tried synaptic, it's not there either. There are actually a lot of programs i used to use that arent in my repositories anymore and it's really bugging me. 
I preffer SVN (and i like having the repositories so that i dont have to go downloading a billion plugins)
Have you got the "universe" repo enabled in Software Sources? (System>Admin>Software Sources)

---

### Post by higashi on 2008-12-21
> **Partyboi2 said:**
> Have you got the "universe" repo enabled in Software Sources? (System>Admin>Software Sources)

No i dont x]
How can i add it? i spent my morning trying to add this repository list thing that includes all these repositories with little success..
I found the apt line for the repositories but pretty much all the packages it downloads say "hit" or "fail" ..

---

### Post by Partyboi2 on 2008-12-21
> **higashi said:**
> No i dont x]
How can i add it? i spent my morning trying to add this repository list thing that includes all these repositories with little success..
I found the apt line for the repositories but pretty much all the packages it downloads say "hit" or "fail" ..
Open up Software Sources by going to System>Admin>Software Sources, on the first tab then tick if it is not already ticked the "community-maintained open source software (universe)" then close Software Sources and try install amsn again.

---

### Post by higashi on 2008-12-21
> **Partyboi2 said:**
> Open up Software Sources by going to System>Admin>Software Sources, on the first tab then tick if it is not already ticked the "community-maintained open source software (universe)" then close Software Sources and try install amsn again.

Thanks, i installed amsn, but whenever i try to run it, it gives me this pop up saying 

>  Loading TkCximage failed. This module is needed to run aMSN. Please compile aMSN first, instructions on how to compile are located in the file INSTALL

Also, i've tried adding repositories for other programs that i wanted to try, and i got the same results as the amsn repositories (either hit or failed packages). Is it something wrong with my ubuntu?

---

### Post by Partyboi2 on 2008-12-21
> Thanks, i installed amsn, but whenever i try to run it, it gives me this pop up saying 

open a terminal and try changing the default  tcl/tk  from 8.4 to 8.5
```
 sudo update-alternatives --config wish
```can you also post the output to
```
sudo apt-get update
```

---

### Post by higashi on 2008-12-22
i entered the command but it only gave me 2 options:

> There are 2 alternatives which provide `wish'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/wish8.4
 +        2    /usr/bin/wish-default

I tried both and neither of them worked.

---

### Post by infamous-online on 2008-12-22
you need to install all of the tclx packages from either apt-get or synaptic! I preferrably like to use synaptic as i get to see what all i need for any particular package.

---

### Post by higashi on 2008-12-22
kay i did that, i now have wish 8.5 , im using it, but i still get the pop up.
i tried running ./configure , but i now get the error 

"checking for jpeg_CreateDecompress in -ljpeg... no
configure: error: libjpeg is required"

Once again, i can't find libjpeg in my repositories. :\

---

### Post by Partyboi2 on 2008-12-23
> **higashi said:**
> kay i did that, i now have wish 8.5 , im using it, but i still get the pop up.
i tried running ./configure , but i now get the error 

"checking for jpeg_CreateDecompress in -ljpeg... no
configure: error: libjpeg is required"

Once again, i can't find libjpeg in my repositories. :\
Try installing the libjpeg62-dev package.
[B]
[/B]

---

### Post by higashi on 2008-12-23
Urrgh, i did, and i'm still getting the same error. >.<
Sorry if im frustrating you guys..

Also, i downloaded this .deb package for amsn svn (thats what i really wanted in the first place but i didnt want to sound to picky..)  but when i open the package installer, where it says 'status' , i get this:

"Error: Dependency is not satisfiable: libgstreamer0.10-0"

At this point, i really dont care which version i end up with, so whatever you feel like helping me with would be greatly appreciated.

---

### Post by Partyboi2 on 2008-12-23
> **higashi said:**
> Urrgh, i did, and i'm still getting the same error. >.<
Sorry if im frustrating you guys..

Also, i downloaded this .deb package for amsn svn (thats what i really wanted in the first place but i didnt want to sound to picky..)  but when i open the package installer, where it says 'status' , i get this:

"Error: Dependency is not satisfiable: libgstreamer0.10-0"

At this point, i really dont care which version i end up with, so whatever you feel like helping me with would be greatly appreciated.
The easiest way is to install the one in the ubuntu repos either by synaptic or from a terminal
```
sudo apt-get install amsn
``` However if you want to learn a little you can go with the deb you downloaded and install the dependencies manually.

When you see a dependency error like that it means that you need to install the package mentioned. So install libgstreamer0.10-0 from synaptic or from terminal
```
sudo apt-get install libgstreamer0.10-0 
```

---

### Post by higashi on 2008-12-23
I've tried both those already, and these are the results:

when i install from repositories, i get that pop up i mentioned earlier about the failure of loading TkCximage.  

when i tried installing libgstreamer via apt-get, i get this: 

libgstreamer0.10-0 is already the newest version.

---

