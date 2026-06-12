---
title: "CD Ripper That Can Reat CD Text?"
date: 2008-11-07
forum: General Help
---

### Post by rfroemming on 2008-11-07
I have done some searching, but have come up empty handed.  I would like a CD ripper that can read the CD Text from the CD.  Are there any graphical ripper programs that will do this.  I used Audiograbber windoze and would like to find something comparable in Ubuntu.

Thanks for any help!

---

### Post by ragtag on 2008-11-07
I'm not sure what you mean by read text, but if you mean info about the songs, such as artist etc. you have multiple options.

Rhytmbox will try and fetch titles, album and artist names from the internet on inserting a cd, and name your files accordingly when you rip. There are also a plugins for fetching lyrics and cover art.

MusicBrainz Picard goes a step further. It can actually identify songs based on the sound, and compare that to an online database to fetch the info. Though I'm not sure if it does ripping, it can always be run on the files afterwards to add id3 tags.

I believe there are many more options, those are just two I've tried.

---

### Post by rfroemming on 2008-11-07
Hello,

Thank you for the reply.  Unfortunately since the CD's I am trying to rip, they often times arent in an online database, such as CDDB, FreeDB, MusicBrainz, etc...   They are promo compilation disks and contain CD Text, which is basically the artist and title information already on the CD, so if the ripping program can read this, it will name the tracks even if there is no database information available.  I may have answered my own question by looking for a definition of CD Text:
[http://en.wikipedia.org/wiki/CD-Text](http://en.wikipedia.org/wiki/CD-Text)

There is a list of software here and it looks like X-CD-Roast is a linux program that can read CD Text.  It appears to be more of a burning program, so I'm not sure if it will work for ripping, but I will give it a try.

If anyone else has any suggestions, that would be great.  Might be forced to use Audiograbber under wine for this task.

Thanks!

---

### Post by editrix on 2008-11-08
I'm almost positive K3B can do this, in that once, when I was not online, I put in a CD to rip and the text--that is, track titles and artists--showed up just as if I had connected to cddb.

K3B can rip, copy, burn, change from wav to mp3 or ogg ... It doesn't make coffee, but that's about all it can't do :-)

---

### Post by rfroemming on 2008-11-08
Yes, you are correct.  K3B does read the CD Text.  But now I have run into another problem.  The CD Text is formatted Title - Artist, and I like my files named Artist - Title.  It would be fine if the artist and title information were separate, then I could format the filename %A - %T, but they have all of the information under %T, so no matter how I format it I get Title - Artist because of the way the Text is formatted.  Audiograbber had a handy feature that would reverse artist and title information by the click of a button.  I am so close, but may be forced to use Audiograbber.  I suppose I could rip the tracks and use a file rename program to format them the way I want, its just that Audiograbber made things so easy.

Thanks for the help!

---

### Post by editrix on 2008-11-09
I don't have access to my K3B at the moment, but I'm pretty sure that under File Naming there's a drop-down menu that gives you choices. Also, you may be able to rewrite the whole string yourself--that is, input your own string.

Click around in it. K3B is amazing.

---

