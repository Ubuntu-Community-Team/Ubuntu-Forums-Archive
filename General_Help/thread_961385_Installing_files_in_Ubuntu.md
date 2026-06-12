---
title: "Installing files in Ubuntu"
date: 2008-10-28
forum: General Help
---

### Post by rmcellig on 2008-10-28
I have been using Ubuntu for about a week now. One of the things I have been struggling with is the way you install files. There seems to many ways to do this. I know in time this will all make sense but for now I would like to know if there is a video I can watch describing how to install files in Ubuntu.

I am using 8.04.

---

### Post by lunarcloud on 2008-10-28
What do you mean by install files?

Create documents? Copy file from a cd or usb disk? install applications/programs?

---

### Post by raedbenz on 2008-10-28
> **rmcellig said:**
> I have been using Ubuntu for about a week now. One of the things I have been struggling with is the way you install files. There seems to many ways to do this. I know in time this will all make sense but for now I would like to know if there is a video I can watch describing how to install files in Ubuntu.

I am using 8.04.
i guess u r talking about installing applications, the easiest way is to use Synaptic manager.
u dont need a video for that i think, check this [link]("http://www.psychocats.net/ubuntu/installingsoftware")
Raed

---

### Post by porteclefs on 2008-10-28
you should read up on the apt-get install utility. it's the easiest way to install applications.

installing things that aren't found and can't be added to your sources.list is a tad bit tricky... but easy enough. 

so, for starters, look into apt-get utility, how to edit your sources.list and then go from there.

---

### Post by porteclefs on 2008-10-28
oh. are you using a GUI?

---

### Post by rmcellig on 2008-10-28
I just watched the excellent screencast video on the Ubuntu site that discusses how to add and remove applications. Helped a great deal. If you say that apt-get install utility is the easiest way I will try it out. I am looking for a GUI solution. Coming from the Mac side, I have little experience with code based stuff if that makes any sense. :)

I just noticed the Gnome Apt Software Manager. Is this the one you mentioned above?

---

### Post by semitone36 on 2008-10-28
> **rmcellig said:**
> I just noticed the Gnome Apt Software Manager. Is this the one you mentioned above?

Im not sure if that is it.  If you go to System -> Administration -> Synaptic package manager you will find it.  On these forums it is referred to as simply "Synaptic"

This is the main way that ubuntu users install packages and it is the first place you should check to find applications you want.  If you still cant find what you are looking for go to [getdeb.net/]("http://www.getdeb.net/") which is like a website for downloadable ready-to-install packages.

These two options should be able to get you the majority of programs that you need.

---

### Post by geirha on 2008-10-28
The easiest way to install applications is through the Gnome Application Installer. That's the program that starts when you go to Applications -> Add/Remove...

The gnome application installer only list a subset of the available packages though, more or less all the GUI applications. If you need to install other software, like command-line applications and libraries, you'll need to use synaptic, apt-get or aptitude or similar.

Common to them all is that they use the same database. If you install an application in Gnome Application Installer, you can uninstall it with synaptic, and vice versa.

---

### Post by rmcellig on 2008-10-28
Thanks semitone36!!

As much as I like Ubuntu and would like to use it as my main OS, there are two apps that I still haven't found the equivalent to in Ubuntu. I'm looking for something similar to these two excellent apps for Mac OS X:


[http://rogueamoeba.com/audiohijackpro/](http://rogueamoeba.com/audiohijackpro/)

[http://store.shinywhitebox.com/home/home.html](http://store.shinywhitebox.com/home/home.html)

---

### Post by rmcellig on 2008-10-28
Thanks semitone36!!

As much as I like Ubuntu and would like to use it as my main OS, there are two apps that I still haven't found the equivalent to in Ubuntu. I'm looking for something similar to these two excellent apps for Mac OS X:


[http://rogueamoeba.com/audiohijackpro/](http://rogueamoeba.com/audiohijackpro/)

[http://store.shinywhitebox.com/home/home.html](http://store.shinywhitebox.com/home/home.html)

---

### Post by semitone36 on 2008-10-28
> **rmcellig said:**
> I'm looking for something similar to these two excellent apps for Mac OS X

Hmmm unfortunately I have never heard of something like your second link but for the **Audio Hijack Pro** is it a recording software? Ubuntu comes with a basic audio recorder (Applications -> Sound and Video -> Sound Recorder or something like that) but if you want something professional try [ardour]("http://ardour.org/").  

I have only recently tried it out so I cant say what it is like but if you want to see it for yourself you can get it [here]("http://www.getdeb.net/search.php?keywords=ardour") OR if you run a 64 bit architecture you can get it [here]("http://www.getdeb.net/search.php?search_distro_id=10&keywords=ardour").

---

### Post by rmcellig on 2008-10-28
Thanks again! I am looking for something that will do scheduled recordings. As for the other app listed, this is software that allows you to do screencast like recordings very easily.

---

### Post by semitone36 on 2008-10-28
Unfortunately I dont know enough on whats out there.  You might want to post a new thread in the "Apple Users" or "Multimedia and Video" subforums.  Im sure someone there will know exactly what you are looking for :)

---

### Post by rmcellig on 2008-10-28
Audio Hijack Pro allows you to do scheduled recordings as well as recording from online straming sites etc... It is one of the most popular pieces of software in Mac OS X.

---

