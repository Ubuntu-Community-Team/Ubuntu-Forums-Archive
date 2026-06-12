---
title: "Build a Drobo?"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by Rabidmonkey1 on 2007-09-04
Hello everyone, I have something of an interesting proposition here for the community.

A nice piece of tech that's recently caught my eye is the Drobo.  For those unfamiliar, see here: [http://www.drobo.com/]("http://www.drobo.com/")

Now though this is very nice and all that, there are some limitations to the system, namely, it doesn't work with linux (at least not officially), and it is quite pricey.

But it got me thinking...could it be possibly to build a unit with Drobo like functionality?

Specifically, something that provides a simple (ha) Hot-swappable RAID array that sits external to the computer and connects via USB...  Think exactly like the Drobo.  It should also work cross-platform.

I've seen arrays that you can build and set up internally, however that does not like a simple solution.  My key goal with this is to be able to safely share large large documents cross platform, instead of maintaining duplicates on different drives for different OS's.

Is there anything out there like this now that allows for all these features?  Or perhaps there is a simple way of building and managing something like this yourself?  Any takers?

---

### Post by tobycatlin on 2007-09-21
I'd like an open source version of the drobo.
It wouldn't even need to be hot swappable. Just auto detecting.
I love the way you can remove a small drive from the array and replace it with the larger disk and it automatically sync's everything.

Am i right in thinking that drobo essentially uses a combination of raid 5 and lvm to work it's magic?

---

### Post by rocktorrentz on 2008-02-24
I hate reviving dead threads but I would love it if something like this were developed. It is possible using LVM and RAID levels 5 and 1 (depending on the number of drives) but it's really tedious and is only something that the more adventurous of us would even dream of trying. Something with a GUI interface that automates everything would be amazing. There is not even a GUI for mdadm at the moment which is really annoying for new users who don't like the command line. Unfortunately I have no programming experience to implement something like this but I imagine it would be relatively simple becuase the tools are already there in mdadm and lvm.

---

### Post by tobycatlin on 2008-02-25
I have been looking at freeNAS 
[http://en.wikipedia.org/wiki/FreeNAS](http://en.wikipedia.org/wiki/FreeNAS)
[http://www.freenas.org/](http://www.freenas.org/)

I am planning on building a file server around this OS and a miniITX board. I still don't know that much about freeNAS as i haven't done a install yet. From what i have read it implements all forms of software raid and would be capable of functioning like a Drobo if it doesn't already. 
It certainly looks like a good start point

---

### Post by rocktorrentz on 2008-02-25
Freenas is simply a file server distribution based on FreeBSD which uses its software raid functionality. Afaik it does not have the advantage of complete automation like the drobo although it is very easy to use if all you want is a file server.

---

### Post by tobycatlin on 2008-02-25
or maybe unRaid would do the job
[http://www.lime-technology.com/wordpress/](http://www.lime-technology.com/wordpress/)

---

### Post by blankphoto on 2008-06-03
I was blown away by the Drobo, and destroyed when i found out it doesn't work with Linux. What is the reason it doesn't work with Linux and is there a work around or fix buy now?

Also saying Drobo did work with Linux, can I move my /home folder to it (or any other drive) and use that as my /home? I've heard of doing this but what goes into it?

Thanks in advance,
Brian

PS: Drobo now has a network share, A NAS box addon. Can the /home folder be in a remote network drive? Aslo does anyone know if the NAS box will work with Samba?

---

### Post by rocktorrentz on 2008-06-03
There is linux support and with the latest firmware it appears that ext3 works:
[http://www.drobospace.com/forum/thread/10552/When-is-ext3-support-expected-/?page=3](http://www.drobospace.com/forum/thread/10552/When-is-ext3-support-expected-/?page=3)

---

### Post by blankphoto on 2008-06-10
Unfortunately, I'm being forced to return to winblows... I do desktop publishing and I cant get CS3 to run on Ubuntu (hardy) I've tried wine (crossover) it just wont work. so back to microshaft I go crawling...

---

