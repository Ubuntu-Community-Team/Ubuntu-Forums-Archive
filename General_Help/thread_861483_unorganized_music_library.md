---
title: "unorganized music library"
date: 2008-07-16
forum: General Help
---

### Post by Sasa_Ivanovic on 2008-07-16
I have a library of songs that's really big and messy. The problem is that most players won't find my songs when i search for them ( i have tried amarok, exaile, banshee, rhytmbox ). It seems these players require that the library is organized in certain way.

What can i do in this situation?

Fixing this is as simple as adding the song file path to the search properties ( which is ignored in all players for some reason ).

Is there any plugin or something for this, or any kind of solution... ( except running winamp via wine :( )

---

### Post by evets25 on 2008-07-16
Most music players have their own library for music that it organizes in a folder in a special way. Just sticking your music in this folder may or may not cause the music player to detect it, you usually need to import it. I know with rhythmbox, for example, you can tell it to make *this* folder be your music collection, and then tell it to keep it organized, and then tell it to import your music from *that* folder, and it will automagically copy your music over whilst organizing it in nice little folders and whatnot. Most music players have this sort capability. Is this what you're talking about?

---

### Post by jonian_g on 2008-07-16
Try "Listen Music Player". Really nice player. It's in the repositories. To import your music go Music>Import folder or Music>Preferences and on the Library tab choose your music library location.
For an alternative to Winamp, install Audacious.  It's in the repositories. It is compatible with Winamp skins.

---

### Post by Sasa_Ivanovic on 2008-07-17
You're assuming that i'm rather stupid... i have tried all of that.
Anyhow i found this player ( the only one ) that is able to search the path of the songs too : [http://www.sacredchao.net/quodlibet/](http://www.sacredchao.net/quodlibet/)
it's really neat, except that you can't resize the queue.

---

### Post by hyper_ch on 2008-07-17
amarok can filter its library on many options... but first you need to tell amarok where you actually have some music files that it then can scan and add and organize.

---

### Post by Sasa_Ivanovic on 2008-07-17
there's this combination of audacious and methlab too.

that's about it i guess. I'm satisfied with this.
songbird sucks ***.

---

### Post by Sasa_Ivanovic on 2008-07-17
> **hyper_ch said:**
> amarok can filter its library on many options... but first you need to tell amarok where you actually have some music files that it then can scan and add and organize.

still assuming that I'm stupid, fine.

---

### Post by logos34 on 2008-07-17
Amarok does a good job of finding stuff, in my experience.  But like hyper_c says, you have to configure the [collection tab]("http://docs.kde.org/development/en/extragear-multimedia/amarok/configure-collection.html") to point to the directories where you want it to scan for music files.  It will automatically update when new songs are added if you enable recursive scan option.  You even have a choice of databases (sqlite is default, mysql or postregsl for really huge collections of music).  

The [search filter dialog box]("http://amarok.kde.org/wiki/Keyword_Filtering") is offers quite a few patterns.

---

### Post by hyper_ch on 2008-07-17
> **Sasa_Ivanovic said:**
> still assuming that I'm stupid, fine.

That is your interpretation of the comments of people that try to help you... so it works for me and others... it does not work for you... what does that tell you?

Besides, such comments as yours are not necessarily especially when others try to help you...

---

### Post by Sasa_Ivanovic on 2008-07-17
you still don't understand my problem do you.

i know all that's been said here.
amarok won't find some stuff and some will, 'cause the music isn't ORGANIZED properly.
amarok ( and other players ) don't search the path of song, only the tags. As for my tags they are empty, so it can't find any songs based on their names or the folders where they reside.

it seems to me you haven't even bothered to read and understand my posts, since most of users here are total n00bs.

As i said above, (and i'm saying this only to help others with similar problem) there are two programs capable of "winamp like" searching :
MethLab
Quod Libet

---

### Post by Sasa_Ivanovic on 2008-07-17
> **logos34 said:**
> 
The [search filter dialog box]("http://amarok.kde.org/wiki/Keyword_Filtering") is offers quite a few patterns.

can you somehow include the path of the song in the search?
that's basically all i need.

---

### Post by jonian_g on 2008-07-17
I know what you can do. Organize your library with a tag editor.
Though I have better solution for you, right click on your music library and delete ;)
Since we are noobs we can only propose stupid solution. Well this is a smart one. Will save you from a lot of trouble and effort. Start listening to radio, it doesn't need to organize it.

---

### Post by Sasa_Ivanovic on 2008-07-17
:)

---

### Post by hugmenot on 2008-07-17
Sasa, I hear you. They are the Amarok robots. Or the Igor Amarovian dogs.
Still, you're a lazy bum for not tagging your stuff.

*tagging this as recurring discussions*

BTW: [http://wiki.banshee-project.org/OnePointEx/Search](http://wiki.banshee-project.org/OnePointEx/Search)
scroll down to List of Fields.

---

### Post by Sasa_Ivanovic on 2008-07-17
ok, i just discovered mpd, it rocks.

banshee is cool, but it doesn't include path field by default. or does it. i must try this out a little more.

---

### Post by Sasa_Ivanovic on 2008-07-17
I have a few problems with banshee ( when i start it a warning pops up about dbus or something, and when i try to delete files from library the app crashes ), i won't bother to fix them, 'cause mpd really rocks ( i'm using mpc client )

i have dreamed of using grep to filter the search results and pipe it to mpc add ... :D

---

### Post by Archimedes0212 on 2008-07-17
okay, you say it is unorganized.  How is it unorganized?  How do you have your song files stored on your computer?  

I personally have them lumped all into one folder, which to me is classified as 'unorganized'.  However, I use amarok and once I tell it to search in my Music folder for songs, it does, it loads all of my songs and I happily listen.

Instead of assuming we are ignorant, assume we do not possess clairvoyance, and describe your problem in a little more detail.

---

### Post by jonian_g on 2008-07-17
> okay, you say it is unorganized. How is it unorganized?

He means that they don't have tags.

> Instead of assuming we are ignorant, assume we do not possess clairvoyance, and describe your problem in a little more detail.

+1

---

### Post by hugmenot on 2008-07-17
> **jonian_g said:**
> He means that they don't have tags.



+1

-1

Just because you can&#8217;t read his post properly and just dump your senseless share of Amarok evangelium here doesn&#8217;t mean he has to be grateful to you.

---

### Post by lisati on 2008-07-17
> **Sasa_Ivanovic said:**
> 
amarok won't find some stuff and some will, 'cause the music isn't ORGANIZED properly.

If this was a Windows forum, I'd suggest using Media Monkey. According to Google, there's howtos on using it with Linux under Wine.

---

### Post by jonian_g on 2008-07-17
> unorganized music library 
I have a library of songs that's really big and messy. The problem is that most players won't find my songs when i search for them ( i have tried amarok, exaile, banshee, rhytmbox ). It seems these players require that the library is organized in certain way.

What can i do in this situation?

Fixing this is as simple as adding the song file path to the search properties ( which is ignored in all players for some reason ).

Is there any plugin or something for this, or any kind of solution... ( except running winamp via wine  )

So smartass, can you understand from that, that he doesn't have his music files taged? If yes, then you are genious and the rest of us stupid.

I never said I use amarok and never recommended it. Read the post from the begining!

And when you ask for help you don't react like this:

> You're assuming that i'm rather stupid... i have tried all of that.
> it seems to me you haven't even bothered to read and understand my posts, since most of users here are total n00bs.

Suggestions are free of charge. Take them or leave them.

---

### Post by jonian_g on 2008-07-17
And since you understood his problem, where is your solution?

---

### Post by lisati on 2008-07-17
Just a thought: What kind of files are they? MP3? WAV? OGG? Something else? If the files have "standard" names with the file type as part of the file name, then most music software should be able to find them once you've told it to scan your disks.

---

### Post by hugmenot on 2008-07-17
> **jonian_g said:**
> So smartass, can you understand from that, that he doesn't have his music files taged? If yes, then you are genious and the rest of us stupid.


Wait, let me see ... Yes!?

---

### Post by jonian_g on 2008-07-17
Great! You're genious! Now do a backflip and tell me what this means: "Pidhin e sateme":popcorn:

---

### Post by cariboo on 2008-07-17
To help get your "unorganized music files" organized you might want to have a look at **picard**. It is in the repositories. I tried it when it was still in beta and it worked quite well.

Jim

---

### Post by hugmenot on 2008-07-18
> **jonian_g said:**
> Great! You're genious! Now do a backflip and tell me what this means: "Pidhin e sateme":popcorn:

Albanian? Greek?

Must be something similar to [what is listed here]("http://www.cracked.com/article_16275_9-most-devastating-insults-from-around-world.html")

---

### Post by jonian_g on 2008-07-18
_

---

