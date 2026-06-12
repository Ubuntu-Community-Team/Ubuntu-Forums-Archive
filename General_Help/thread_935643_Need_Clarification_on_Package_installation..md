---
title: "Need Clarification on Package installation."
date: 2008-10-01
forum: General Help
---

### Post by dgoddard1 on 2008-10-01
I am trying to install gnomesword locally because my only internet connection is a slow dial up connection and given enough time it will screw up. So installing over the internet should be considered a bad idea for me.

I went to :
[http://packages.ubuntu.com/hardy/gnomesword](http://packages.ubuntu.com/hardy/gnomesword)
to get the package and I find a 5.3 megabyte .deb package downloadable at the bottom of the page.  

Before finding what appears to be the main file I found about 34 other packages noted as "depends".  They are rather cryptically described in linux jargon.  I have no idea what the designation "depends" means.  Do I have to download some or all of these to get a functioning installation of gnomesword on my computer???

I thought I would find the entire thing in a single package.

---

### Post by hansdown on 2008-10-01
Hi dgoddard1.

Gnomesword is in the repos.

System> administration> synaptic package manager.

Hope this helps.

---

### Post by karlr42 on 2008-10-01
> **dgoddard1 said:**
>  Do I have to download some or all of these to get a functioning installation of gnomesword on my computer???
Short answer- yes.
Better answer- you may already have a lot of those dependencies, you can check.
But this is why apt-get/synaptics is there, it takes care of those dependencies.
Try get access to someonoe's internet and run
```
 sudo apt-get install gnomesword

```
and you'll have the program in seconds.

---

### Post by karlr42 on 2008-10-01
> **hansdown said:**
> Hi dgoddard1.

Gnomesword is in the repos.

System> administration> synaptic package manager.

Hope this helps.
I think his probelem is that the PC he wants to install to only has dial-up, so he wants to get the package elsewhere, then transfer it across and install it. 

Try that command I gave you, the download is 8041kB, not huge. 

```
$ sudo apt-get install gnomesword
..
Need to get 8041kB of archives.

```

---

### Post by drs305 on 2008-10-01
I just looked up gnomesword in synaptic. I have a fairly normal install of hardy and on my system I would need to install about 7 extra packages. I frequently clean my cache of unused packages/libraries but a lot depends on the file sizes.

Edited: It requires about 30 packages, I would need 7 extras...

---

### Post by karlr42 on 2008-10-01
It depends on the particular system- I only need to get 7 packages. 
But to the OP- just install it from synaptics/my command, it may take a while, but you can leave it overnight if necessary. Then, get broadband ;)

---

### Post by Therion on 2008-10-01
> **dgoddard1 said:**
> 
Before finding what appears to be the main file I found about 34 other packages noted as "depends".  They are rather cryptically described in linux jargon.  I have no idea what the designation "depends" means.
"Dependencies" are other applications, or bits of software, that another application requires in order to run -- the main application is *dependent* on them being there.  Linux will automatically find and install these dependent applications for you so there's nothing to worry about.

---

### Post by jerome1232 on 2008-10-01
It's amazing how many people don't seem to read the OP, it's screws up becuase of his connection when he tries to use the package manager. An easy way to figure out exactly which packages you should download try this.

```
sudo apt-get install gnomesword
```

now take a look at your screen, mine looks like this:

```
sudo apt-get install gnomesword 
[sudo] password for jeremy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gtkhtml3.8 libclucene0ldbl libgtkhtml3.8-15 libsword6 sword-comm-mhcc
  sword-dict-naves sword-text-arasvd
Suggested packages:
  libgtkhtml3.8-dbg
Recommended packages:
  sword-frontend
[COLOR="Blue"]The following NEW packages will be installed:
  gnomesword gtkhtml3.8 libclucene0ldbl libgtkhtml3.8-15 libsword6
  sword-comm-mhcc sword-dict-naves sword-text-arasvd[/COLOR]
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 8502kB of archives.
After this operation, 20.4MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

So from that it is going to download everything under the blue section (well what shows up for you, the exact packages for you may vary), so download those individual pacakges and install them one by one.

---

### Post by dgoddard1 on 2008-10-05
So I tried that command in terminal mode and this is what I get.

######## Record of attempt ##########

user1@dell-desktop:~$ sudo apt-get install gnomesword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnomesword
user1@dell-desktop:~$ 

######## End Record of attempt ##########

I had an active internet connection at the time

Then I noticed that my modem connection seemed to be tied up doing some sort of large download from some unidentified location so I decided I should hang it up because I had no idea what it was downloading  

Details provided by clicking on the icon for the modem connection revealed:
Address          69.130 198.20
Destination      69.130.198.1

Then I decided to let it run its course anyway and download whatever and hope it did not screw over my computer.

######## Traceroute Results ##########
Hop   Hostname                                       ip            Time 1
1     h69-130-198-20.stldmo.dial.dynamic.tds.net 69.130.198.20   0.085ms
1     69.130.198.20                              69.130 198 20   0.093ms
1     h69-130-198-20.stldmo.dial.dynamic.tds.net 69.130.198.20   0.061ms

######## End Traceroute Results ##########

If that means anything.  Hopefully I didn't make any typos in transcribing that.  There is nothing there I recognize other than that tds.net is my dial-up internet service provider

---

### Post by dgoddard1 on 2008-10-05
Well after waiting for the dowload to finish, I figured that it had probably downloaded gnomesword as it seemed to have downloaded about 8+ megabytes of something, so I tried the Add/Remove option under Applications on the menu bar, and found that I was now offered gnomesword as an application I could Install.  After a few clicks there It needed to download a bit more and Voila, I found Gnomesword as an application under Appllications/accessories/Gnomesword.  

I clicked on it and the application started up with a display of the Bible in Arabic! :mad::confused: Now that is about as useless to me as tits on a boar hog!  And no instructions about how to get an english version either.  After all the effort I went to to get this application I am appalled that the default of the automatic install process would put this most unlikely to be sought of all translations in place.

Does anyone have a suggestion on how to proceed from here to get the modules of English Translations that might be useful to me.  I would be potentially interested in any English Translations and Greek and Hebrew Lexicons or Concordances.

Perhaps there is a forum somewhere that deals with these issues, and someone could direct me there.

---

### Post by jerome1232 on 2008-10-05
Ok this is how you download alternate texts.

Pop open gnomesword, click on Edit->Module Manager, click on Configure on the lefthand side, select remote, click refresh on the lower right hand side, now back to your left-hand pane select install, You should be able to browse through various texts.


Now if the text turns out to be a monster file (they are compressed so they shouldn't be very big) that would cause you problems you can download modules from [this]("http://www.crosswire.org/sword/modules/") site and install them locally.

edit: Wow they have alot of translations available, neat.

---

