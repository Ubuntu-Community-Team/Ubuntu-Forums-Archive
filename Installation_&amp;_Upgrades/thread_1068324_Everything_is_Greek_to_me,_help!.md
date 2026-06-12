---
title: "Everything is Greek to me, help!"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by olivertwisted on 2009-02-12
I got my hands on a couple of servers and was told to try Ubuntu on them. I have installed several times and I cannot figure out what to do next. Once I login there is this prompt: 

**spencer@ubuntu-sks:~$ **

How do I get past this and finally to the actual OS?

Thanks

---

### Post by jrusso2 on 2009-02-12
The server all you get is a text interface and I think you have that.

---

### Post by olivertwisted on 2009-02-12
Since that is the case, what information do I need in order to operate it properly and where can I find it? I have to self-teach. Any information is greatly appreciated.

---

### Post by olivertwisted on 2009-02-12
> **jrusso2 said:**
> The server all you get is a text interface and I think you have that.

Since that is the case, what information do I need in order to operate it properly and where can I find it? I have to self-teach. Any information is greatly appreciated.

---

### Post by jrusso2 on 2009-02-12
Yea that's kind of a big job for a forum.  I suggest learning Linux commands and the software the server is going to run.

[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

---

### Post by boof1988 on 2009-02-12
> **olivertwisted said:**
> I got my hands on a couple of servers and was told to try Ubuntu on them. I have installed several times and I cannot figure out what to do next. Once I login there is this prompt: 

**spencer@ubuntu-sks:~$ **

How do I get past this and finally to the actual OS?

Thanks

Have you decided what you want to do with the servers?  What are their purposes?  This should help in determining what to do next.

---

### Post by roshanjose on 2009-02-12
if you are finding that difficulty then install the desktop on the server by typing this:

sudo apt-get install ubuntu-desktop

---

### Post by olivertwisted on 2009-02-12
> **boof1988 said:**
> Have you decided what you want to do with the servers?  What are their purposes?  This should help in determining what to do next.

On one I wanted to place programs that my wife and I use a lot to free up our hard drives and other data.

The other, I wanted to play around with with web pages and connect it to the internet.

I admit this is probably way out of my league, but I have these things (servers) and I would like to learn as much as possible.

Thanks.

---

### Post by olivertwisted on 2009-02-12
> **roshanjose said:**
> if you are finding that difficulty then install the desktop on the server by typing this:

sudo apt-get install ubuntu-desktop

Came back with:  E: Couldn't find package ubuntu-desktop

Do I need to specify a different drive? Possibly?

---

### Post by roshanjose on 2009-02-12
try going to the synaptic manager.....and check it there

---

### Post by boof1988 on 2009-02-12
Maybe we need to back up a little...  Some basic questions to get an idea of where you're at so we're all on the same page.

Do you have a monitor/keyboard/mouse connected directly to the server(s)?

Are you logging onto the servers over your network?

Are you logging directly onto the servers?

Are the servers connected to your network?

Are the servers connected to the interwebs?

---

### Post by olivertwisted on 2009-02-12
> **roshanjose said:**
> try going to the synaptic manager.....and check it there

Holy cow - the what?! I briefly looked at the server guide and also did not see that in the contents.

I thought that when I downloaded Ubuntu it would operate much like windows. I saw some screen shots of that. I guess I was wrong. Do you have the patience to walk me through this? Or you can point me in another direction.

Thanks

---

### Post by boof1988 on 2009-02-12
> **roshanjose said:**
> try going to the synaptic manager.....and check it there

There's no GUI, so there wont be Synaptic Package Manager.

A (semi-GUI-like) package manager (on a server) is:

```
sudo aptitude
```

---

### Post by olivertwisted on 2009-02-12
> **boof1988 said:**
> Maybe we need to back up a little...  Some basic questions to get an idea of where you're at so we're all on the same page.

Do you have a monitor/keyboard/mouse connected directly to the server(s)? **Yes.**

Are you logging onto the servers over your network? **I currently don't have any computers connected to them**

Are you logging directly onto the servers? **Yes, with the mouse, keyboard, and monitor.**

Are the servers connected to your network? **Not networked yet - was just trying to crawl first.**

Are the servers connected to the interwebs? interwebs**Uh?**

---

### Post by olivertwisted on 2009-02-12
> **boof1988 said:**
> There's no GUI, so there wont be Synaptic Package Manager.

A (semi-GUI-like) package manager (on a server) is:

```
sudo aptitude
```

Says: Obsolete and Locally Created Packages and Virtual Packages

1 - "These packages are currently installed....."

2 - "These packages do not exist..."

---

### Post by boof1988 on 2009-02-12
> **olivertwisted said:**
> interwebs**Uh?**

The "interwebs" part was meant to be humourous.

I meant to ask if the servers are connected to the internet.  If they are not connected to the internet, then additional packages (ubuntu-desktop etc.) will need a different method of installation than just typing in the commands as proposed earlier in the thread.

---

### Post by olivertwisted on 2009-02-12
> **boof1988 said:**
> The "interwebs" part was meant to be humourous.

I meant to ask if the servers are connected to the internet.  If they are not connected to the internet, then additional packages (ubuntu-desktop etc.) will need a different method of installation than just typing in the commands as proposed earlier in the thread.

Ok. Where do I get it? Also, will this be a graphical interface at some point or will this forever be text base since it is a server? I tried selling these this first, but no one bought so if I'm stuck with them I want to have the most "user-friendly" way. BTW, they are IBM eServers x series 346 and 345 rack mount type. If that helps?

---

### Post by boof1988 on 2009-02-12
> **olivertwisted said:**
> On one I wanted to place programs that my wife and I use a lot to free up our hard drives and other data.

I'm not sure how to place programs on a server.  I do know a little (very little) bit on how to store data on a server.  Also... I am setting up a music server for playing music (stored on the server) and control it from a different computer on my network.  So my knowledge is somewhat limited, but I might be able to help anyway.

> **olivertwisted said:**
> The other, I wanted to play around with with web pages and connect it to the internet.

I don't think I can help mush here.  I have no experience with web page hosting and such.

> **olivertwisted said:**
> I admit this is probably way out of my league, but I have these things (servers) and I would like to learn as much as possible.

Maybe you can teach me a bit.  :)

---

### Post by olivertwisted on 2009-02-12
> **olivertwisted said:**
> Says: Obsolete and Locally Created Packages and Virtual Packages

1 - "These packages are currently installed....."

2 - "These packages do not exist..."


^^What does this mean?^^

---

### Post by cariboo on 2009-02-12
If you plan on placing windows programs on the server, it won't work. Windows executables don't run on Linux. If you want to store your data files, there is no problem, you will need to setup Samba. Here is a good [howto]("http://ubuntuforums.org/showthread.php?t=202605")

Jim

---

### Post by boof1988 on 2009-02-12
> **olivertwisted said:**
> Ok. Where do I get it?

This will depend on whether you can connect the servers to you network and also the internet.

> **olivertwisted said:**
> Also, will this be a graphical interface at some point or will this forever be text base since it is a server?

You may be able to install the regular desktop version of Ubuntu instead of the server edition so you'll have a more familiar environment.  There are also other options available (that I don't know much about).  It really just depends on what you want to learn/do with them.

> **olivertwisted said:**
> I tried selling these this first, but no one bought so if I'm stuck with them I want to have the most "user-friendly" way. BTW, they are IBM eServers x series 346 and 345 rack mount type. If that helps?

I don't know anything about server hardware.  So I can't help here.

If you are more comfortable, you might just install Ubuntu Desktop on them (and then add the needed packages) so that it's more comfortable for you.  It really just depends on how much you want to learn and how much time you have (or want) to spend on working on them.

---

### Post by boof1988 on 2009-02-12
> **olivertwisted said:**
> ^^What does this mean?^^

Does the screen (to which you refer) look like the attached screen-shot?

---

### Post by olivertwisted on 2009-02-12
> **cariboo907 said:**
> If you plan on placing windows programs on the server, it won't work. Windows executables don't run on Linux. If you want to store your data files, there is no problem, you will need to setup Samba. Here is a good [howto]("http://ubuntuforums.org/showthread.php?t=202605")

Jim
Would it be more simple to just install Ubuntu desktop program like another person metioned? An environment I'm more used to?

---

### Post by olivertwisted on 2009-02-12
> **boof1988 said:**
> Does the screen (to which you refer) look like the attached screen-shot?

Yes, but it only has the Obsolete and Virtual options, not the other 2.

---

### Post by roberto.eiberle on 2009-02-12
you had really better get the desktop edition and work visually, having absolutely no experience with servers you would need a pile of books for learning - not just a few tips in a forum. once connected to the internet you can download all the additional programs you want and setup your server. Once you feel comfortable without a visual user interface you can always come back to the command line.

---

### Post by olivertwisted on 2009-02-12
> **roberto.eiberle said:**
> you had really better get the desktop edition and work visually, having absolutely no experience with servers you would need a pile of books for learning - not just a few tips in a forum. once connected to the internet you can download all the additional programs you want and setup your server. Once you feel comfortable without a visual user interface you can always come back to the command line.

I agree with you completely. Now, can I create a disk like I did for the server edition and install it directly to the server? Because the server is not connected to the web - yet.

Thanks

---

### Post by boof1988 on 2009-02-13
> **olivertwisted said:**
> Now, can I create a disk like I did for the server edition and install it directly to the server? Because the server is not connected to the web - yet.

Thanks

Yes,  you can go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) or any other mirror server and download whichever version is suited to your architecture.

Chose either the 32-bit or 64-bit version.  32-bit operating system will pretty much run on either 32 or 64 bit.  But the 64-bit operating system will only run on 64-bit architecture.

The download file should have a name similar to the following:

For 32-bit or 64-bit hardware:

```
ubuntu-8.04.2-desktop-i386.iso
```

-or-

For 64-bit hardware:

```
ubuntu-8.04.2-desktop-amd64.iso
```

The "amd64" version is not exclusively for AMD processors.  It works on Intel 64-bit processors as well.

---

### Post by olivertwisted on 2009-02-13
> **boof1988 said:**
> Yes,  you can go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) or any other mirror server and download whichever version is suited to your architecture.

Chose either the 32-bit or 64-bit version.  32-bit operating system will pretty much run on either 32 or 64 bit.  But the 64-bit operating system will only run on 64-bit architecture.

The download file should have a name similar to the following:

For 32-bit or 64-bit hardware:

```
ubuntu-8.04.2-desktop-i386.iso
```

-or-

For 64-bit hardware:

```
ubuntu-8.04.2-desktop-amd64.iso
```

The "amd64" version is not exclusively for AMD processors.  It works on Intel 64-bit processors as well.

Ok, created an installation disk (tested it and passed) for the 32-bit and have tried to install several times and will not work/boot. I tried all the boot parameters provided here [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)
and still nothing. Do I need to uninstall the current Ubuntu (server) first? If so, how?<---could not figure this out.

Thanks

---

### Post by roberto.eiberle on 2009-02-13
Nothing to uninstall, does LiveCD work? if not - is Cdrom set as first bootdisk in bios? The new install will overwrite the previous if you don't repartition and I think in your case thats what you should do. I think that server has bootprotection in bios -(not sure) have a look at that

---

### Post by oldos2er on 2009-02-13
No need to uninstall the server version, as you can take care of that during the desktop version installation.

 When you boot the LiveCD, do you get a menu? If so, run 'Check CD for defects.' And if you see any error msgs, please post them here.

---

### Post by olivertwisted on 2009-02-13
> **oldos2er said:**
> No need to uninstall the server version, as you can take care of that during the desktop version installation.

 When you boot the LiveCD, do you get a menu? If so, run 'Check CD for defects.' And if you see any error msgs, please post them here.

Yes I got to the menu and I ran "Check CD for Defects", but it froze and I had to restart. I really did not think there was an issue with the CD because no error messages showed up and I had already did the MD5SUM. Should I try re-downloading and creating a new disk?

Thanks

---

### Post by olivertwisted on 2009-02-13
> **roberto.eiberle said:**
> Nothing to uninstall, does LiveCD work? if not - is Cdrom set as first bootdisk in bios? The new install will overwrite the previous if you don't repartition and I think in your case thats what you should do. I think that server has bootprotection in bios -(not sure) have a look at that

I do get to the menu, but that's it. Everything else just freezes up after selection.

---

### Post by boof1988 on 2009-02-13
> **olivertwisted said:**
> Yes I got to the menu and I ran "Check CD for Defects", but it froze and I had to restart. I really did not think there was an issue with the CD because no error messages showed up and I had already did the MD5SUM. Should I try re-downloading and creating a new disk?

Thanks

Do you know the specs of the servers?  Do they have the minimum requirements to run a Ubuntu desktop?

See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) for system requirements.

---

### Post by olivertwisted on 2009-02-13
> **boof1988 said:**
> Do you know the specs of the servers?  Do they have the minimum requirements to run a Ubuntu desktop?

See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) for system requirements.

Yes, they do.

---

