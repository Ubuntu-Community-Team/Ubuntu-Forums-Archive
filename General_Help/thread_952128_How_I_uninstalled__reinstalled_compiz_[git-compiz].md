---
title: "How I uninstalled / reinstalled compiz [git-compiz]"
date: 2008-10-18
forum: General Help
---

### Post by doktor_apokalypse on 2008-10-18
Note: these actions were performed on an hp dv5-1004nr laptop running Hardy amd64.

Compiz was driving me nuts today, so I decided to uninstall it  _completely_ and re-install to see if i could make it work like new again.  Three hours later and now I'm *mad*.  This shouldn't be so hard.  Take a break.  Drink some coffee, slow down and think.  There's got to be a way to do this right.  Well, hell if I could figure it out, so I cheated.  

I found a good script on the forums at compiz-fusion.org, called git-compiz.  It works with git, so make sure you have that installed:
```
 sudo aptitude install git-core
```
It solved the problem of uninstall and re-install all by itself.  So here's the code to get the script and a link to the original thread in case you want to check it out:

[list]
[*]Uninstall:
   [http://forum.compiz-fusion.org/showthread.php?t=8620](http://forum.compiz-fusion.org/showthread.php?t=8620)
   ```

   git clone git://anongit.compiz-fusion.org/users/omega/scripts
   cd scripts
   ./git-compiz --purge
   cd ..
   rm -rf scripts
   
```
[*]Install
    [http://forum.compiz-fusion.org/showthread.php?t=7744](http://forum.compiz-fusion.org/showthread.php?t=7744)
    ```
git clone git://anongit.compiz-fusion.org/users/omega/scripts
    cd scripts
    ./git-compiz --with-desktop=gnome
    
```
[/list]
This may give some errors when compiling, you can ignore *some* of the packages with no real consequences.
Also, replace the --with-desktop==gnome parameter with whatever you have.  I think the options were --with-desktop=all|gnome|kde|kde4.  Good luck.

---

### Post by loomsen on 2008-10-18
> 
git clone git://anongit.compiz-fusion.org/users/omega/scripts
   cd scripts
   ./git-compiz --purge


> 
git clone git://anongit.compiz-fusion.org/users/omega/scripts
    cd scripts
    ./git-compiz --with-desktop=gnome


Makes 

> 
cd ..
   rm -rf scripts

git clone git://anongit.compiz-fusion.org/users/omega/scripts
    cd scripts


kind of obsolete ^^

Anyway, I'll give it a try, thanks for pointing to it.

---

### Post by loomsen on 2008-10-18
Script didn't work for me, broke everything. Ended up purging and reinstalling from shames repo, which is the same version anyway, just fyi ^^

---

### Post by doktor_apokalypse on 2008-10-19
> **loomsen said:**
> Makes 



kind of obsolete ^^

Anyway, I'll give it a try, thanks for pointing to it.

Yeah you're right.  I just overlooked that, thanks.  

I wonder if you know what happened; that is, why did it break?  I'd like to know, just for curiosity's sake.  Worked for me, then again, this kind of business is always sort of hit-and-miss.

---

### Post by loomsen on 2008-10-19
Yep. Thats why I actually prefer using repositories in the meanwhile. It's way more comfortable. 

But as I just saw git's version is 0.81 already. I still got shames 0.79. 

Guess I'll search the compiz-fusion forum now a lil bit and then considering doing this thing again.

But I will for sure drop to a terminal this time prior to this whole magics :D

Tho I should not, as if it was real magic my freewins plugin suddenly started working today. Until now I had like a demo of it for 1 sec after initiating, then the window froze and I killed it.

But since today... charming.

Anyway, if it works now, it will work in case I fail again and fallback to 0.79 still. It should at least :)

---

### Post by loomsen on 2008-10-19
Alright, been there done that :D

Took some more time to make sure it will work this time tho.

So, what I did, and what I'd recommend (maybe you should integrate it to your postings above too), was, besides editing git-compiz and git-cpmpiz.conf how I like and need it, was running 
```

./git-compiz --build-dep --with-desktop=gnome

```

Well I did, this command returned it would love me for installing some_pkg, else it would just stop. Some sort of these pkgs google usually provides, so they did, I grabed and installed it.

Run the command above another time, and it worked almost perfect.
Failed to build 2 plugins/packages, vino or such and another one, but I won't miss them as I don't know what it was anyway.


Oh, btw, I nearly forgot, the only reason I actually installed git version was the ongoing implementation of googles protobuf code.
Looking forward to seeing future developement.


Just one thing which isn't that nice, my snow doesn't seem to work anymore... 

Dammit, started a script to call DBus events like snow and rain and such at song changes, new mails whatever yesterday. :/

---

