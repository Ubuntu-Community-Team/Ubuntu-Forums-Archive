---
title: "If I rip in Ubuntu, will it automatically populate in iTunes in windows?"
date: 2008-11-17
forum: General Help
---

### Post by PsychedelicWonders on 2008-11-17
I have an iPhone finally and will be using it to its fullest extent.

Now I have a bunch of cds I would like to back up and make digital on my computer.

I also want these cd's to all be available in iTunes and Ubuntu in an equal manner.

So should I rip in Ubuntu or iTunes?

I guessed I'd rather rip in Ubuntu since I use it more often and just somehow have it to where iTunes will see all the new files next time I start up iTunes and autopopulate them into the main list.

Now mind you I have a 3rd HDD I use for media and both Ubuntu and Windows are linked up to it, but I want to make sure I'm set up so I can rip once and auto-populate in all categories on both OS.

---

### Post by PocketDog on 2008-11-17
I rip (with EAC but the ripping app isn't important) and import into iTunes. I have iTunes set to import tracks to, and organise, my library, which it does using the id3 tags. I'm obsessive when it comes to id3 tags... in Ubuntu, Rhythmbox uses iTunes' library as its own library. So, to answer your question, all my music is in one place (organised by iTunes) and it's all automatically scanned and accessible by Linux without any input from me. There may be easier or better ways, but this is my way, and I'm drunk. Hurray!

---

### Post by PocketDog on 2008-11-17
By the way, I do it this way round simply because iTunes doesn't scan its own library when started; it will only notice library changes when the tags are read by it, or it attempts to play a file.

---

### Post by PsychedelicWonders on 2008-11-17
> **PocketDog said:**
> I rip (with EAC but the ripping app isn't important) and import into iTunes. I have iTunes set to import tracks to, and organise, my library, which it does using the id3 tags. I'm obsessive when it comes to id3 tags... in Ubuntu, Rhythmbox uses iTunes' library as its own library. So, to answer your question, all my music is in one place (organised by iTunes) and it's all automatically scanned and accessible by Linux without any input from me. There may be easier or better ways, but this is my way, and I'm drunk. Hurray!

Alright so a few questions,

Does iTunes import automatically, or do you still have to manually do it?

You rip with iTunes then?

What is EAC?

I dont use rhythmbox, but if it is familar like iTunes and organizes like that, I'd prefer to have my music saved one way and I'll be using iTunes a lot because of my iPhone.

I think I have rhythmbox, but how do I tell if I have the latest version?

---

### Post by PocketDog on 2008-11-17
You have to import manually with iTunes. EAC is Exact Audio Copy, a Windows CD-ripper program for audiophiles. No other OS has its equivalent unfortunately, although iTunes will rip CDs perfectly well. When Rhythmbox starts it will scan its library and when you browse you know it'll be up to date. iTunes won't scan its library, it will only look at items you are examining or modifying and update them accordingly. So I can do what I want in iTunes and my music via Linux is unaffected. If I messed about with the same folder using Linux then iTunes would have a massive fit and put "(!)" everywhere.

---

### Post by PsychedelicWonders on 2008-11-17
ahh.

So basically just rip and edit any music file in windows since its a cry baby and linux will compensate and adapt?

---

### Post by PocketDog on 2008-11-17
Yes, in a nutshell. It's a pity that Apple have encrypted the iPhone's USB connection making it useless for anyone not on OS X or Windows. Blame Steve

---

### Post by PsychedelicWonders on 2008-11-17
> **PocketDog said:**
> Yes, in a nutshell. It's a pity that Apple have encrypted the iPhone's USB connection making it useless for anyone not on OS X or Windows. Blame Steve

What do you mean I dont understand?

iPhones connect via some weird plug not USB?

How does this come into play, I guess I'm just realy confused.

And also, as long as I have iTunes set to rip these songs onto a particular HDD, I should be able to see all of these songs when I access the HDD from Ubuntu right?

---

### Post by PocketDog on 2008-11-17
Sorry, I'm making this sound more complicated than it is. The connection from an iPhone to a computer is encrypted. On Windows or Mac that's not a problem. On Linux it's a problem. So, without jail-breaking your iPhone and invalidating its warranty it's necessary to use Windows' iTunes to transfer music to your iPhone. So, do all that using Windows. You can still access the music using Linux. If you want to access your iPhone with Linux you'll have to invalidate its warranty and I don't want to do that

---

### Post by PsychedelicWonders on 2008-11-17
gotcha.

So hold on, I just ripped a CD via iTunes, I see it in iTunes, but I cant seem to locate it on my 3rd media HDD.

I went under preferences>advanced>iTunes music folder location

And I have it set to E:/my music which is where all my my music is stored on my media HDD.

?

---

### Post by PsychedelicWonders on 2008-11-17
For some reason it saved Marylin Mansons Golden Age of Grotesque in a Compilations folder.

Any idea why it would associate it with a Compliations folder and not the Marylin Manson folder, or even creat a new one?

---

### Post by PsychedelicWonders on 2008-11-17
I just tried again and it put another cd in the compliations folder inside of my music folder isntead of making a new one, or preferably putting it in the correct folder to begin with.

---

### Post by PocketDog on 2008-11-18
Sorry it took so long, I went to bed. The compilation's easily fixed - highlight all of the album's tracks in iTunes - right click - info. Untick 'compilation', save, and the album will be moved to the artist's folder.

---

### Post by PsychedelicWonders on 2008-11-18
> **PocketDog said:**
> Sorry it took so long, I went to bed. The compilation's easily fixed - highlight all of the album's tracks in iTunes - right click - info. Untick 'compilation', save, and the album will be moved to the artist's folder.

ha son of a bitch!  i ended up doing them all pretty much through the compliation folder.

No biggie, they're all done now.

Now I had changed everything technically via 

my computer>E:>my music

not through iTunes.

But when I went to 

/media/johnnyscience/my music

(which is basically my media HDD)

None of the changes I did through windows took when I booted up Ubuntu?

All of my files are still unorganized after I spent 5 hours trying to do so last night.

Please dont tell me I will have to do the same thing in ubuntu?!

there has to be a way to have it mirror the changes I made to my HDD in windows?!

---

