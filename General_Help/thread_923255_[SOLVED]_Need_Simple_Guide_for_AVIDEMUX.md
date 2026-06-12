---
title: "[SOLVED] Need Simple Guide for AVIDEMUX"
date: 2008-09-18
forum: General Help
---

### Post by rbjscv on 2008-09-18
Hi All,

I know AviDemux is available for us, but i can't create a video file.  It does create a file, but not one that is playable.

I've tried this same app in Windows, and on my Mac.  Never have ended up with a viewable video.  

And I've read every guide and followed every procedure exactly - most of them several times. Maybe someone could walk me through?  I really don't think there's anything left for me to read/follow online.  But maybe.

All I want to do is load an .avi, resize, use Xvid codec, Lame codec, add subs as needed and then save as an .avi.  But there is something i must be missing in this simple procedure.

I'd done the same thing 100's of times with virtualdub, and (Auto)GordianKnot but of course i gave that up with xp.

Avidemux seems like a great program i just don't understand where I'm going wrong.  The file starts coding, the progress bar progresses, but when finished there is an unviewable file.

Thanks so much.

---

### Post by mb_webguy on 2008-09-18
Have you added the [Medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu") and installed all of the niceties from there?  Avidemux uses external codecs to do all of the heavy lifting, so if you don't have them installed, Avidemux won't be worth much.

Make sure you update and upgrade after adding the Medibuntu repository.  You especially need to make sure you have the ubuntu-restricted-extras, mencoder, ffmpeg, and non-free-codecs.  All but the first should be the versions from Medibuntu.

As for a walk-through, either it will have to wait until tomorrow, or someone else will have to do it, because I unfortunately need to get some sleep...

---

### Post by jonian_g on 2008-09-18
Well, try to do a simple thing. Import an .avi file change only the audio and video codec and save it, so you can see if the application works ok.
Also you might be missing some codecs.

I use avidemux all the time and works perfectly and it is so simple that I don't think you need a guide.

---

### Post by rbjscv on 2008-09-18
Well, I was missing the non-free-codecs.  So they are now added.  Mencoder, ffmpeg, and non-free-codecs are all on box. And of course avidemux.

I know it is supposed to be simple.  So I'm going to use a 2 min. snippet and change size, and encode using xvid, lame and save as avi file. Isn't this reasonable?  Or am I still missing something?  Will report back with results shortly.

---

### Post by rbjscv on 2008-09-18
Well well well, don't i feel stupid now.  IT WORKED.

I resized 3 mins of Anna Karinina. like this:
video codec:  mpeg-4 asp (xvid4)
audio codec:  mp3 (lame)
container:    avi
resized to gross aspect ratio

saved, but forgot .avi extension.  added extension, burnt disk, played on standalone dvd player, ugly but exactly what i did.  Far easier that setting up VirtualDub.

So i'm the goober of the day.  Now on to adding subs.  It works but 1.5 hrs Video is taking close to 3 hrs coding time on machine as shown below. VirtualDub in XP same machine does about real-time.  Strange?

Thank you everybody.  One more reason why i left vista behind.

---

### Post by jonian_g on 2008-09-18
Good.

Also if you want to convert .avi etc to DVD try DeVeDe, its in the repositories, it supports entering subtitles and creating a menu.

---

