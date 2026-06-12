---
title: "Installing third party packages REALLY sucks!"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by km4hr on 2005-12-26
I followed instructions on yahoo.com for installing their instant messenger (IM) software on debian systems. It has made a mess of my system. Here are the instructions on yahoo.com:

To install on Debian Linux:

   1. Save the file to your machine.
   2. Log in as root and type: dpkg -i ymessenger_1.0.4_1_i386.deb to install the application.
   3. Run /usr/bin/ymessenger from X Window to launch the application.

Step 2 above results in the following on my machine:

$ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
Password:
Selecting previously deselected package ymessenger.
(Reading database ... 61584 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger


Now when I go into System -> Administration -> Synaptic I get a message telling me to run Edit -> Fix broken packages. This starts a process that consumes 100% of my cpu continously without resolving the problem. A message in a dialog box tells me something about synaptic is attempting to remover the faulty package.
What a mess!

I hate to say it, but until Linux systems get a uniform way for unskilled users to install routine software it's not going be a serious contender to Windows on the desktop.

What can I do now to get my system straightened out? Re-install from scratch? Sounds like MS to me.

---

### Post by 23meg on 2005-12-26
```
sudo apt-get remove ymessenger
sudo apt-get -f install
sudo apt-get update
```

---

### Post by km4hr on 2005-12-28
Thanks 23meg,

I appreciate your response. I'll try your recommendation when I get back to my computer at home.

After re-reading my initial message I saw that it reflected how frustrated I was at the time. I was a little over the top. Sorry about that. 

I would still like to install the yahoo instant messenger client on my computer. Is there any way to install software that's not in an Ubuntu repository?

I do think it's bad for Ubuntu that a prominant web site like yahoo contains an installation procedure that causes Ubuntu's installation/package management system to choke. That's not a strong selling point for new users.

Thanks for your reply.

---

### Post by deNoobius on 2005-12-28
I would download and install the dependencies mentioned in the error message you received and try again.  I haven't installed yahoo messenger (Gaim will work on the Yahoo account, so I see no need), but I have had similar situations and installing the dependencies has always resolved the issue.

Alternatively, there's a way to write a script so that you can create a local repository and install a deb file using synaptic, which should resolve the dependencies just as though you were installing from the actual repositories.

[http://www.ubuntuforums.org/showthread.php?t=42862&highlight=local+repository](http://www.ubuntuforums.org/showthread.php?t=42862&highlight=local+repository)

---

