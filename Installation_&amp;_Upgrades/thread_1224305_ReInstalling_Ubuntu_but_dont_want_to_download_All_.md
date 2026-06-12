---
title: "ReInstalling Ubuntu but dont want to download All updates and changes Again"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by omer53 on 2009-07-27
Hi every one !
 
I got a question. 
When i install ubuntu 9.04 and start it for the first time it download few updates from internet. My internet is quite slow. And because of technical mistakes i want to reinstall ubuntu on my laptop again (as i am new to ubuntu) :). 
The problem is that i have already downloaded the updated and few other applications. which are important to make every thing work perfectly on my laptop e.g) Network manager for VPN ... which require dependencies.....
SOoo i want to reinstall Ubuntu but dont want the extra things to download.
What you guys recomend me to do ...
I dont want to download 100+ Updates and other applications 
 
I was trying to search a backup application for that and found "Aptoncd" do you think it will work for me.....
 
or any clever ideas...:confused:

---

### Post by csabo2 on 2009-07-27
if you have not cleaned up with janitor or apt-get clean, you might be able to do that.

---

### Post by nikhilk on 2009-07-27
> **csabo2 said:**
> if you have not cleaned up with janitor or apt-get clean, you might be able to do that.

I will elaborate. The packages that are downloaded during installation are save under "/var/cache/apt/archives".

You can create a local repository from these .deb files. See my post [here]("http://ubuntuforums.org/showpost.php?p=7685342&postcount=4") for links to references for creating a local repository.

---

### Post by omer53 on 2009-07-27
Yahhh i have'nt done that ...
....
 
But can you tell me, do you know any application which can make an installation CD or DVD of the ubuntu i have right now and when i install it .. it installs exactlly the same NO need to download any thing ....
 
Actually i want to change the partitions .. soo that i can completely remove windows .. and save a hellova space :-D

---

### Post by nikhilk on 2009-07-27
> **omer53 said:**
> But can you tell me, do you know any application which can make an installation CD or DVD of the ubuntu i have right now and when i install it .. it installs exactlly the same NO need to download any thing ....

Take a look at [this]("https://help.ubuntu.com/community/InstallCDCustomization") for creating a custom install CD containing packages of your choice.

---

### Post by omer53 on 2009-07-27
@ [nikhilk]("http://ubuntuforums.org/member.php?u=153302")
 
Awesome 
 
Thanks .. you are a life saver

---

### Post by nikhilk on 2009-07-27
> **omer53 said:**
> @ [nikhilk]("http://ubuntuforums.org/member.php?u=153302")
 
Awesome 
 
Thanks .. you are a life saver

You are most welcome :)

---

### Post by Cheesemill on 2009-07-27
Also check out [remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html").

---

### Post by omer53 on 2009-07-27
I am already in love with Ubuntu .... Soo many customizable options anddd ....... free ... :D
 
Thanx Cheesemill

---

