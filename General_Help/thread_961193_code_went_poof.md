---
title: "code went poof"
date: 2008-10-28
forum: General Help
---

### Post by Hrairoo on 2008-10-28
And so now I'm here, to tell my story and hope someone has a suggestion to save my ****.

Today I was working on a final version of a product we have been developing for over 2 years now. There were some few glitches still in need of squishing, so naturally I got my self connected on sftp over nautilus on the remote developing server, and started to fix the glitches. 

One of witch was a bug in the image manipulation engine that resized the image infinitively. I managed to fix the bug and moved on to the next thing, while forgetting to kill the process that was still resizing the image in the background. 

And then after a hour or so, disaster.... A collection of things that can go wrong, did go wrong. 

I wanted to save a source file critical for the project. Right after saving the code editor asked me if I wanted to reload the file since the one on the disk drive is newer then the one I have in cache, so I thought the editor acted a bit weird, but thought nothing of it and clicked yes.

After reload :shock: the file was empty, no code in it. Slight panic in me arose. My first action to the reaction was "ctrl+z" resulting in nothing, next was edit -> undo, but it was grayed out. Next I logged on the server checked the file, 0b! Now panic was getting a hold of me. But I thought ok we make backups every day, only about 4 hours of work went bye bye, and besides I still know the fixes I made today, so I called the system admin responsible for backups. After a short but loud conversation (with a lot of offensive words) I found out that because the project was being developed on a new, isolated and for the time being dedicated server for this particular project, that the backups weren't being made regularly actually as I found out  later, the guy didn't set up backups at all. 

And now I'm here, without the file, the code and any backup, so what to do... I went to find out what went wrong. What was the cause of the file going *poof*.... you know the back process I mentioned earlier, well it was creating a temp file in the /tmp/ folder using up all the free disk space. As I tried to save the file, nautilus tried to upload the changes, while overwriting the file I was saving the server ran out of disk space so nautilus couldn't save the file anymore, resulting in a 0b file on the server. 

Since the backprocess was constantly writing on the disk, until I killed it later on, there was no use in running any data recovery. 

Any ideas on how to get the file back (can't find it in /tmp/ on my work PC and nothing in the server /tmp/ ... *doooh* no free space for tmp files). Or how to recode about 10k+ lines of code in 5 hours.    
 

Thanks for any help and see ya soon in a homeless shelter near you.

---

### Post by geirha on 2008-10-28
You guys should seriously consider looking into version control. Editing files with 10k lines of code without version control is beyond crazy. But, which editor were you using?

---

### Post by SteveHillier on 2008-10-28
I cannot help with the problem but why are you writing 10K lines of code in a single file (with or without version control)?
In my programming days there were some unwritten rules.
If a function went over a single screen split it
If a file went over 500 lines split it
If you find yourself cutting and pasting turn it into a function
If the indents go above 4 or 5 levels split it
It may seem picky but it does help to avoid the sort of disaster you are experiencing

---

### Post by ad_267 on 2008-10-28
I don't know how this works when working over sftp but for local files some text editors save backups with a ~ in front of the name. Also not sure if there's a size limit on the files. Only thing I can think of sorry.

---

### Post by Hrairoo on 2008-10-28
Well there is no version control because none of the suits give it any credit, so no one sets it up and no one uses it. System admins are students, and there you have it.

As of splitting the file in small ones... good idea, but we usually have all the related functions in the same file so you include one and have all that you need in it (and what you don't need as well, but... lazy bums do lazy things...). I guess from now on, files are gonna be split, just like other things, like my head...

I code in Geany


p.s.: I found a backup I made for my self in march. So I have some code back...

---

### Post by geirha on 2008-10-28
Suits with no experience in software development leading a software development project. Sounds promising :)

Haven't used geany myself, but perhaps someone else here knows if geany stores backup copies anywhere. One thing you could try is to recursively grep for a known string in the code. Let's say you have a function called super_function in your missing code-file, then try
```
grep -rw super_function ~
```
If it doesn't find anything in ~, try the same command on /tmp. I have my doubts, but worth a try.

---

### Post by ju2wheels on 2008-10-28
> **ad_267 said:**
> I don't know how this works when working over sftp but for local files some text editors save backups with a ~ in front of the name. Also not sure if there's a size limit on the files. Only thing I can think of sorry.

That should be the case, but only if the application  he was using to edit the file does autosave, and it would also most likely be on the local machine and not the remote one (if he trasnfered the file and then opened it) or on the remote machine if the application was running on the remote machine through ssh. And the tilde would be at the end of the file name, not the beginning.

---

### Post by ad_267 on 2008-10-28
Oops my mistake, yes the tilde is at the end of the file name. They are also hidden in nautilus so you have to turn on showing hidden files. I'm pretty sure both vim and gedit do this, don't know about other editors.

---

