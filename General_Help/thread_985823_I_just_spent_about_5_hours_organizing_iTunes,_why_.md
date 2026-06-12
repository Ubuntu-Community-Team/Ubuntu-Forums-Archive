---
title: "I just spent about 5 hours organizing iTunes, why didnt it transfer to Ubuntu?"
date: 2008-11-18
forum: General Help
---

### Post by PsychedelicWonders on 2008-11-18
I just spent the last 5 hours ripping and editing my main media folder via iTunes & mostly through the E: drive itself.

Why that when I go to the HDD in Ubuntu and go to the main media folder, it shows all of the music folders the same way BEFORE I made all of the changes in iTunes.

What can I do to make Ubuntu reconginze everything I did on the E: drive through my computer in windows?

---

### Post by amp_man on 2008-11-18
Because iTunes' sorting is stored in a registry key or config file $somewhere, not in the music directory itself. Although you can use the same folder for the library, you're still using two different installs of iTunes, you can't configure one install and have the configuration transfer over to the other one. It sucks, but that's the reality of it.

---

### Post by easoukenka on 2008-11-18
I am not sure where itunes stores it but it will 99% of the time be in your home directory drop to terminal and do a ls -la look for something named .itunes or something and that should be all you need

---

### Post by PsychedelicWonders on 2008-11-18
Technically I was in the music directory on my HDD just through windows, not iTunes.

my computer>E:>my music

I edited all files there in windows, yet Ubuntu still doesnt show all the work I did?

---

### Post by PsychedelicWonders on 2008-11-18
bump

---

### Post by Archmage on 2008-11-18
We are really sorry, but the software is from Apple and therefore we can't do anything about it. Tell Apple your problem, but they will only laugh at you. :(

But the good news is, that there are many good programs out there in Ubuntu that will do the sorting for you. E.g. Amarok.

---

### Post by PsychedelicWonders on 2008-11-18
I didnt sort via itunes, I sorted via my HDD through windows.

so it should have transfered over correct?

---

### Post by Mark Phelps on 2008-11-18
When you say you "sorted" your files using "windows", what exactly did you do?

Did you create folders and move the audio files into those folders and now, when you view the drive in Ubuntu, either the folders aren't there or the files aren't in them?

Or did you use a windows-based file manager to change the sequence in which you viewed the files?  This is only an artifact of the file manager; the actual files are not moved around into a different sequence.

If you did the second, the ordering of the files was not actually changed so it would look the same as it did before -- in Ubuntu.

---

### Post by PsychedelicWonders on 2008-11-18
> **Mark Phelps said:**
> When you say you "sorted" your files using "windows", what exactly did you do?

Did you create folders and move the audio files into those folders and now, when you view the drive in Ubuntu, either the folders aren't there or the files aren't in them?

Or did you use a windows-based file manager to change the sequence in which you viewed the files?  This is only an artifact of the file manager; the actual files are not moved around into a different sequence.

If you did the second, the ordering of the files was not actually changed so it would look the same as it did before -- in Ubuntu.


I think I did the 2nd thing.

I went into windows

Then my computer

Then you know how C: shows your main HDD?  Well I have that AND an E: drive because I have a media HDD.

So I went into the E: drive via my computer and then went into the My Music folder that was on my E: drive.

From there I proceeded to edit all of my folders to be much more organized.

So how do I get ubuntu to reflect the work I've done this way?

---

### Post by Mark Phelps on 2008-11-19
OK, if you organized files inside Windows using a file manager, or if you did that using iTunes, in both cases, the file organization is stored inside the Windows tool -- the files aren't physically resequenced.

If you create folders and move the files into them in Windows using a file manager, those same folders will show up in Ubuntu, but the sequence of files in each folder, when viewed in Ubuntu, is set by the file manager you're using in Ubuntu.

If you did the organization using iTunes, I don't know how that works, but I'm guessing that Ubuntu won't see that because the structure used is only resident inside iTunes.

So, basically, you can't get Ubuntu to recognize the iTunes ordering because only iTunes will see that.

If you want the file structure as seen in Ubuntu to look the same as seen in iTunes, you would have to create the directories from Ubuntu and move the files into those directories.  Problem is, I'm pretty sure that would hose up iTunes in the process -- because then, the files would no longer by in the folders they were in when you organized them in iTunes.

---

### Post by PsychedelicWonders on 2008-11-19
Lets take itunes out of the picture.

If I organized them through my HDD's file system in windows, are you telling I need to do the same thing in Ubuntu, that there is no way to make it carry over?

---

### Post by Mark Phelps on 2008-11-19
The organization that "carries over" is the following:
1) Set of directories
2) Files in each directory
3) Hierarchial structure of directories

What does NOT carry over is the sequence of files inside each directory -- because that is an artifact of the file manager you're using.  For example, the files may appear to be in sequence alphabetically by filename, but that is because the file manager you're using sorts its file list in that order.

If you mix upper and lower case letters and "_" (underscores) at the beginning of filenames, you will see that the same set of filenames has a slightly different sequence in Windows than it does in Ubuntu.  In windows, for examples, filenames beginning with "_" are always sorted to the front of the list; in Ubuntu, they are not.

---

### Post by PsychedelicWonders on 2008-11-20
Hmm.  I dont get it, everything else transfered exactly the same.

When I went into windows, I did 2 things, rip about 75 cds and then  consolodated a bunch of folders down.

Now Ubuntu got all of the new folders, but didnt catch the consolodation.

Is there any way for it to do that?

I cant imagine having to manage 2 music files on the same hard drive.

It's double duty and when youre talking thousands almost impossible.

---

### Post by Mark Phelps on 2008-11-24
If you're doing the consolidation using a Windows file manager, Ubuntu should see that -- at least, it does on my multi-boot systems.

If you're doing the consolidation using iTunes, Ubuntu won't see that.

---

### Post by PocketDog on 2008-11-24
iTunes will organise files and folders according to how they're organised inside iTunes' library, but only if iTunes is set to 'organise my library', and the library location is on the E: drive you want to use. Set both in iTunes preferences.

---

### Post by PatrickVogeli on 2008-11-24
why don't you post some screenshots with the differences? I guess it'll be easier to see what you mean.

---

