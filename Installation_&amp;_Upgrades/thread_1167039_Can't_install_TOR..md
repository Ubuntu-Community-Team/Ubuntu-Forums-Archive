---
title: "Can't install TOR."
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by aninona on 2009-05-22
Hello.
I'm trying to install TOR and when I run:
```
sudo apt-get install tor
```
I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate

```

What should I do?

Thanks!!!;);):roll:

---

### Post by fillintheblanks on 2009-05-22
you may need to enable some repositories 

System > Administration > Software Sources 



[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

---

### Post by aninona on 2009-05-22
> **fillintheblanks said:**
> you may need to enable some sources (backports?)

System > Administration > Software Sources > Updates tab

And then what?
My updates tab is attached.


thanks:D

---

### Post by yaroto98 on 2009-05-22
try [this]("http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/")

*EDIT*
looks like you just have to install their [repository]("https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian") first

---

### Post by aninona on 2009-05-22
> **yaroto98 said:**
> try [this]("http://ubuntu-tutorials.com/2006/11/02/how-to-install-tor-privoxy-kubuntu-606-610/")

*EDIT*
looks like you just have to install their [repository]("https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian") first

What exactly do I have to do here?

I've tried:
```
  deb     http://mirror.noreply.org/pub/tor jaunty main
  deb-src http://mirror.noreply.org/pub/tor jaunty main

```

with no success...

---

### Post by aninona on 2009-05-22
When I run ```
apt-get update
```

I receive:
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

Is it the problem?

Thanks!!\\:D/

---

### Post by oldos2er on 2009-05-22
You need to run that as admin:
```
sudo apt-get update && sudo apt-get install tor

```

---

### Post by aninona on 2009-05-22
> **oldos2er said:**
> You need to run that as admin:
```
sudo apt-get update && sudo apt-get install tor

```

thanks(no success), but I get this:
```
Hit http://il.archive.ubuntu.com jaunty Release.gpg
Ign http://il.archive.ubuntu.com jaunty/main Translation-en_US      
Hit http://security.ubuntu.com jaunty-security Release.gpg           
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://il.archive.ubuntu.com jaunty/restricted Translation-en_US 
Ign http://il.archive.ubuntu.com jaunty/universe Translation-en_US   
Ign http://il.archive.ubuntu.com jaunty/multiverse Translation-en_US 
Hit http://il.archive.ubuntu.com jaunty-updates Release.gpg          
Ign http://il.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://il.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://il.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://il.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://il.archive.ubuntu.com jaunty Release                      
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US           
Hit http://security.ubuntu.com jaunty-security Release               
Hit http://il.archive.ubuntu.com jaunty-updates Release             
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://ppa.launchpad.net jaunty Release                          
Hit http://il.archive.ubuntu.com jaunty/main Packages               
Hit http://il.archive.ubuntu.com jaunty/restricted Packages          
Hit http://il.archive.ubuntu.com jaunty/main Sources                 
Hit http://il.archive.ubuntu.com jaunty/restricted Sources           
Hit http://il.archive.ubuntu.com jaunty/universe Packages            
Hit http://security.ubuntu.com jaunty-security/restricted Packages   
Hit http://security.ubuntu.com jaunty-security/main Sources          
Hit http://security.ubuntu.com jaunty-security/restricted Sources    
Hit http://security.ubuntu.com jaunty-security/universe Packages     
Hit http://ppa.launchpad.net jaunty/main Packages                    
Hit http://il.archive.ubuntu.com jaunty/universe Sources             
Hit http://il.archive.ubuntu.com jaunty/multiverse Packages
Hit http://il.archive.ubuntu.com jaunty/multiverse Sources
Hit http://il.archive.ubuntu.com jaunty-updates/main Packages        
Hit http://il.archive.ubuntu.com jaunty-updates/restricted Packages  
Hit http://il.archive.ubuntu.com jaunty-updates/main Sources         
Hit http://il.archive.ubuntu.com jaunty-updates/restricted Sources   
Hit http://il.archive.ubuntu.com jaunty-updates/universe Packages    
Hit http://il.archive.ubuntu.com jaunty-updates/universe Sources     
Hit http://il.archive.ubuntu.com jaunty-updates/multiverse Packages  
Hit http://security.ubuntu.com jaunty-security/universe Sources      
Hit http://security.ubuntu.com jaunty-security/multiverse Packages   
Hit http://security.ubuntu.com jaunty-security/multiverse Sources    
Hit http://il.archive.ubuntu.com jaunty-updates/multiverse Sources   
Hit http://ppa.launchpad.net jaunty/main Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate[/B]

```

---

### Post by sim-value on 2009-05-22
> **aninona said:**
> What exactly do I have to do here?

I've tried:
```
  deb     http://mirror.noreply.org/pub/tor jaunty main
  deb-src http://mirror.noreply.org/pub/tor jaunty main

```

with no success...
in what way did you try it ?

you need to add it to your sources.list

```
sudo gedit /etc/apt/sources.list
```

---

### Post by oldos2er on 2009-05-22
Looks like you're missing the tor repos deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main and deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main

---

### Post by yaroto98 on 2009-05-22
System->Administration->Software Sources

Third-Party Software Tab:

Click Add:
Paste:
```
deb     http://mirror.noreply.org/pub/tor <DISTRIBUTION> main"
```
into the URL it asks for
(Replace "<DISTRIBUTION>" with jaunty, intrepid, or hardy, or whatever version you're running.

redo the same for
```
deb-src http://mirror.noreply.org/pub/tor jaunty main
```

exit out of Software Sources, if it asks to reload, go for it. lastly use the following command in the terminal

```
sudo apt-get update && sudo apt-get install tor
```

---

### Post by aninona on 2009-05-22
> **sim-value said:**
> in what way did you try it ?

you need to add it to your sources.list

```
sudo gedit /etc/apt/sources.list
```

Thanks! I misunderstood what I had to do. It is installed now, but I now I have problems with TOR itself. I guess I'll create a new thread tomorrow...

[img] http://ubuntuforums.org/images/smilies/smiley-faces-80.gif[/img]

---

