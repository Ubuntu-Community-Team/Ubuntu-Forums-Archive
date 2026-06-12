---
title: "Java Install gone bad! Cant install ANYTHING."
date: 2008-11-21
forum: General Help
---

### Post by rstellers on 2008-11-21
I installed the "ubuntu-restricted-extras" package using "sudo apt-get install ubuntu-restricted-extras" and encountered a problem with the Java portion and had to manually close the terminal window.  Now I cannot install anything using either apt-get or adept.  In adept I get a message saying the following regardless of what package i am trying to install...  I get a similar error with apt-get install as well.  I am a newb and just statring to learn my way around so your help is greatly appreciated.

Download failed.
The list of errors is attached. The recovery for this case is currently not implemented. If you see 404 errors, it might be useful to try fetching package lists (see the Sources tab) and retrying the operation.

The error was: 
APT Error. Context:
    Package download failed, 
    I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch), 
    : ,

---

### Post by oldos2er on 2008-11-21
Try running these commands one at a time:

sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by rstellers on 2008-11-21
I knew it had to be easy.  Thanks worked perfectly!

---

### Post by anjilslaire on 2008-11-21
(hint: Click the little gold medal to the right of the post to Thank the user who helps you :) )

---

