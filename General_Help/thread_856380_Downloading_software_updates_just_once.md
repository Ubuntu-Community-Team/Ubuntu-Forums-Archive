---
title: "Downloading software updates just once"
date: 2008-07-11
forum: General Help
---

### Post by chettyk on 2008-07-11
I have Hardy installed on three of my computers: my laptop, my personal desktop and the family computer. At present, I am downloading software updates separately for each of the three computers. That seems to me to be a waste of bandwidth. 

Is there some way I can download the software updates on just one computer and then use the downloaded software files to update the other two computers?

Thanks for any help.

-- Chettyk

---

### Post by coffeecat on 2008-07-11
> **chettyk said:**
> Is there some way I can download the software updates on just one computer and then use the downloaded software files to update the other two computers?
-- Chettyk

Yes. The following is crude but it works. Others may have better ideas. The downloaded packages are *.deb files and you will find them in /var/cache/apt/archives/ . The folder is owned by root so you'll need 'sudo cp' or whatever way you have of copying root-owned files. I open a file browser with 'gksudo nautilus' so that I can drag and drop onto a usb drive (or via my file server) and thence to the next machine. One gotcha though. There's a file called 'lock' which prevents you from copying the whole contents in one go. All I do is to highlight everything up to lock and copy that lot and then everything after. Also, there's a folder called 'partial'. I have no idea what it does; I don't bother to copy it, and everything works fine.

I'm sure there's a way of setting up a home server as a repository, but I haven't got round to figuring out how to do this yet.

**Edit**: Sorry, what I didn't explain is that once you've copied the *.deb files into /var/cache/apt/archives/ on the second machine, the package manager uses them and doesn't download from the Ubuntu server.

---

### Post by MasterXandrex on 2008-07-11
If you have a spare PC and/or the space to hold it you can mirror the repos.

But if you're bandwidth limited this might not be for you.

[http://www.howtoforge.com/local_debian_ubuntu_mirror]("http://www.howtoforge.com/local_debian_ubuntu_mirror")

Xan

---

### Post by chettyk on 2008-07-11
Thanks a lot, coffeecat. The idea of copying the *.deb files from the cache had crossed my mind, although I haven't tried it out. But your suggestion about moving the *.deb files to the second (and subsequent machine's) /var/cache/apt/archives/ folder had not occurred to me. Great idea! Thanks again.

-- Chettyk

---

### Post by chettyk on 2008-07-11
> **UbuntuUser3859 said:**
> 

But if you're bandwidth limited this might not be for you.

Xan

I do have bandwidth limitations, I am afraid, which is why I am trying to avoid downloading the same software updates multiple times. But yours is certainly a very interesting idea and one that I'll bear in mind. Thanks.

---

### Post by chettyk on 2008-07-12
coffeecat, your suggestion worked beautifully. Thanks.

---

### Post by MasterXandrex on 2008-07-12
I had a spare box to sit in the closet and decied to mirror and repos. The nice thing is that the other five ubuntu machines running in the house install and upgrade at around 11.5MB/s. 


Xan

---

### Post by chettyk on 2008-07-12
Xan, I'll try your idea out when I have a bit more spare time. Thanks.

---

