---
title: "Window tearing"
date: 2005-12-03
forum: General Help
---

### Post by veelivar on 2005-12-03
Hello,

I really hope that some one could help me here. 

The problem:
When I drag windows around my desktop I'm getting lots of tearing (choppiness? artifacts? distorting? blocking?) around the edges of the windows and the paint update on windows undearneath the current window seems to lag in blocks. 

I've just upgraded to Breezy (fresh install) and I had the same problem in Hoary too.  I'm using the standard Gnome setup with nothign extra installed (apart from fglrx drivers).  I have an ati 9800 pro graphics card with the following output from fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

``` 

From fgl_glxgears I get about 828fps and glxgears I get about 4746fps.  So I think my graphicas card is set up ok.

I had the same effect even beofre I upgraded the drivers fromt he default setup.

Any help here would be appreciated as it basically make the desktop feel really awkward to use.

Thanks alot in advance.

Dan.

---

### Post by celluloid on 2005-12-03
I had this same problem (on my rather low-end spec computer). You may like to give this a try, although it's not very pretty and may not be the best answer to your question.

Go to:
Applications > System Tools > Configuration Editor

Once inside:
Apps: > metacity > general
Then look for the option "reduced_resources" and tick it. There is no need to save, just close out.

You may like to read the description of what this does however.

Hope this may help you, at least until someone with more knowledge of your card etc, comes along.

Regards,
Grant.

---

### Post by veelivar on 2005-12-05
thank I'll have a look into it tonight.

Dan.

---

### Post by veelivar on 2005-12-05
Thankyou for the suggestion I see what you mean by "It's not pretty".  I gave it a go but it dosn't really solve the problem.  My PC should be able to to be smooth, I have a at 9800, 1Gb RAM, and a overclocked athalon.

Does any one have any other suggestions? 

Thanks,
Dan.

---

### Post by newuser111 on 2005-12-05
what kernal are you using? type uname -r in terminal to find out

if you have a new athon i think you should use the k7 kernel or 686

---

