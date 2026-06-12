---
title: "i need help  kind of bad"
date: 2008-11-05
forum: General Help
---

### Post by rayz321 on 2008-11-05
i have been trying to find a [SIZE="5"]FREE program[/SIZE] to make animated files how can i do that i tryed gimp if you know a good way to do it please post and also tweening would be nice

---

### Post by steveneddy on 2008-11-05
Gimp

---

### Post by rayz321 on 2008-11-05
> **steveneddy said:**
> Gimp

wtf what do you mean

---

### Post by Scott-271 on 2008-11-05
I have never used it but take a look at [Blender]("http://www.blender.org/").

---

### Post by pirattrev on 2008-11-05
tweening? And also, try to avoid swears on these forums.  What exactly do you need?

---

### Post by damis648 on 2008-11-05
Please just relax a bit. We can try our best to answer your question if we understand what you are asking. What exactly do you mean by "animated file"? This doesn't tell me much. If you are looking to make an animated image, use the gimp, it has that feature. If you want to make an animated 3D movie, have a look at blender.

---

### Post by rayz321 on 2008-11-05
ok what i mean is some thing like this [IMG]http://www.east-cal-pioneers.com/Image/animining_cart.gif[/IMG] ok no 3d like blener

:oops: :oops: um sorry about the hurrying and the cursing :oops: :oops:

tweening is An animation technique that, based on starting and ending shapes, creates the necessary "in-between" frames

---

### Post by zombiepig on 2008-11-05
Try:

Pencil - [http://www.les-stooges.org/pascal/pencil/index.php?id=Home](http://www.les-stooges.org/pascal/pencil/index.php?id=Home)

Synfig - [http://www.synfig.org/Main_Page](http://www.synfig.org/Main_Page)

Hope either of those meet your needs!

(I should add, synfig is available via add/remove programs, pencil has a download for ubuntu on their website)

---

### Post by rayz321 on 2008-11-05
i get this on the first one i got this error and on the second have tryed it it does not oped it just says loading then nothing

oh and i tryed to open it with GDebi package installer

---

### Post by zombiepig on 2008-11-05
Yeah, I just tried synfig from the ubuntu repos and I get the same failed startup. Give me a minute, I'm trying to compile the latest version to see if it helps.

---

### Post by rayz321 on 2008-11-05
ok will do an thanks for all the help so far hope for more to come

---

### Post by zombiepig on 2008-11-05
Ok, synfig works if you compile the latest version. How computer literate are you? There's a few steps to go through:

1. Under system->admin->synaptic package manager. You need to remove the existing version of synfig and all it's parts. Do a search for synfig, and remove anything it finds that's installed (right click and mark for removal). Then do a search for etl, and make sure etl-dev is also removed. Hit apply to make these changes take effect.

2. You need to download the source for the latest version. There's 3 parts to it:
[http://downloads.sourceforge.net/synfig/ETL-0.04.12.tar.gz?modtime=1224707037&big_mirror=0](http://downloads.sourceforge.net/synfig/ETL-0.04.12.tar.gz?modtime=1224707037&big_mirror=0)
[http://downloads.sourceforge.net/synfig/synfig-0.61.09.tar.gz?modtime=1224793932&big_mirror=0](http://downloads.sourceforge.net/synfig/synfig-0.61.09.tar.gz?modtime=1224793932&big_mirror=0)
[http://downloads.sourceforge.net/synfig/synfigstudio-0.61.09.tar.gz?modtime=1224707325&big_mirror=0](http://downloads.sourceforge.net/synfig/synfigstudio-0.61.09.tar.gz?modtime=1224707325&big_mirror=0)

3. These files are all compressed, so you'll need to open each and copy the folder inside to somewhere on your hdd. I usually make a folder called 'Source' inside my home folder for things like this. When you've extracted them all, you should have three folders called ETL-0.04.12, synfig-0.61.09 and synfigstudio-0.61.09

4. Load up a terminal window (applications->terminal) and change to the folder you extracted the file to eg, "cd Source"

5. Enter the following commands, entering your password when prompted:

sudo apt-get build-dep synfigstudio
cd ETL-0.04.12
./configure
make
sudo make install
cd ../synfig-0.61.09
./configure
make
sudo make install
cd ../synfigstudio-0.61.09
./configure
make
sudo make install
sudo ldconfig

6. If all goes well, you should now have a working version of synfig under Applications->Graphics!

7. Read [http://synfig.org/Getting_Started](http://synfig.org/Getting_Started) :P


Let me know if you get stuck at any stage, or if you hit any errors.

---

### Post by rayz321 on 2008-11-06
when i do the first code i get this 
ray@ray-desktop:~$ sudo apt-get build-dep synfigstudio
[sudo] password for ray: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_main_source_Sources - open (2 No such file or directory)
ray@ray-desktop:~$

---

### Post by zombiepig on 2008-11-06
Ok, try a "sudo apt-get update" in terminal first, then the rest of the commands. Let me know how that goes!

---

### Post by gabz8472 on 2008-11-17
Synfig works pretty well for tweening. The only problem I've so far encountered with it is when I upgraded to intrepid. It starts loading then just stops.

---

### Post by Ubuntiac on 2009-01-10
Synfig is definitely what you want. A much easier way than compiling is to just add:
> deb [http://ppa.launchpad.net/stemp/ubuntu](http://ppa.launchpad.net/stemp/ubuntu) intrepid main
to your sources and of course:
> apt-get update && sudo apt-get install synfig

Enjoy!

---

