---
title: "Because of iTunes, I have songs in folders that are in folders that are in folders"
date: 2008-10-21
forum: General Help
---

### Post by PsychedelicWonders on 2008-10-21
Alright because I used to use iTunes as my player, it has made so many sub folders for songs and cds etc etc.

i dont care what cd the song was associated with or the album artwork etc.

How can I extract all the songs out of all of these sub folders so I dont have to go into 3984 folders to play a song?

Thanks.

---

### Post by Soupcan on 2008-10-21
I think if you have Rhythmbox, Banshee or Amarok you can import the Music folder from your Ipod. Then you can play them from there. 

You might need to copy over the folder from your Ipod.

---

### Post by linuxluver on 2008-10-21
Ah, yes, the subject of iTunes being stupid once again arises! Oh, I'd say that you should just go into those folders, 
Ctrl-x(cut) the music out, and paste them into My Music or wherever. Your "Trying to install 32, progress bar gets 75% and seems to shut down comp?" thread has a reply.

---

### Post by PsychedelicWonders on 2008-10-21
The problem is, these songs arent on my ipod any more.

they are just in a Music folder that has sub folders for every band, then a subfolder for every album, then like 28 more sub folders until you get to the song.

Opening every one, copying and pasting them into a main folder would literally take days and days and days.

Is there any quick, easy way to just search all music file and move them into a particular file?

---

### Post by RequinB4 on 2008-10-21
> **PsychedelicWonders said:**
> The problem is, these songs arent on my ipod any more.

they are just in a Music folder that has sub folders for every band, then a subfolder for every album, then like 28 more sub folders until you get to the song.

Opening every one, copying and pasting them into a main folder would literally take days and days and days.

Is there any quick, easy way to just search all music file and move them into a particular file?

Install the soundconverter package with

```
sudo apt-get install soundconverter
```

go to applications - sound and video - soundconverter

add all of the files you wish to use

Go to edit - preferences, choose to place and name results as you want them, as well as the output filetype (can be the same as what it is now).  Run it.

Note: This seems like using a hatchet instead of a scalpel, but it works and is useful for good, constant format for song names as well as lets you put your songs in better formats.

---

### Post by sea_monkey987 on 2008-10-21
run
```

find /path/to/parent/music/folder -type f

```
this will list every file in /path/to/parent/music/folder and the sub folders of /path/to/parent/music/folder.  if you want, you can apply filters after "-type f" like
```
-name "*.mp3"
``` to search just mp3 files.



Then, once you check that the file names outputted are correct, run this:
```

find /path/to/parent/music/folder -type f | xargs -I {} cp "{}" /path/to/new/existing/folder/
```

this will copy all the music the new folder.

---

### Post by linuxluver on 2008-10-24
Sometimes you just gotta do what you gotta do.

---

### Post by cyfur01 on 2008-10-24
I would recommend using Amarok. Once you have it installed, add the main music folder to your collection (nothing else), and then, if it doesn't do so automatically, go to Tools->Rescan Collection. This will grab all the songs from the all the folders. Then, after this, click the collection tab to see everything that has been added to your collection.

To organize everything, within the collection pane, click on one file, then press CTRL+A to select all the files in your collection. Then right-click, and go to Manage Files->Organize ### Files. In the new window, check the box for "Custom Format" under "File Naming Scheme", and then modify the string to whatever suits your fancy. Going by what you've said, you'll want something like this:```
%folder/%albumartist/{%track - }%title.%filetype
```Then, before continuing, make sure that the "Overwrite Destination" box is checked. Once Ready, hit ok, and this should tear through everything and clean it up.

If you're paranoid about this not working, create a copy of your music (providing you have storage and patience), and then do this on that working copy.

I've included a couple screencaps to hopefully help you along.

---

### Post by cicatrix1 on 2008-10-24
> **sea_monkey987 said:**
> run
```

find /path/to/parent/music/folder -type f

```
this will list every file in /path/to/parent/music/folder and the sub folders of /path/to/parent/music/folder.  if you want, you can apply filters after "-type f" like
```
-name "*.mp3"
``` to search just mp3 files.



Then, once you check that the file names outputted are correct, run this:
```

find /path/to/parent/music/folder -type f | xargs -I {} cp "{}" /path/to/new/existing/folder/
```

this will copy all the music the new folder.

You're the man.  This is how I would do it, too.  CLI 4tw!

---

### Post by PsychedelicWonders on 2008-10-25
> **sea_monkey987 said:**
> run
```

find /path/to/parent/music/folder -type f

```
this will list every file in /path/to/parent/music/folder and the sub folders of /path/to/parent/music/folder.

So this?...

**/media/storage/my music**   ?

I've attached a screen shot of the master folder properties section...


> 
Then, once you check that the file names outputted are correct, run this:
```

find /path/to/parent/music/folder -type f | xargs -I {} cp "{}" /path/to/new/existing/folder/
```

this will copy all the music the new folder.

**/media/storage/my music -type f | xargs -I {} cp "{}" /media/storage/Master Music/[/CODE]**

is that correct?

Run those two codes with my information in them ?

---

### Post by Corelogik on 2008-10-25
Are there any of the Linux music apps that can just read and use the iTunes playlist format? I would like to just drop my iTunes folder on the new system and then use it as is. 

Call me strange, but I actually like the way iTunes organizes my music,.. most of the time,.. when I find an error I can move and/or rename as needed and iTunes updates its self in the playlist xml file.

---

### Post by Corelogik on 2008-10-25
** Double Post **

---

### Post by PsychedelicWonders on 2008-10-25
Don't get me wrong, I like the way iTunes works, but doubt it will be compatible enough to run in ubuntu.  But I could be wrong.

For now I'd like to just compile eveyrhting into one folder instead of so many sub folders

---

### Post by RequinB4 on 2008-10-26
any linux-based music player you can import directories into your music library - it will scan and look at the song metadata just as itunes does - easiest is exaile, I prefer mpd but it requires configuring

```

sudo apt-get install exaile

```

---

### Post by sea_monkey987 on 2008-10-26
> **PsychedelicWonders said:**
> So this?...

**/media/storage/my music**   ?

I've attached a screen shot of the master folder properties section...




**/media/storage/my music -type f | xargs -I {} cp "{}" /media/storage/Master Music/**

is that correct?

Run those two codes with my information in them ?

whoa! way too many conversations in one thread

almost.
       1. make sure you specify the program "find" at the beginning of those code lines.
       2. also, use the " -type f" filter.  otherwise, you'll copy the sub-directories also.
       3. escape spaces in path names with a \.  so it would be /media/storage/my\ music/ and /media/storage/Master\ Music

two last notes since your music collection is 14 gigs:
        1.  make sure you have the extra free space in /media/storage to duplicate the collection.  :)
        2.  add the --verbose option to the cp program to see what's happening.  so, your final code line to copy the music should like like this:

```

find /media/storage/my\ music -type f | xargs -I {} cp "{}" /media/storage/Master\ Music/ --verbose

```

---

### Post by PsychedelicWonders on 2008-10-28
> **sea_monkey987 said:**
> whoa! way too many conversations in one thread

almost.
       1. make sure you specify the program "find" at the beginning of those code lines.
       2. also, use the " -type f" filter.  otherwise, you'll copy the sub-directories also.
       3. escape spaces in path names with a \.  so it would be /media/storage/my\ music/ and /media/storage/Master\ Music

two last notes since your music collection is 14 gigs:
        1.  make sure you have the extra free space in /media/storage to duplicate the collection.  :)
        2.  add the --verbose option to the cp program to see what's happening.  so, your final code line to copy the music should like like this:

```

find /media/storage/my\ music -type f | xargs -I {} cp "{}" /media/storage/Master\ Music/ --verbose

```

Alright, this is taking me a minute to wrap my head around, so bear with me.

I've got a 500g so i'm good.  :)

What is the purpose of putting the \ then a space?

```
find /media/storage/my\ music -type f -name *.mp3
```

Is that right now?

Then obviously the code you gave me...

```
find /media/storage/my\ music -type f | xargs -I {} cp "{}" /media/storage/Master\ Music/ --verbose
```

That will import all of my music files into the new master music folder?

What about some songs that arent saved in .mp3... there may be a few others... how do I make sure I get them all?

Just figure out what the other common file system that my music is saved under and re-run the same 2 codes? (obviously changing the .mp3 to whatever it may be)

---

### Post by sea_monkey987 on 2008-10-28
the backslash is to let the terminal know that the " " in "my music" is part of the path name and not a new parameter being passed to the program.  it is required.

if you have music in multiple formats (besides i don't itunes stores in mp3 anyway now that i think about), just omit the "-name *.mp3" bit of the command.  without that part, the command will just copy every file.

---

### Post by PsychedelicWonders on 2008-10-30
So what will happen when I run the first bit of code?

Will it pull and trap all of the files in a temp file until I run the second code to place them in?

---

### Post by sea_monkey987 on 2008-10-30
running ```
find /media/storage/my\ music -type f
``` will just list (in the terminal) all the files in your music folder and all its subfolders.  this command is not really necessary.

```
find /media/storage/my\ music -type f | xargs -I {} cp "{}" /media/storage/Master\ Music/ --verbose
``` will do all the copying of the music to the new folder.

---

### Post by PsychedelicWonders on 2008-11-03
```
find /media/storage/my\ music -type f | xargs -I {} cp "{}" /media/storage/Master\ Music/ --verbose
``` will do all the copying of the music to the new folder.[/QUOTE]

Ahh, so just run the one code and it will take care of it all?

Does this copy or move the files?

---

### Post by PsychedelicWonders on 2008-11-03
psychedelicwonders@JohnnyScience:~$ find /media/storage/my\ music -type f | xargs -I {} cp "{}" /media/storage/Master\ Music/ --verbose
find: /media/storage/my music: No such file or directory
psychedelicwonders@JohnnyScience:~$ find /media/storage/my\ music -type f | xargs -I {} cp "{}" /media/storage/Master\ Music/ --verbose
find: /media/storage/my music: No such file or directory
psychedelicwonders@JohnnyScience:~$ find /media/storage/johnny\ science/my\ music -type f | xargs -I {} cp "{}" /media/storage/Master\ Music/ --verbose
find: /media/storage/johnny science: No such file or directory
psychedelicwonders@JohnnyScience:~$ 


I thought I had the file name right?

---

### Post by sea_monkey987 on 2008-11-03
from your screen shot, it looks like the folder is My Music, instead of my music.  so do
```

find /media/storage/My\ Music -type f | xargs -I {} cp "{}" /media/storage/Master\ Music/ --verbose

```
in liux (and unix), the case of the letters matter in file and directory names.  so a file called test and a file called TEST  can be in the same folder.  Make sure Master Music is spelled in that case.  if it still doesn't work, post the output of ```
ls -l /media/storage/
```

also, make sure that your hard drive is still mounted at /media/storage/.

---

### Post by PsychedelicWonders on 2008-11-03
Alright ran that code and got this...

psychedelicwonders@JohnnyScience:~$ find /media/storage/My\ Music -type f | xargs -I {} cp "{}" /media/storage/Master\ Music/ --verbose
xargs: unmatched single quote; by default quotes are special to xargs unless you use the -0 option
psychedelicwonders@JohnnyScience:~$

---

### Post by PsychedelicWonders on 2008-11-04
bump

---

### Post by sea_monkey987 on 2008-11-04
allright, that's because you have an apostrophe in a file name.  when i ran the command here, i didn't get that error.  as soon as i made a file with an apostrophe in it, i get that error too.  bear with me while i try to find a way around this problem.  sorry this is taking so long...

---

### Post by sea_monkey987 on 2008-11-04
```
find /media/storage/My\ Music -type f -print0 | xargs -0 -I {} cp "{}" /media/storage/Master\ Music/ --verbose
```
works on my comp. with filenames that have spaces and apostrophes.  Another thing I just thought of: if some of your music files have the same file name, dumping them into one directory will also cause problems.

---

### Post by PsychedelicWonders on 2008-11-04
No worries my friend, you are the teacher helping me.

What did you actually change in the code to make it look for apostrophes?

That latest code seems to be working, it is going to take a few minutes since there are so many files.

just deleting the old file is the last step.

---

### Post by sea_monkey987 on 2008-11-04
I added the -print0 option to the find command and the -0 option to the xargs command.  before find was outputting the file names one to a line.  with the -print0 command, it outputs them all on one line, seperated by the null character (which is what the 0 refers to).  on the xargs side of the things, the -0 option tells it that the input is separated by the null character.  another effect of the -0 option is that xargs doesn't treat the "\" and the "'" characters specially.

---

### Post by PsychedelicWonders on 2008-11-04
> **sea_monkey987 said:**
> I added the -print0 option to the find command and the -0 option to the xargs command.  before find was outputting the file names one to a line.  with the -print0 command, it outputs them all on one line, seperated by the null character (which is what the 0 refers to).  on the xargs side of the things, the -0 option tells it that the input is separated by the null character.  another effect of the -0 option is that xargs doesn't treat the "\" and the "'" characters specially.


It seems to have worked, but...

Because of the way that iTunes ripped the music, instead of naming the file itself by the artist, it created a folder for the artist, so now when I rip the file out of the folder, all I have is a song name with no idea what artist it is attached to.

Is there anything that can be done about this?

it seems I'm asking for the impossible... but you never know...

---

### Post by RequinB4 on 2008-11-04
> **PsychedelicWonders said:**
> It seems to have worked, but...

Because of the way that iTunes ripped the music, instead of naming the file itself by the artist, it created a folder for the artist, so now when I rip the file out of the folder, all I have is a song name with no idea what artist it is attached to.

Is there anything that can be done about this?

it seems I'm asking for the impossible... but you never know...

Use any ol' tag editor or media player.  I use EasyTag for tag editing but that might be a little high-tech for your needs.  It's in the repos

---

### Post by PsychedelicWonders on 2008-11-05
> **RequinB4 said:**
> Use any ol' tag editor or media player.  I use EasyTag for tag editing but that might be a little high-tech for your needs.  It's in the repos

What will a tag editor do for me?

How would the media player attach the artists name to the file? and save it as such so I can do a quick browse through my files?

---

### Post by RequinB4 on 2008-11-07
> **PsychedelicWonders said:**
> What will a tag editor do for me?

How would the media player attach the artists name to the file? and save it as such so I can do a quick browse through my files?

Most media formats have what is called metadata also called tags - things in the file that tell media players what song it is, what artist/album, etc.  These are different then the filename  A tag editor such as easytag will allow you to view/edit these tags for any media file.  I detail in my first post how to make all the mp3s into the same format such as "artist-title.mp3"

---

### Post by sea_monkey987 on 2008-11-08
I personally would use EasyTag.  However, that program is incredibly new user unfriendly.  I recommend starting a new thread and asking your new question.  Also, please mark this thread as solved.

---

