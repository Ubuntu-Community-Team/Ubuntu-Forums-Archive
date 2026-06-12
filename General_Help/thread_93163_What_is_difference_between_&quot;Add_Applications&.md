---
title: "What is difference between &quot;Add Applications&quot;, Synaptic, and apt-get ?"
date: 2005-11-21
forum: General Help
---

### Post by pbb on 2005-11-21
Here I am with another newbie-question.

Playing around with Ubuntu and reading comments on websites, I've tried out a bit on installing components/applications. In one specific case, I got a bit confused about the differences:

* "Add Applications" (at the bottom of the Applications menu) turned up no results when searching for "DHCP"

* Synaptic (in the System > Administration menu), or selecting File > Advanced from "Add Applications", did give a list of results when searching for "DHCP", but nothing with just the name "dhcp".

* apt-get did respond positive when performing "apt-get install dhcp".

I was under the impression that "Add Applications", Synaptic and apt-get were just three different interfaces to the same application. How is it then possible that a search in them displays different results? Are they in deed different things?

Note: this is NOT a question about dhcp. I just provide that as an example I've found. This question is about the differences betwee the three mentioned interfaces.

Thanks, Peter

---

### Post by mgor on 2005-11-21
add applications is a lightweight altarnative for synaptic,
synaptic is a gui frontend for apt-get,
and apt-get is the command line tool for installing packages.

---

### Post by earobinson on 2005-11-21
I assume that synaptic has everything + more than add applications.

---

### Post by pbb on 2005-11-21
Okay, so you are saying that you can choose from more installable components with Synaptic than with Add Applications? And apt-get has again a more complete list?
Is there a filosophy behind this? Because at the moment I am mostly using Add Applications because of it friendly interface, but then I find I need to install components that cannot be found within Add Applications, so I need to switch to Synaptic again. Why doesn't Add Applications contain a complete list? And apparently not even Synaptic contains everything apt-get does contain?

---

### Post by earobinson on 2005-11-21
synaptic has a good gui IMHO. I have never used Add Applications.

Ubuntu is designed with everyone in mind. My guess is that the dev team thought that Add Applications would be less intimiadation to a novice user so they put only programs that users are likley to need in the Add Applications program. Synaptic lists all the programs in your repo and lots of ones that you wont need. It also lists programs that the user will never used but other programs use. For example if you installed a program that used python synaptic would install python, so even though you may never use pytho, python is installed and listed in synaptic.

My guess is that this is not the case in add remove, and that add remove would install python but not tell you that it did so.

If you are going to want to be installing less main stream programs you will have to learn to use synaptic, (or maybe even compile on your own for the really small programs)

Hope this helps

---

### Post by rejser on 2005-11-21
dont forget aptitude.
it can backtrack :)
if some program installs dependencies and you then uninstall that program it checks if any other program uses those deoendencis and if not, removes them to

---

### Post by pbb on 2005-11-21
Okay, I understand the background a bit. Too bad the whole idea is not really working, since as a novice you already get confronted with components that are not available in Add Applications...

And can anybody explain why I could not find a components called "dhcp" (with nothing extra), but "apt-get install dhcp" works? Is there maybe an alias defined somewhere that says "dhcp" is really "dhcp-blah-x.xx-something" ?

---

