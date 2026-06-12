---
title: "Cairo install woes"
date: 2008-09-12
forum: General Help
---

### Post by schizostatic on 2008-09-12
I am attempting to install Cairo and I am following the [wiki page]("https://help.ubuntu.com/community/CairoDock"). I first added the rep option, when I run the line
```
sudo apt-get install cairo-dock cairo-dock-plugins
```
I get
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cairo-dock-plugins

```

Then I move onto option #2 from the wiki. Which is down the deb's and run them. When I do that I get.
```
static@static-laptop:~/Desktop$ sudo dpkg -i cairo-dock_v1.6.2.3_i686.deb
dpkg-deb: `cairo-dock_v1.6.2.3_i686.deb' is not a debian format archive
dpkg: error processing cairo-dock_v1.6.2.3_i686.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 cairo-dock_v1.6.2.3_i686.deb

```
And I checked to make sure the .deb was executable incase that was the issue. Tried just double clicking it to that error'd saying it is either corrupt or I don't have permission. So was curious what are my other options other then building from source? Or should I give up and just try out AWN?

---

### Post by fabounet on 2008-09-12
just double-click on the .deb (the dock's one first), and install it with GDebi
Or better, use the [Cairo-Dock's repository]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en") instead of downloading yourself the .deb

---

### Post by schizostatic on 2008-09-12
> **fabounet said:**
> just double-click on the .deb (the dock's one first), and install it with GDebi
Or better, use the [Cairo-Dock's repository]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en") instead of downloading yourself the .deb

Did you even read what I posted? I stated and showed what happens when I double click the deb and what happens when I use the reps.

-
I gave up and went with AWN. Not sure why this doesn't work tho.

---

### Post by fabounet on 2008-09-12
I didn't but you too :-p
> E: Couldn't find package cairo-dock-plugins
clearly means that this package doesn't exist in your repos, because simply the name is mispelled.
try with cairo-dock-plug-ins, or better, use Synaptic !

---

### Post by ellalan on 2008-09-12
Its actually cairo-dock plugins. There is no dash(-) between dock and plugins. Synaptics is easier.

---

### Post by IanW on 2008-09-12
I think I can shed some light on why your "Option#2" failed...

If you right-clicked to save the *.deb files from the Berlios page linked in the wiki, this is where you went wrong.
Each link claims to be a downloadable file, but actually links to a "mirror chooser" page with 2 choices for each file.

You need to right-click & choose "Open in new tab" to reach the mirror page, then left-click on a mirror to save each *.deb file.

---

### Post by alopecoid on 2008-10-06
I have similar problems to the original poster. I have been trying to install Cairo Dock on-and-off for weeks now. If anyone can help it, that would be awesome.

I followed the directions here:
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)
[LIST]
[*]When I try approach #1 ("From the repository"), after adding the repository to my "/etc/apt/sources.list":
[LIST]
[*]When I do "sudo apt-get update", I get:
"[I]W: Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/hardy/cairo-dock/binary-amd64/Packages.gz](http://repository.cairo-dock.org/ubuntu/dists/hardy/cairo-dock/binary-amd64/Packages.gz)  403 Forbidden
E: Some index files failed to download, they have been ignored, or old ones used instead.[/I]"
[*]Then, when I do "sudo apt-get install cairo-dock cairo-dock-plug-ins", I get: "*E: Couldn't find package cairo-dock*"
[/LIST]

[*]When I try approach #2 ("With the deb package (stable)"), when I run "sudo dpkg -i cairo-dock_v1.6.2.3_i686.deb", I get: "*cannot access archive: Permission denied*". I have no idea why.
[/LIST]

I am running Hardy on amd64.

Thanks!

---

### Post by alopecoid on 2008-10-06
I have tried installing the 64-bit *.deb files as well. No luck.

I have also tried compiling from source. After finally finding and installing all the required dependencies, "autoreconf -isvf' said something like "autoreconf: no command found". However "./configure –prefix=/usr" and "make" both worked. Then when I do "sudo make install" says something like "no target found: install".

This is so freaking frustrating.

---

### Post by fabounet on 2008-10-07
consider installing the 32bits packages, there is a clear topic about that.
the 64bits packages maintainer does not maintain them anymore, so for the moment we don't have them, sorry.

---

### Post by alopecoid on 2008-10-07
Hi, Thanks for your response!

I have tried the 32-bit packages as shown in my first post (right? not entirely sure).

When following the instructions, I get the errors that I mention.

I even tried compiling from source... which I actually got to work after getting all the dependencies. However, I'm not exactly sure what to do once it builds successfully. As I said "sudo make install" says something like "no target found". Really, I would only want to build from source as a last resort anyway.

Do you have any other suggestions?

Thanks for your time!

---

### Post by fabounet on 2008-10-08
> autoreconf: no command found
means you have to install autoconf first.

I'm sorry I can't help you more with the 64bits package, I just know that many people could do it with the 32bits packages and getlibs. There is a nice thread here explaining the process.

---

### Post by tnd on 2008-12-02
fabounet is correct, the name of the package is "cairo-dock-plug-ins" not "cairo-dock-plugins". Changed on the wiki.

---

### Post by loomsen on 2008-12-02
Try mine, should work.

---

