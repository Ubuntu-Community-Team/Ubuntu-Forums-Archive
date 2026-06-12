---
title: "Ubuntu server and client installations"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by roshanjose on 2009-04-22
I have been given an opportunity to install Ubuntu on 60 systems in our lab with a local server connecting all these systems.

The main purpose of local server is only for package updations i.e i wanted to update packages to the local server first and then the client systems update from the server.

I want solutions to these problems:

1) Any idea how i can install the client without using the cd each and every time. Is there any way i can install the desktop systems from the server.

2) How can I make the clients update packages from the local server

3) i wanted to put up a private mirror so that many ubuntu users of our campus from their homes can have two advantages:

   a) update packages from this server
   b) upgrade to new release from this server.


Is there any solutions to these??

---

### Post by halitech on 2009-04-22
for the install you could follow the info here:

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

not sure on the updates but you could try pointing the repo to the IP of the server

---

### Post by roshanjose on 2009-04-22
and i got the idea of the private network from here

[http://www.ubuntu.com/getubuntu/mirror/1](http://www.ubuntu.com/getubuntu/mirror/1)

nothing much is said about private mirror..

i wanted the local machines to update packages as well as download the cd image from this server.

---

### Post by zvacet on 2009-04-22
Read [this]("https://help.ubuntu.com/community/Apt-Cacher-Server") for your second question.

---

### Post by roshanjose on 2009-04-22
for the 2nd question there where three suggestions:

 a)apt-cacher
 b)apt-proxy
 c)apt-mirror

whats really the difference between them and which one should be used??

---

### Post by roshanjose on 2009-04-22
i spent a lot of time on the xchat to get some ideas. Here's the conversation:


<jdu> PerryArmstrong, you can use apt-proxy on the server to share updates.  The cd could potentially be booted from the network and installed.


<PerryArmstrong> jdu; so through this apt-proxy...i can boot the cd from the network??


<jdu> PerryArmstrong, no apt-proxy would only handle updates through the server.


<jdu> [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)  should work, I think



<jdu> PerryArmstrong, Another way is to use the cd in all the clients but to specify a .cfg file over the network.

Perry; this is getting complicated

<jdu> PerryArmstrong, yes. The file would supply the answers to all the questions when installing so all you would have to would be to insert the cd and tell it where the file is.

---

### Post by roshanjose on 2009-04-22
<simNIX> PerryArmstrong, with apt-cacher I had that clients borked on some files that were corupted while apt-cacher grabbed it - I then had to manualy remove it from pool and then it would be regrabbed







<simNIX> PerryArmstrong, apt-proxy sometimes failed here so I went for a local mirror with apt-mirror

simNIX> with apt-mirror you can also setup to grab updates

<simNIX> PerryArmstrong, I only mirror i386 and thats around 22Gb, the 1Gb ram is overkill but nice to have - I serve it out with vsftpd to my clients

<PerryArmstrong> simNIX; whats really the difference between apt-mirror, apt-proxy and apt-cacher

<simNIX> apt-proxy and apt-cacher are mostly the same; if a cliet requests a file they grab it for thhat cleint and store it for use for next client wanting the same - apt-mirror is a way to download have a full mirror (with posiblity only i386 or any arch)

<simNIX> PerryArmstrong, simpler put; proxy programs grab only that requsted (and in my experience sometimes wrongly) and apt-mirror just downloads everithing

PerryArmstrong> simNIX; so i think apt-mirror works better

<simNIX> I agree


<simNIX> PerryArmstrong, I dont get -> this is all I have to do to get it working; [http://pastebin.com/f342577b5](http://pastebin.com/f342577b5)

Peery;  can my dektop update from campus

<simNIX> is your home on campus or do you from home needto go over the Internet to connect ot it ..


<PerryArmstrong> simNIX; the server will have internet connection and i'll put it on 24 hrs. if necessary...

<PerryArmstrong> simNIX; should the server be running all the time then??


<simNIX> PerryArmstrong, Internet connection to grab new files is no problem; the risk comes if you make it so someone on the Internet can connect to it - that would open up a can of worms, that you dont have if at home you use another server to update / install from


<Perry> simNIX; i just wanted all the students of the campus have the ability to update from their homes through the internet..


<simNIX> PerryArmstrong, if you have a local dns at home you could point your desktop to a name that resolves to ubuntu mirror online, and at work have that name resolve to ip box with apt-mirror


<simNIX> PerryArmstrong, why ?

<PerryArmstrong> simNIX; we have many ubuntu users locally and they complain of taking time for updating packages from the other severs which are not available locally


<PerryArmstrong> simNIX; but what i am worried now is network traffic and you also mentioned there will be some problem if anyone else is updating..whats the problem..."you mentioned can of worms"

<simNIX> PerryArmstrong - then apt-mirror dowlnoad of all files 2x a day maybe would be perfect on campus - just share out what it downloads over http or ftp and point every client to use this ftp/http


<PerryArmstrong> simNIX; are there any manuals upon this...??

<simNIX> PerryArmstrong, you still got pastebin I gave you with how to config it ?

<PerryArmstrong> simNIX; yes i do have

<simNIX> thats all you need
<simNIX> + setup a vsftpd of http server
<simNIX> loose the lines I have for Debian

<simNIX> install apt-mirror

<simNIX> modify in config directory you want it to download and do apt-mirror. it will  dowlnoad about 22Gb

<PerryArmstrong> simNIX; i have to install apt-mirror only on the server??

<simNIX> PerryArmstrong, on campus make it for instance so the ubuntu.campus.com (replace domain) point to ip box runnig vsftpd (shares out what apt-mirror on same box grabs) in /etc/apt/sources.list


<simNIX> PerryArmstrong ... in /etc/apt/sources.list of clients you then set ubuntu.campus.com


<PerryArmstrong> simNIX; you have given me lots of info thanks...now i have to check on various things like setting up ftp..etc...


<simNIX> PerryArmstrong, gladely helped - vsftpd is an option or maybe lightttpd since ftp is a bit harder to let through risticted firewall - this is only an consideration if clients also need to be able to use same mirror at home over the Internet

<PerryArmstrong> simNIX; so setting up this on vsftpd or lightttpd doesn't depend on the speed of internet on the server

<simNIX> PerryArmstrong, for clients on campus only the speed to the vsftpd oor lighttpd counts

<PerryArmstrong> simNIX; but i have to consider both...clients connected to the server and machines on the internet (home)


<simNIX> PerryArmstrong, then a script at clients that checks somehow if its at campus or at home and set at home to use normal online mirror instead of the campus one will save the campus a load of outbound bandwidth

<PerryArmstrong> simNIX; yes but maybe if i limit it to only our campus students to update from their homes and not anyone else...it might help...but the question is how to do this??


<PerryArmstrong> simNIX; or maybe i have to request the department head to increase the speed

<simNIX> PerryArmstrong, I am going ... a bash script at boot could copy a diferent apt.sources depending on where it -is - for how that I dont have recepy ready for ..


<simNIX> PerryArmstrong, IF you figure out howto get clients at boot to have a different apt.sources depending if at campus or not will make clients not use presious bandwidt of campus when at home ANd that wil make that  clients get best speed


<PerryArmstrong> simNIX; the clients at home are the people who are going to work on Ubuntu development... so its not all of the students..its only those who are on the craze for Ubuntu who are a handful

---

### Post by roshanjose on 2009-04-22
if anyone has any idea and wishes to add something here...

please do so...i need answers to all my questions

---

