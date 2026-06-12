---
title: "Need a program that will let me watch a video, take a screenshot &amp; put in slide show?"
date: 2008-09-18
forum: General Help
---

### Post by PsychedelicWonders on 2008-09-18
Alright I want to be able to watch a video in what ever various formats they may be in, pause the video and then take a snapshot of that particular scene of the movie and some how arrange them into a slide show of some sort?

I'd like a higher grade program that can be easy to learn.

I would also like a program that will allow me to take several pictures, layer them ontop of each other and make one complete image.

But also allow me to edit the size and the surrondings of the picture before i super impose it onto the main layer.

Does this make sense?

I've heard about _Ubuntu Studios_, does this program allow me to do what I want?

---

### Post by silverglade00 on 2008-09-18
For the layering and image manipulation part, you can't do much better than Gimp. It is installed by default. It is easy to do simple things and you can keep learning new features as you go along.

For the screenshots, you could try using Alt+PrtScrn, but it may not work with video overlays. I haven't tested that yet.

Ubuntu Studio will have lots of programs for manipulating video and audio, but might be a little overkill for what you are doing. On the other hand, it might contain the right mix of software that you need.

---

### Post by ju2wheels on 2008-09-18
You can take snapshots while watching a movie in Movie Player (Totem) by pressing Shift+S.

Then for layering, as has already been suggested you can use Gimp.

You dont need Ubuntu Studio, unless you are doing full fledged mutlimedia development. The above two programs should be available in regular Ubuntu by default.

---

### Post by PsychedelicWonders on 2008-09-18
> **silverglade00 said:**
> For the layering and image manipulation part, you can't do much better than Gimp. It is installed by default. It is easy to do simple things and you can keep learning new features as you go along.

For the screenshots, you could try using Alt+PrtScrn, but it may not work with video overlays. I haven't tested that yet.

Ubuntu Studio will have lots of programs for manipulating video and audio, but might be a little overkill for what you are doing. On the other hand, it might contain the right mix of software that you need.

Is GIMP like Photoshop then?  Why is it called Gimp?  thats an odd name?

So this program will allow me to stretch or reduce pictures and then layer them on top of each other, but is there a walk-thru in Gimp that explains how exactly  to do layering?

I've never done any photo editing, but would really like to get into it.

Perhaps I will look into Ubuntu Studio first, if it offers many different angles of programs that are a little bit more "professional", this is what I'm looking to do.

But Ubuntu Studios is kind of an "all-in-one" program that will do everything I'm asking?

When i take snapshots, is there a particular file type I need to save it in, in order to have the easiest, most effective time editing them?

---

### Post by ju2wheels on 2008-09-18
Yes it is like Photoshop. GIMP = Gnu Image Manipulation Program (I think, dont remember).

There should be layering tutorials all over the net, however if you know Photoshop you wont have a problem with GIMP at all.

No Ubuntu Studio is not a "program". It is simply regular Ubuntu with many useful multimedia packages already installed for you. Each program will do a particular task. Many of these you can install on a basic installation of Ubuntu through Synaptic. 

No, not really, but typically you will want to use png or jpeg. The only time when format might be an issue is when you need to include transparency in the photo. Most photo editing programs, especially GIMP should be able to handle any image format you throw at it.

---

### Post by PsychedelicWonders on 2008-09-18
> **ju2wheels said:**
> Yes it is like Photoshop. GIMP = Gnu Image Manipulation Program (I think, dont remember).

There should be layering tutorials all over the net, however if you know Photoshop you wont have a problem with GIMP at all.

No Ubuntu Studio is not a "program". It is simply regular Ubuntu with many useful multimedia packages already installed for you. Each program will do a particular task. Many of these you can install on a basic installation of Ubuntu through Synaptic. 


I am not really familar with photoshop, but I'm a quick learner.

So do I need to un-install the version of ubuntu I am using and re-install ubuntu studios, or am I able to just add the "studio" part to my current 64 ubuntu?

If so, what is the code I need to enter in the terminal to get this?

---

### Post by ju2wheels on 2008-09-18
I really think installing Ubuntu Studio is truly overkill. For what you are trying to do, you will not use even a fraction of the software you will be installing. But if you want to go ahead with this anyway, then go to System->Administration->Synaptic Package Manager. Once it opens, click search and type "Ubuntu Studio" and all packages related to setting it up completely should come up (I say should because I dont know what packages are available on 64bit Ubuntu).

This will install *everything* related to Ubuntu Studio in a terminal, again I really think its overkill but here it is:

```

sudo apt-get install ubuntustudio*

```

I would suggest looking into it more before moving forward with that. Thats a lot of wasted space if you wont be using a majority of those packages.

---

### Post by PsychedelicWonders on 2008-09-18
Yeah I'm not jumping into anything right yet, my computer is gonna be down for a week or so anyways, I had a bad video card and had to send it back.

Just doign research now.

But what about that program is overkill?

I'm not saying I wouldnt get into other things as time goes on...

---

### Post by PsychedelicWonders on 2008-09-18
**Graphic design and modeling applications** including The GIMP, Inkscape and Blender. Along with plugins like dcraw to help with RAW camera files and wacom-tools for people with Wacom drawing tablets

This is what apparently comes in the package for graphics, are that many programs really needed to play with graphics?  

Or are they all the same kind of program, just a different "name brand"?

same goes with movies...

PiTiVi, Kino, Cinepaint are included for **video creation**. We hope to provide a creative environment to people as well as give a spotlight to some amazing open-source applications.

Do those all do something different, or are they all similar, just different brand names?

---

### Post by ju2wheels on 2008-09-18
What I meant was from the perspective of not using a lot of the components. 

In general, you can compare installing Ubuntu Studio to say installing MS Office, Adobe Creative Suite, and MS Visual Studio. Would you really need to install all of MS Office if you just need Powerpoint and wont be using Word, Access etc.

Typically people research which applications they need for a task (in your case applications that are included in Ubuntu Studio) and just install those individual components on their regular Ubuntu distro.

Im not at all telling you dont install Ubuntu Studio, as by all means its a learning experience to see what applications are available if you are unaware. Its just that im more of the type to search for that one application instead of a suite.

---

