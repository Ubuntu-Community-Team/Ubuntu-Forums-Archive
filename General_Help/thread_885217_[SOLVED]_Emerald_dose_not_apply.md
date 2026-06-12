---
title: "[SOLVED] Emerald dose not apply"
date: 2008-08-09
forum: General Help
---

### Post by Alien260 on 2008-08-09
Hello, 

I just installed a new .emerald theme on my pc. I was looking about in the forum and the command ```
emerald --release 
``` is said to be run. 
It works fine when i run that but the problem i get is that i have to keep that terminal open if i close it, the emerald theme crashes and i get windows with no buttons and i cant to anything with it. 

The only was to recover from that is to open a new terminal and re-release the theme. 

Any ideas what i can do to make it work?

Thanks 
[COLOR="PaleGreen"]Alien[/COLOR]

---

### Post by overdrank on 2008-08-09
> **Alien260 said:**
> Hello, 

I just installed a new .emerald theme on my pc. I was looking about in the forum and the command ```
emerald --release 
``` is said to be run. 
It works fine when i run that but the problem i get is that i have to keep that terminal open if i close it, the emerald theme crashes and i get windows with no buttons and i cant to anything with it. 

The only was to recover from that is to open a new terminal and re-release the theme. 

Any ideas what i can do to make it work?

Thanks 
[COLOR="PaleGreen"]Alien[/COLOR]

Hi and add it to the start up under system, preference, session. I believe the command is emerald --replace

---

### Post by ad_267 on 2008-08-09
You can also run it by entering that command after pressing Alt+F2.

---

### Post by Alien260 on 2008-08-10
> **overdrank said:**
> Hi and add it to the start up under system, preference, session. I believe the command is emerald --replace

Well, isnt this a hugh problem that emerald has? As in if i want to use it i have to write a script and run it at startup ?!?!?! 

Isnt there another way to solve it.

I was reading around that some people say that this problem is because compiz and emerald dont really work well together, is this the problem?

Thanks again guys 
[COLOR="PaleGreen"]Alien [/COLOR]

---

### Post by halln on 2008-08-10
> **Alien260 said:**
> Well, isnt this a hugh problem that emerald has? As in if i want to use it i have to write a script and run it at startup ?!?!?! 

Isnt there another way to solve it.

I was reading around that some people say that this problem is because compiz and emerald dont really work well together, is this the problem?

Thanks again guys 
[COLOR="PaleGreen"]Alien [/COLOR]

It should be emerald --replace not emerald release and Go to system/preference/session/ type this for Name: emerald or anything  Command: emerald --replace/close/reset

---

### Post by Alien260 on 2008-08-10
> **halln said:**
> It should be emerald --replace not emerald release and Go to system/preference/session/ type this for Name: emerald or anything  Command: emerald --replace/close/reset


Perfect got it working fine, 

Thank you for that.

Regards 
[COLOR="PaleGreen"]Alien [/COLOR]

---

### Post by overdrank on 2008-08-10
> **Alien260 said:**
> Well, isnt this a hugh problem that emerald has? As in if i want to use it i have to write a script and run it at startup ?!?!?! 

Isnt there another way to solve it.

I was reading around that some people say that this problem is because compiz and emerald dont really work well together, is this the problem?

Thanks again guys 
[COLOR="PaleGreen"]Alien [/COLOR]

Hi and as you can see you did not have to write a script. :)
Just the directions that I and halln gave.

---

