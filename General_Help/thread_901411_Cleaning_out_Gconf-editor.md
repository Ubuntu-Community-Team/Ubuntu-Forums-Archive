---
title: "Cleaning out Gconf-editor"
date: 2008-08-26
forum: General Help
---

### Post by anotherdisciple on 2008-08-26
I have noticed while tweaking things in gconf-editor that programs that I have removed (Like totem and rhythmbox) still have folders and subfolders. There is nothing in those folders, but I can't delete them.

Is there a program that cleans out your gconf-editor?... or can I delete those folders somehow?

---

### Post by aysiu on 2008-08-26
```
mv ~/.gconf ~/.gconf.old
mv ~/.gconf.d ~/.gconf.d.old
``` should do it.

---

### Post by anotherdisciple on 2008-08-27
Thanks aysiu... one question though...

Won't that clear out all my saved settings for all my programs?

---

### Post by iaculallad on 2008-08-27
Or, try using Synaptic to purge the package that created those folders/subfolders in your gconf-editor setting.

---

### Post by aysiu on 2008-08-27
> **anotherdisciple said:**
> Thanks aysiu... one question though...

Won't that clear out all my saved settings for all my programs?
You're right. Sorry. I misunderstood the question.

What happens when you try to delete the Rhythmbox folder?

---

### Post by kaibob on 2008-08-27
> **anotherdisciple said:**
> ...Is there a program that cleans out your gconf-editor?... or can I delete those folders somehow?

There is a utility called GConf Cleaner, which will do what you want. I tried it some months ago and found it overly aggressive in removing entries to the extent that some applications wouldn't work afterward. So, I would recommend against the use of this utility but thought I would make note of it since you asked.

[http://www.gnomefiles.org/app.php/GConf_Cleaner](http://www.gnomefiles.org/app.php/GConf_Cleaner)

---

### Post by aysiu on 2008-08-27
Do you have a small hard drive?

---

### Post by anotherdisciple on 2008-08-27
No, my hard drive is pretty big... I'm just one of those annoyingly nit-picky kind that likes everything to be the way it should be. haha! I'll try the Gconf-cleaner... 

Back in my windows days I used to clean my registry often and it seemed to make a significant speed difference... Am I right in assuming that Gconf-editor works much like the registry?

This also brings up a thought. You don't have to be root to edit settings in the Gconf-editor. Could someone make a "virus"(not really a virus, because it couldn't send itself to anyone) by hiding some code (maybe in a .deb file) that changes important settings in the Gconf-editor? Because I've seen some pretty important stuff in there... editing frequency scaling and all kinds of power options. It would all be reversible, but might take a long time to reverse.

---

### Post by aysiu on 2008-08-27
You won't see any performance increase by deleting configuration files.

---

### Post by anotherdisciple on 2008-08-27
Not even a tiny bit? I mean, the thought behind cleaning the registry is that the OS has to look for all kind of information constantly in the registry, so the less it has to look through, the faster it will find what it is looking for.

I'm taking it that it doesn't work like on M$ products yet again. I swear... I've been using only Linux at home for over a year now... I still have a junkload to learn.

I want to study the whole boot process soon... I just have to talk myself into reading my "Linux in a Nutshell" section on it. It's complicated from what little I understand right now.


Thanks for the replies!

---

### Post by sdennie on 2008-08-27
> **anotherdisciple said:**
> No, my hard drive is pretty big... I'm just one of those annoyingly nit-picky kind that likes everything to be the way it should be. haha! I'll try the Gconf-cleaner... 

Back in my windows days I used to clean my registry often and it seemed to make a significant speed difference... Am I right in assuming that Gconf-editor works much like the registry?


The similarities of gconf-editor to the Windows registry are mostly cosmetic.  gconf-editor is really just a specialized XML editor and all the local files live in ~/.gconf.  It should be safe to delete files from there as they have default XML schemas that automatically appear there the first time you run an application.

As aysiu said, you won't notice any speed difference by "cleaning" gconf related things as they are essentially just XML files that applications get their configuration from.

> 
This also brings up a thought. You don't have to be root to edit settings in the Gconf-editor. Could someone make a "virus"(not really a virus, because it couldn't send itself to anyone) by hiding some code (maybe in a .deb file) that changes important settings in the Gconf-editor? Because I've seen some pretty important stuff in there... editing frequency scaling and all kinds of power options. It would all be reversible, but might take a long time to reverse.

I suppose it's possible but, it's not very destructive because you can literally erase that directory and the files will magically reappear to their defaults.

---

### Post by aysiu on 2008-08-27
Not even a little bit. If you don't have Rhythmbox installed, there's no reason that Ubuntu needs to look at the Rhythmbox configuration files. I guess you could argue that indexing lists of all your files might take that millisecond longer, but if your processor and RAM can't handle the indexing of an extra text file or two, I think you should just turn indexing off altogether or have it index only when the computer is otherwise idle.

---

