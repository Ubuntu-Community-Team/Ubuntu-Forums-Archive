---
title: "problem installing java..."
date: 2008-09-23
forum: General Help
---

### Post by drudogg on 2008-09-23
i don't really have any idea what i am doing.  i have tried teh procedure that is given with the jre bin file... but the su command comes back with authentication failure. not sure why. i was going oto install it to the default directory that sun recommended, but can't get past permissions.

also, how do i go about making a new directory in a protected folder?

8.04

---

### Post by fooman on 2008-09-23
what is the exact "su command" that you are trying to run?

instead of su try:

```
sudo <followed by whatever command>
```

hit enter, then type your password when prompted.

to create a folder,  you can use the mkdir command:

```
sudo mkdir <foldername>
```

as an example...to create a folder in your home directory:

```
sudo mkdir /home/<foldername>
```

hope that is of some help.

---

### Post by oilchangeguy on 2008-09-23
why not just use add/remove, or synaptic package manager?

---

### Post by drudogg on 2008-09-24
> **oilchangeguy said:**
> why not just use add/remove, or synaptic package manager?

if it was that easy, then why is there a long instruction thing on sun's website? 

what am i looking for?

also trying to do this in faunOS-shadow if you guys have any experience with portable distros.

---

### Post by Sef on 2008-09-24
> drudogg 	 		**Re: problem installing java...**
 		 	Quote:
 	 	 		 			 				 					Originally Posted by **oilchangeguy** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5843335#post5843335") 				
 				*why not just use add/remove, or synaptic package manager?*
 			 		 	 	 
if it was that easy, then why is there a long instruction thing on sun's website? 

what am i looking for?

Applications > Add/Remove > Show: change to 'All Available Applications' > Search: Sun Java 6 > check the top one > apply changes > apply > close.

If you want to install flash and DVD/music codecs as well, type 'restricted' in search instead of 'Sun Java 6'.  (Don't use the quotes in search.)

---

### Post by drudogg on 2008-09-24
got java, but not sun, the ubuntu supported one. it should work... 

thanks for the help!  also found a few other goodies while i was in there!

---

