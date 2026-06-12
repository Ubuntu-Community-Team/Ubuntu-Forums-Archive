---
title: "XMMS Question"
date: 2006-01-18
forum: Installation &amp; Upgrades
---

### Post by nee coa la on 2006-01-18
Okay does xmms only play mp3 files? or is there a way to get it to play more than that? I have a crap load of m4a files and it can't play any of them. And if it cannot play them..does anyone know of a audio file converter so i could convert the m4a's to mp3?

---

### Post by heimo on 2006-01-19
[quote=nee coa la]Okay does xmms only play mp3 files? or is there a way to get it to play more than that? I have a crap load of m4a files and it can't play any of them. And if it cannot play them..does anyone know of a audio file converter so i could convert the m4a's to mp3?[/quote]

Is m4a same as aac? :???:
[xmms-mp4]("http://packages.ubuntu.com/breezy/sound/xmms-mp4") is in [multiverse]("https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu")


This link is Debian specific, but instructs how to install "marillat repository" codecs.
[http://wiki.debian.org/MultimediaCodecs](http://wiki.debian.org/MultimediaCodecs)

---

### Post by nee coa la on 2006-01-19
jez i really don't know.

---

### Post by nee coa la on 2006-01-19
*bump*

---

### Post by kaamos on 2006-01-19
Well you got the answer alrealdy from heimo.
> xmms-mp4 - a mp4/aac audio player for xmms
So open up synaptic and install the package, or to do the same in terminal:
```
sudo apt-get install xmms-mp4
```

---

### Post by reet on 2006-01-19
Maybe he should take some advice from his own signature :p

Maybe change the error in it as well since if you actually read it "...and stupid have..." doesn't actually make any sense, and the grammar is just horrible.

---

### Post by shade11 on 2006-01-19
XMMS comes with not only mp3 support but also ogg support. I dont know about the other formats. Because I installed decoders from Automatix before I had a chance to see the plugins. But If you install Automatix it can install decoders for other audio formats for you. As for m4a/mp4/aac files? The mp4/m4a/aac files are all the same thing, owned by apple, it is a high-quality compressed sound format. I had the biggest problem with those trying to get 1 media player to run 'em all but to get m4a/mp4/aac support open up your terminal and type in:

```
sudo apt-get install xmms-mp4
```
You may need to set Universe and Multiverse.

---

### Post by nee coa la on 2006-01-19
Well I searched for it in synaptic...couldn't find it. Is there a repository i need to add to find it?

and reet, thanks for the help...i can see it is people like you who give these forums a great name! keep it up! :-D

---

### Post by shade11 on 2006-01-20
Enable universe/multiverse.

---

### Post by kaamos on 2006-01-20
Here you go: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by nee coa la on 2006-01-20
how do enable multi and universe?

---

