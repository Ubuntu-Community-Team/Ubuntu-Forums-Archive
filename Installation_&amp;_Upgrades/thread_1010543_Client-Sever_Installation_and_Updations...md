---
title: "Client-Sever Installation and Updations.."
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by roshanjose on 2008-12-13
hey i have been given an assignment to have a client-sever install in our lab with nearly 60 client systems.

I have very little knowledge about severs and clients.....but I have to be done with this assignment

 To these systems there will be a net connection only to the server...the updations will be made to the sever only...so will the client systems be able to update through the sever


If possible then how can we do it?? what are the steps to be taken..

---

### Post by roshanjose on 2008-12-14
is there no  help regarding this issue........

i just wanted to install the client systems from the sever over FTP

---

### Post by roshanjose on 2008-12-18
because there was no reponse from this forum i had to manually install each system without a sever... but i have retained 3 systems for a client-sever installation...

I wanted to experiment this..but i have no idea..

Someone suggested me the debian FAQ's..The forum just explained vaguely..

can anyone help me do the client installation form the sever over FTP

---

### Post by iponeverything on 2008-12-18
> **roshanjose said:**
> is there no  help regarding this issue........

i take it that people are ignorant about it....

Indeed. Or based on your original post, there appears to have been no effort on your part to do your own assignment. 

Your original post was akin to -- this is my assignment - tell me what you would do and how you do it -- step by step.

Perhaps, those looking at original post were not ignorant, but instead perhaps they were unwilling to do your assignment for you.

I know in my case, if you had presented viable solutions and ask for opinions on each -- I might have been willing to help.

---

### Post by roshanjose on 2008-12-18
i have installed 60 systems manually without any sever...

i left 5 systems for client-server installation...

If anyone could help..it would be appreciable

---

### Post by roshanjose on 2008-12-18
Can you suggest me some books also which are available for free download to learn the installation...

probably we are setting up websever, mysql sever..etc

---

### Post by mewithafez on 2008-12-18
> **roshanjose said:**
> Can you suggest me some books also which are available for free download to learn the installation...

probably we are setting up websever, mysql sever..etc

Well, I'm probably the last person you want advice on servers from, but it sounds to me like you want to set up this: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") at the very least for the webserver end of things. 

Internally (the whole client-server thing) you could use apt-cacher on the server so that you would only have to download each package once and then the clients could just get them from the server.

EDIT: Oh and there are instructions on installing all sorts of ways at [https://help.ubuntu.com/community/Installation/LocalNet]("https://help.ubuntu.com/community/Installation/LocalNet"), I just googled and that came up.

---

### Post by roshanjose on 2008-12-19
We are putting up a sever only for the sake of package updations.

The net will be connected only to the sever and the updations will be made by the clients thorough apt-cacher...

so what type of sever do I have to install

---

### Post by roshanjose on 2008-12-23
one system gets updates and then I want to pipe those updates down to other machines on the network?

Some people suggested rsync, aptoncd or some other things like ssh. Which is a good solution???

and can anyone explain how to the updations to the systems

---

