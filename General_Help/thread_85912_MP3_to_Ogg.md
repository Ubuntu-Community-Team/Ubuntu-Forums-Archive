---
title: "MP3 to Ogg"
date: 2005-11-03
forum: General Help
---

### Post by losslesshead on 2005-11-03
I need a program that can convert MP3's to Oggs, but that can also recognize my ID3 tags.  I have tried Sound Convertor, but it couldn't get all of the ID3 tags, and seemed a bit buggy.  Do you guys know any other programs?

---

### Post by kvidell on 2005-11-03
If you're not doing lots of files at once, you can use Audacity for this purpose... but it's sort of an editing suite so it's really only good for one file at a time...

For lots of files... I'm not sure. I'm not seeing anything obvious in the repositories...

Maybe someone else has an idea?
- Kev

---

### Post by bionnaki on 2005-11-03
[this](http://www.ubuntuforums.org/showthread.php?t=82806) will work.

but I must say transcoding from lossy to lossy will result in crap audio. be warned. only lossless to lossy is worth your time.

---

### Post by kvidell on 2005-11-03
[QUOTE=bionnaki][this](http://www.ubuntuforums.org/showthread.php?t=82806) will work.

but I must say transcoding from lossy to lossy will result in crap audio. be warned. only lossless to lossy is worth your time.[/QUOTE]
This is true, unless of course you go from "high" quality lossy to "slightly lower, but still tolerably high" quality lossy, no?

Otherwise you get empty overhead with whitenoise.
- Kev

---

### Post by matthew on 2005-11-03
There is a package in the repositories called mp32ogg that says it will do the trick. I haven't tried it. Here's the package page in the ubuntu breezy packages list:

[http://packages.ubuntu.com/breezy/sound/mp32ogg](http://packages.ubuntu.com/breezy/sound/mp32ogg)

---

### Post by losslesshead on 2005-11-03
In reply to, well, everything, here is what I have to say.  I will look into the software mentioned.  I am converting from 128-256 VBR MP3 to like either 192 or something a bit higher OGG.  Will this sound like crap?  What about possibly converting to lossless?  And how much does lossless usoually take up per song?

---

### Post by kvidell on 2005-11-03
Ah... the plight of many an audio engineer.
You sadly cannot trade up, only down.
If the data is not there, you can't just magically create it.

That would be something like taking a 50 piece lego set and trying to use the instructions for a 500 piece lego set to make things. It just can't be done.
However if you have a 500 piece set, you can make things from the 50 piece set.

Does that make sense?
You can't ascend in quality, on descend.

What ends up happening is the file has a lot of overhead available for the frequency ranges that that bitrate can allow for... yet they're empty so what happens is you can get some white-noise issues in your songs...

Empty overhead in audio files is bad.
- Kev

---

### Post by losslesshead on 2005-11-03
[QUOTE=kvidell]This is true, unless of course you go from "high" quality lossy to "slightly lower, but still tolerably high" quality lossy, no?

Otherwise you get empty overhead with whitenoise.
- Kev[/QUOTE]

Well, all my mp3's actually used to be aac files.  So I have alreadu done some lossy to lossy converting and I really can't notice a difference.

---

### Post by bionnaki on 2005-11-03
[QUOTE=kvidell]This is true, unless of course you go from "high" quality lossy to "slightly lower, but still tolerably high" quality lossy, no?

Otherwise you get empty overhead with whitenoise.
- Kev[/QUOTE]


any type of transcoding from lossy to lossy will result in data loss. now, the question is whether or not your ears can tell the difference.

I generally frown upon transcoding lossy to lossy - I dont see the point in converting mp3 to ogg when the mp3 will contain more data and be more true to the original audio. But it's all up to what the original poster wants to do, but really hope he/she doesnt share those files on p2p...

---

### Post by matthew on 2005-11-03
[quote=losslesshead]Well, all my mp3's actually used to be aac files. So I have alreadu done some lossy to lossy converting and I really can't notice a difference.[/quote]
There are a lot of factors involved beyond what has been stated already. Among those are the quality of the audio equipment the files will be played through, the number of times the files have been converted, and the sensitivity of the listener's ears.

As a musician I can usually tell a difference, but most of my friends and family cannot tell when a file has been converted even two or three times. I also notice a big difference between a quality tube stereo amplifier and my computer's $50 set of 2.1 speakers. My wife doesn't.

In other words, the poster making the statements about converting from lossy to lossy is right, but your mileage may vary.

---

### Post by losslesshead on 2005-11-03
[QUOTE=bionnaki]any type of transcoding from lossy to lossy will result in data loss. now, the question is whether or not your ears can tell the difference.

I generally frown upon transcoding lossy to lossy - I dont see the point in converting mp3 to ogg when the mp3 will contain more data and be more true to the original audio. But it's all up to what the original poster wants to do, but really hope he/she doesnt share those files on p2p...[/QUOTE]

Well, I wouldn't share them over p2p.  I have boughten all my music legally, pluss I don't see the point in doing so: I am the kid who tells other kids in my grade it is illegal to download copywritten songs from limewire, etc...  But I have one more question, how much quality do you think I would lose form converting the mp3's to ogg?

---

### Post by bionnaki on 2005-11-03
aint nothing wrong with p2p :p 

the quality would be enough for my ears to notice.
plus, I like as high quality encodings as possible
(I primarily rip to flac via crip).
your mileage may vary...

isnt it ironic that your name is losslesshead?

---

### Post by losslesshead on 2005-11-04
Yeah, it is ironic a bit.  :)  Well think about it, lossless=uncompressed/no loss head=well, head!  means I think a lot ;)  Well, I am going to stick with my MP3 collection for the moment, but I am going to convert one of my backups (of my musi cocllection) to the ogg vorbis format, and see if I notice any difference at all, or maybe there wont be a difference :)  Now I am just wishing someone will come out with a software hack that allows iPods to play Ogg Vorbis files!

---

### Post by Sykil on 2005-11-04
I'd just use vorbis-tools

losslesshead: lossless does not mean uncompressed---FLAC itself is lossless but compressed.

Anyway, typical FLAC files are 20-40MB, I would guess, but it depends on the level of compression. So, an album encoded in it would be about 300-400MB or so.

---

### Post by losslesshead on 2005-11-04
Kk.  Thanks.

---

### Post by losslesshead on 2005-11-04
Ok, I have download mp32ogg.  I have also located the script.  But, still being a newbie to linux, how do I run the script?  I have double-clicked it and clicked run, but that doesnt really do anything.  Help please (and I need it ASAP!)!

---

### Post by bionnaki on 2005-11-04
move the script to /home/[username]/.gnome2/.gnome2/nautilus-scripts
right-click on the file you want to convert & open the scripts context menu.
be sure to make the script executable...

---

### Post by SickTwist on 2005-11-04
[QUOTE=losslesshead] . . . Now I am just wishing someone will come out with a software hack that allows iPods to play Ogg Vorbis files![/QUOTE]

Keep this in mind when purchasing your next digital audio player. Believe it or not, there *are* players out there besides iPod and some of them *do* support open formats ([FLAC]("http://flac.sourceforge.net/"), [Ogg Vorbis]("http://www.vorbis.com/"), etc). :D

Check out some of the current offerings of [iRiver]("http://www.iriver.com/"), [COWON]("http://www.cowon.com/"), and [Rio]("http://www.rioaudio.com/"). I own a [Rio Karma]("http://www.digitalnetworksna.com/shop/_templates/item_main_Rio.asp?model=261") (not sure if they are still on the market) that I have been very happy with.

---

### Post by losslesshead on 2005-11-04
KK, thanks for the How-TO on running the script.  And yes, I know there are other players besides iPods.  When I used windows I had an iRIver.  But remember, I am switching from Mac, and the only player for Mac that has music store capabilities was the iPod.  I also am saving up for another computer, otherwise I might consider something from Nereus.

---

### Post by bionnaki on 2005-11-04
I have an iriver h340 & it rules.

---

