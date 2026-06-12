---
title: "[SOLVED] How do I remove a path from $PATH permenantly"
date: 2008-08-12
forum: General Help
---

### Post by Subban on 2008-08-12
Many moons ago I added ~/bin to my $path for some of my scripts I have written to run easily. I can't recall how it was done (I think it was by doing export PATH=~/bin:$PATH) but I have just now noticed that ~/bin is the first entry in $PATH. Obvoiusly this is less than satisfactory as any commands in that path will be used prior to ones in such places as /bin and /usr/bin etc and could potentially be insecure.

My problem is that I cannot permanently remove /home/subbass/bin from $PATH though. I have tried 'export' and when I fire up a new shell the path has returned. It is not being set in ~/.bashrc and I do not have a ~/.bash_profile

Any help is appreciated.

---

### Post by nazish on 2008-08-12
hi subban,
if you dont have the .bashrc file then I think you need to check your /etc/profile file.
 
or else you can create your own .bashrc file. to do this type the following in your terminal
> 
cat > ~/.bashrc << "EOF"
set +h
umask 022
LC_ALL=POSIX
PATH=/bin:/usr/bin
export LC_ALL PATH
EOF

dont forget to change the "PATH" variable to point to entries of your choice. separate entries using the " : "
 
then run this command to activate this new .bashrc file
 
> source ~/.bash_profile

---

### Post by kpkeerthi on 2008-08-12
Perhaps in /etc/profile ?

---

### Post by Subban on 2008-08-12
Thanks for taking time to reply, I do have a ~/.bashrc file.

I do not have a ~/.bash_profile

.bashrc doesn't contain anything that adds ~/bin to my $PATH, and if I try and export PATH=etcetc without the /home/subbass/bin then it simply comes back next shell I open. 

I don't really want to remove it permanently even, just get rid of it from the front of the $PATH and put it at the end so its safer.

Any other thoughts ?

---

### Post by nazish on 2008-08-12
did you check the /etc/profile file ??

---

### Post by Subban on 2008-08-12
Sorry I forgot to say.

No there is nothing in /etc/profile fiddling with $PATH.
Also, nothing in /etc/bash.bashrc

---

### Post by dexter.deepak on 2008-08-12
check the ~/.profile file

---

### Post by Subban on 2008-08-12
> **dexter.deepak said:**
> check the ~/.profile file

Bingo!

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

By my estimation if I just flip 
```
PATH=~/bin:"${PATH}"
```

into 
```
PATH="${PATH}":~/bin
```

I will get the result required.

Thank you to everyone who helped and especially dexter.deepak for the solution.

---

### Post by nazish on 2008-08-12
gr8 to see that someone always knows the answer and someone is always there to help this is what FOSS is all about. I simply luv the community.

---

