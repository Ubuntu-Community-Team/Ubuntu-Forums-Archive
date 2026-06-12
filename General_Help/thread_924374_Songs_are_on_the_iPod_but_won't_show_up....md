---
title: "Songs are on the iPod but won't show up..."
date: 2008-09-19
forum: General Help
---

### Post by RudiePoo on 2008-09-19
I was wondering if anyone could help me out... I've been trying to be able to manage my music on my iPod Touch with gtkPod and everything seemed to be going fine except once I was done adding the songs I wanted, I ejected my iPod and went to go check it out and there wasn't any music on it... I mounted my iPod back up and then browsed it rather than opening it with gtkPod again.  I searched and found that in iPod:/iTunes_Control/Music there are about 13 folder labeled F00, F01, F02, etc... And in these folder were my music, however, my music still doesn't show up when I go to listen to it on my iPod.... Anyone have any ideas?

btw, I'm running Ubuntu 8.04

---

### Post by timcredible on 2008-09-19
if you unplugged the ipod without doing an unmount of the device first, then the database file didn't get written to it and now it doesn't know where the files are, even though the files exist.  try using gtkpod again and get it to write the database file again (maybe add or remove 1 song to get it to re-write the database file).

---

### Post by dfreer on 2008-09-19
This sounds like it might be your problem, there is a fix for it:
[http://ipodminusitunes.blogspot.com/2007/09/apple-cuts-us-off.html](http://ipodminusitunes.blogspot.com/2007/09/apple-cuts-us-off.html)

---

### Post by RudiePoo on 2008-09-19
> **timcredible said:**
> if you unplugged the ipod without doing an unmount of the device first, then the database file didn't get written to it and now it doesn't know where the files are, even though the files exist.  try using gtkpod again and get it to write the database file again (maybe add or remove 1 song to get it to re-write the database file).

*slaps forehead* I think this might have been the problem. I ejected it from gtkpod, but I don't remember putting in the unmount command.... I'll try copying the songs over again and try using the command this time and see how that goes :P

Thanks for the quick responses guys!

---

### Post by RudiePoo on 2008-09-19
I tried putting the songs back on the ipod and making sure to use the unmount command, but the songs still won't show up....

---

### Post by HermanAB on 2008-09-19
The database corruption problem of the iPod is the reason why I will never recommend that POS to anyone.  Why it cannot just list the files without needing a gawddamn database is beyond me.

Anyhoo, that being said, gtkpod does have the ability to rebuild the database.  I cannot remember anything about it, but I have done that on occasion for a friend with an iPod.  Soooooo, have a careful look through the gtkpod menus and things - the solution is in there Sculley...

Cheers,

Herman

---

### Post by RudiePoo on 2008-09-19
Thanks Herman, I looked and there was an option under the File menu to Check iPod Files.  It's still processing but the songs are now popping up in gtkpod.... Looks like this might work :D

---

### Post by RudiePoo on 2008-09-19
Nope, no luck... Still doesn't see the songs.... :(

---

### Post by oxboood on 2008-09-19
Rhythmbox has always worked flawlessly for me. Try that out.

---

### Post by treymul on 2008-09-19
That sounds like a problem I had with amarok.  See if maybe this helps.

[http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music]("http://amarok.kde.org/wiki/Media_Device:IPod#My_iPod_does_not_show_any_music")

---

### Post by RudiePoo on 2008-09-19
I can't get Rhythmbox to see my iPod and I just tried manually setting the FirewireGuid but it still doesn't see the songs....

Update:  I just Deleted my whole iPod_Control directory and rebuilt it creating another SysInfo file and it *still* will not see the songs...

---

### Post by RudiePoo on 2008-09-19
I just tried switching over to Amarok and I was able to add the iPod and add music to it but it still doesn't see it...

---

### Post by RudiePoo on 2008-09-20
Alright, this is getting *really* frustrating.... I mounted my iPod and opened up my terminal and entered:
```
sudo lsusb -v | grep -i Serial
```

And I got this for the output:
```

  iSerial                 3 d14af04050950205a404041764a013fa8f73c0d4
  iSerial                 1 0000:00:0b.1
  iSerial                 0 
  iSerial                 0 
  iSerial                 0 
  iSerial                 1 0000:00:0b.0

```
 
I opened my SysInfo file found in /media/ipod/iPod_Control/Device and edited it to look like:
```

ModelNumStr: xA623
FirewireGuid: 0xd14af04050950205

```

And the iPod ***still*** continues to not see my music...

---

### Post by dfreer on 2008-09-21
> If you can't sync files yet, grab the latest libgpod from SVN or get libgpod 0.6.0 and compile it, install it and finally compile Amarok against it. 

Did you try this yet?

---

### Post by RudiePoo on 2008-09-21
What does it mean by compile Amarok against it?  I installed libgpod-0.6.0 and then installed Amarok, but it didn't seem to help...

---

### Post by dfreer on 2008-09-22
> **RudiePoo said:**
> What does it mean by compile Amarok against it?  I installed libgpod-0.6.0 and then installed Amarok, but it didn't seem to help...

I haven't done this myself, but from compiling other programs I'm guessing that they want you to download the development libraries of libgpod-0.6.0, and then downloading/compiling amarok, which would then use the latest libgpod libraries while compiling. (hint: sudo apt-get install build-essential and sudo apt-get build-dep amaroK).

But the iPod classic has been out for a while now, along with the fix to keep the database from locking up. I'd imagine that there is a precompiled binary out there, or some better solution than compiling amarok.

---

### Post by RudiePoo on 2008-09-22
But would the songs not showing up on my iPod be a problem with Amarok?  I can add songs to my iPod fine and it comes up in Amarok fine, just when I go to listen to the songs on my iPod they don't show up, but I know they're there because I can see them when it's connected to Amarok...

---

### Post by dfreer on 2008-09-22
Yes. If you had read the article I posted, you'd notice the problem is with the iPod itself. I don't think this isn't a "corruption" issue, or a misbehaving program not correctly adding songs to your iPod. This is an intentional lockout feature by Apple. 

From what I understand of it, on the new iPod's they take a hash of the database, and if any program modifies the database (e.g. amarok, rhythmbox) without recomputing the hash, when you go to use your iPod it will refuse to play or even see your music (you can notice it's still there, because it doesn't actually delete your music, just refuses to see it).

I bought my iPod classic right when it came out. Synced a movie to it, brought it to my sister's Ubuntu machine and simply copied the movie to my sister's hard drive. Didn't add music/sync/nothing besides that (opened amarok to find the movie). And suddenly my iPod is telling me I have 30 GB's used but absolutely no songs.

The only thing I'm concerned about is that they figured out the hash issue a while ago (before 8.04 ubuntu I'm pretty sure), and why hasn't Amarok/Ubuntu been upgraded? There should be a ton of threads out there with this same issue...

---

### Post by RudiePoo on 2008-09-22
> **dfreer said:**
> Yes. If you had read the article I posted, you'd notice the problem is with the iPod itself. I don't think this isn't a "corruption" issue, or a misbehaving program not correctly adding songs to your iPod. This is an intentional lockout feature by Apple.

Yes, I understood that.  In other threads I've read, it seems like the solution was to manually put in the FirewireGiud into the SysInfo file, which I've done.  That seemed to fix it for most people...  I ended up restoring my iPod with iTunes and then modding it again and trying to get it to work with Ubuntu again, but I get the same thing, no songs.... However, I did notice that the FirewireGuid had an 'n' at the end of it making the whole string 19 characters (including the '0x').  Which I thought was kind of strange since if I do```
sudo lsusb -v | grep -i Serial
``` I get```
d14af04050950205a404041764a013fa8f73c0d4
``` So the next character would be an 'a'.  There is no 'n' in the string...  I tried removing the 'n' but it didn't seem to help....

---

### Post by blacksheep31 on 2012-12-25
Hey, I know this is an old post, but I am having the same exact issue as you and have been all over the web trying everything I can find to fix it. Did you ever find a way to get it to work?

---

