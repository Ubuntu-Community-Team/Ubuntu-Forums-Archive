---
title: "[SOLVED] Unison Help Needed"
date: 2008-07-15
forum: General Help
---

### Post by jlacroix on 2008-07-15
I set up Unison via [this]("http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html") howto.

It's working, I can synchronize back and forth between my Desktop and Laptop. However, there are a couple of things I need help with.

1.) Firstly, on my Desktop computer, my /home/jeremy/Music folder is a symbolic link. I have Windows XP and Ubuntu installed, and I made the Music folder a symbolic link so both operating systems have the same music. However, when I preview the changes Unison-GTK is going to make, it says "new symbolic link". This worries me. That symbolic link is unnecessary on my laptop, I don't want that symbolic link created on my laptop, I just want it to synchronize the Music folder as if it were local.

2.) Unison takes FOREVER to scan files. Granted, I have over 3000 music files alone (not to mention how many pictures and videos I have to synchronize), but it shouldn't take 15 minutes to check the dates on the files to see if they have changed. Can I speed it up? I don't think it needs to scan the entire files, just the dates, right?

3.) Can I automate this, or do I have to open unison-gtk every time I synchronize? I would like to synchronize on log in to my profile and have a message come up and tell me what it's doing, but if not I'll settle for how it is now.

4.) Since I do a lot of photography, maintaining the date stamp on each file is important. For example, if I have a picture file on my desktop created last year, when I synchronize it to my laptop, my laptops copy should also show the file was created last year.

Here is my Unison configuration file:
```
### ROOT SYNC PATHS ###
 
# first root is my home directory on this laptop
root = /home/jeremy/
 
# second directory is my desktop's home folder over SSH
root = ssh://jeremy@**IP ADDRESS HIDDEN**//home/jeremy/
 
### PATHS TO SYNCHRONIZE ###
 
# gaim/pidgin IM client logs and settings
path = .purple/

# Personal folders
path = Shared/
path = Pictures/
path = Videos/
path = Music/
path = Documents/
path = Roms/
path = .zsnes/
path = Themes/
 
### IGNORE RULES ###
 
# ignore archived backups
#ignore = Path websites/archive/*
```

Any help is greatly appreciated!!!

---

### Post by jlacroix on 2008-07-15
Anyone? :(

I'm especially concerned with Unison wanting to create the symbolic link on my Desktop on my Laptop, I just want the files synced, not the symbolic link.

So the link on my Desktop that points to /home/jeremy/Music, should just be read as a directory /home/jeremy/Music on the laptop.

---

### Post by jlacroix on 2008-07-16
Well I found some info, although this is still not solved.

Apparently this section of the Unison manual deals with what I'm up against:

> Ordinarily, Unison treats symbolic links in Unix replicas as &#8220;opaque&#8221;: it considers the contents of the link to be just the string specifying where the link points, and it will propagate changes in this string to the other replica.

It is sometimes useful to treat a symbolic link &#8220;transparently,&#8221; acting as though whatever it points to were physically in the replica at the point where the symbolic link appears. To tell Unison to treat a link in this manner, add a line of the form

             follow = pathspec

to the profile, where pathspec is a path pattern as described in the Path Patterns section.

However, that makes absolutely no sense to me. Where am I supposed to put "follow = pathspec" and what the heck is a pathspec? I tried a ton of things, for example "follow = /home/jeremy/Music" and nothing works at all.

Hopefully one of you can read the quoted part of the manual above and translate it to me so I know where to put that and what exactly to type in for the file.

Thanks!

---

### Post by jlacroix on 2008-07-17
I think I got it.

---

### Post by xiphosurus on 2008-12-01
Wanted to do the same thing... was lazy and tried to search for help. But no solutions posted. So I spent a few minutes to figure out this solution.

Put this in the .prf file:

```
follow = Path sync/*
```

So...basically whatever symbolic directories in 'sync' will get synced transparently.

OP, next time please post the solutions to your own question! Will definitely help someone out. Thanks.

---

### Post by conscious on 2008-12-01
> **jlacroix said:**
> 2.) Unison takes FOREVER to scan files. Granted, I have over 3000 music files alone (not to mention how many pictures and videos I have to synchronize), but it shouldn't take 15 minutes to check the dates on the files to see if they have changed. Can I speed it up? I don't think it needs to scan the entire files, just the dates, right?

Run unison with the -fastcheck option. It will rely on the modification dates rather than full file contents.

---

