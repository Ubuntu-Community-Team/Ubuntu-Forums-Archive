---
title: "wget need to login to site"
date: 2008-08-18
forum: General Help
---

### Post by boblemur on 2008-08-18
hey, im writing a python script to download my lecture notes as they become available, however one site, needs you to auth, and i dont know how i can do this using python....

i want to get to a pdf inside the site...

[http://www.maths.usyd.edu.au/u/mueller/math1005/loc/w01.pdf](http://www.maths.usyd.edu.au/u/mueller/math1005/loc/w01.pdf)

is the pdf, but i end up at some login page, i have my auth rights... or i can ssh into the uni and see if they still ask for auto internaly...

---

### Post by mikjp on 2008-08-18
What about using university's proxy server so that the site does not ask for authentication?

mikko

---

### Post by boblemur on 2008-08-18
well all i have is ssh access, but they allow tunneling so i guess i could setup tunneling and proxy that way, however i dont know if it will let me even internal without login. 

so if i tunnel in with ssh, how can i set my python to use a proxy?

---

### Post by mikjp on 2008-08-19
This is not really an answer to your question as I have no experience with Python, but I suppose you've read the man page of wget and noticed you can give a username and password using options --http-user and --http-password?

mikko

---

