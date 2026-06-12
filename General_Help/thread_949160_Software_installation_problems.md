---
title: "Software installation problems"
date: 2008-10-15
forum: General Help
---

### Post by jbu004 on 2008-10-15
I am trying to install Eclipse and Java on my laptop. I downloaded the eclipse tar.gz and I was wondering where the correct place to unpackage it is. Right now I just have it unpackaged on my desktop, which I'm sure is not where it is supposed to be. I have the same situation with Java as well. I just started using Linux yesterday and have a general understanding of the file system, but still don't know exactly what to do.

---

### Post by patrickballeux on 2008-10-15
> **jbu004 said:**
> I am trying to install Eclipse and Java on my laptop. I downloaded the eclipse tar.gz and I was wondering where the correct place to unpackage it is. Right now I just have it unpackaged on my desktop, which I'm sure is not where it is supposed to be. I have the same situation with Java as well. I just started using Linux yesterday and have a general understanding of the file system, but still don't know exactly what to do.

You started wrong by downloading the tar.gz...  The "correct" way is to use Synaptic (System - Administration menu) or "Add/Remove" from the Application menu.

In Ubuntu, you install software from a repositories that you can access with Synaptic (or Add/Remove).  You can search in there for the proper software to download and install/remove).

Java 6, Eclipe and Netbeans are available from the repositories.

Downloading from the website is kept for the power users who knows how to do things since it can sometime not work on a specific Linux version...

Manage your software in Synaptic, and you'll be a lot happier.  Also, doing this, you can benefit from the automatic update for all your softwares that you installed using the repositories.

It's like Windows Update + Add and Remove Software, but for all the softwares available (that was tested with your Ubuntu).

Again, see "System - Administration - Package Manager Synaptic" or "Application - Add/Remove"

Good luck!

---

### Post by shawnrgr on 2008-10-16
It doesn't matter how you downloaded eclipse. I don't use the eclipse from the repositories either because i use it for php programming. Usually you put it in /opt/eclipse/ and the run script will be in the base directory. Eclipse can run straight out of the directory wherever to put it. its java, it doesn't need to be "installed".

As far as java goes, yes best to install from repositories.

$ sudo apt-get install sun-java6-jre sun-java6-bin

add sun-java6-jdk if your going to be creating java apps.

---

