---
title: "Adept problems?"
date: 2005-11-21
forum: General Help
---

### Post by gypsy98101 on 2005-11-21
I just can't seem to use Adept.  Almost everytime I try to connect, it just hangs at "retrieving headers" or something.  It just sits there at "0%" and never moves.  Then I have to kill it or just leave it for like 30 minutes and it will finally time out.  
Is anyone else having this problem?

---

### Post by ltmon on 2005-11-21
It works fine for me.

Do all your command line apt-get tools work?

e.g.
> sudo apt-get update
> sudo apt-get install <package>
> sudo aptitude
> sudo synaptic

What if you start adept from the command line?  Does it give any extra information?

L.

---

### Post by gypsy98101 on 2005-11-21
No, nothing works.  I just opened a shell and did the command line thing.  apt-get update just says connecting to us.archive.ubuntu.com 0% and never goes anywhere else.  
Wierd.

---

### Post by aysiu on 2005-11-21
Have you tried changing your sources.list?
See the first link in my sig for details.

---

### Post by ltmon on 2005-11-21
[QUOTE=gypsy98101]No, nothing works.  I just opened a shell and did the command line thing.  apt-get update just says connecting to us.archive.ubuntu.com 0% and never goes anywhere else.  
Wierd.[/QUOTE]

It sounds like you can't get a connection to the update sites.

Either:
- You have no internet connection at all (can you browse the web fine?)
- You have a proxy server you need to get through 
- The sites are down (in this case you can use a different mirror, or just wait until they are fixed)

L.

---

### Post by gypsy98101 on 2005-11-22
Ok, I think it might have been some cheese in the sources.list file.  I deleted it all and replaced the sources with the ones in the above post and at least now I can get to the locations.

LTmon, thanks for the advice but I knew it wasn't the connection.  I could use the i'net, I could even ping the sites that apt-get couldn't reach.  It just wasn't getting the headers for some reason.  

Now it seems to work.  Thanks again!!!

---

### Post by Licaon on 2005-11-24
i have a problem with Adept, running Breezy+kubuntu-desktop

i do an Update -> Upgrade.... the window (Adept has only one window where it shows stuff) will show some packages beeing downloaded... so while i wait for it to finish i look at the Adept menu and click on the Manage repositorys.... it shows the edit window.... i click on the CLOSE  button located in the lower right side of the window... and now Adept will show the usual window that you get when you start Adept... the one where you see what packages are installed NOT the window that shows package download progress.... i cant find any way to get to that window... if i close adept i will still have a ADEPT process in memory

any ideas? 10x

---

