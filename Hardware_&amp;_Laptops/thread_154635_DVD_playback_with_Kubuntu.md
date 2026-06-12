---
title: "DVD playback with Kubuntu"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by kdnewton on 2006-04-03
Heyall.

I've managed to install libdvdcss by following other instructions on the forums here and I thought that would be the solution to my problems.

I was under the assumption that a media player, such as Kaffeine or Xine would now be able to play my store-bought DVD movies. The DVDs are North American, I shouldn't have any region-specific problems (I think).

That's as far as I've gotten. I put the DVD in the DVD-Rom tray and Konqueror tells me there's a problem opening it (to explore it) and to 'open with' a program of my choosing.

Kaffeine complains, Xine complains as well.

Is there a next step to this?
Thanks.

---

### Post by aysiu on 2006-04-03
What's the complaint?

By the way, you may want to try Totem instead of Kaffeine. Be sure to install the *totem-xine* package as well.

---

### Post by DeeZiD on 2006-04-03
Here's a new version of kaffeine which fixes the error :)
[http://ubuntuforums.org/showthread.php?t=154452&highlight=kaffeine](http://ubuntuforums.org/showthread.php?t=154452&highlight=kaffeine)

but you need to compile it from source.
The new Xine needs to be compiled before, too ;)

---

### Post by kdnewton on 2006-04-03
I put the DVD in the DVD-drive (media:/hdb)

   Konqueror opens asking me what I'd like to do with it... and Hey, look at that. I wait long enough (long enough to check the various popup windows and type this and the movie starts playing in Kaffeine all by itself :P )

   Anyway, Konqueror opens:

Question - Konqueror
Open 'media:/hdb'?
Type DVD Video Disk.
[]Do not ask again.
Save As / Open With... / Cancel

Followed by Kaffeine opening automagically (unfortunately) and giving me three errors in the following order (via popup windows):

Three of the following:
Error - Kaffeine Player
Internal GStreamer error: negotiation problem. File a bug.
Details>> / Ok

Kaffeine then opens and sits at the default Kaffeine display.

And as I wrote above, 20 seconds later the movie decides to start playing in Kaffeine on its own. Actually, correction. It seems to have stopped playing when I clicked "OK" on the error windows.

I have installed Totem and Totem-Xine and am looking forward to getting this working properly. Thanks for the help so far. Please keep it coming.

[EDIT]
Just a little extra information here. I chose "open with..." within the Konqueror window and chose Totem. Now Totem gives me the following error:

Totem could not play 'file:///home/myhome/media:/hdb'.
The specified movie could not be found.
Ok.

---

### Post by seanmc42 on 2006-04-03
Automatix?

---

### Post by kdnewton on 2006-04-04
I don't understand your post of a single word "Automatix" but if you are referring to my use of the word "automagically" it is just a play on the word "automatically".

---

### Post by seanmc42 on 2006-04-04
Apologies. Do a search in this website for automatix it is a script which will setup everything you need.

---

### Post by kdnewton on 2006-04-05
Thanks for the suggestion for Automatix. That looks to be a great script for newbie users and people who have not yet started setting up their machine. I ran the script and selected everything except what I absolutely didn't want (Wine, Opera when I use Firefox, etc). I haven't restarted my computer yet, but after the Automatix finished installing/configuring I still can't play my store-bought DVDs.

This last time I tried right-clicking the DVD from my desktop and opening with "oKle" and I did get another error. The error through oKle is a popup that displays as follows:

---
Error - KIOExec
/media/cdrom1 is a folder, but a file was expected.
---

So still no luck there. I also get the same error for Totem that I wrote about before. I can appreciate that Ubuntu/Kubuntu takes some work to set up. I just wish there was a more obvious way to get a DVD player working.

It reads my Data DVDs fine. It will play avi files from DVD through it no problem. I can copy data off the DVD onto the hard drive without a hitch. I'm hoping in the end I can click around and navigate the DVD menu before watching the movie.

[EDIT]

Well, look at that!

I was expecting to just be able to put the DVD in the tray, select a media player to play the DVD (oKle in this case, or Totem) and have it play. When I tried that, I got error after error after error.

I tried something different. I opened the program then pointed it toward the video_ts.vob file in the media/cdrom1/video_ts/ directory and it brought up the DVD menu. One that I can interact with and browse the chapters and navigate menues. Thanks for the help :)

---

### Post by davebgimp on 2006-04-09
I had the same problems. However trying as you did, to open the video_ts.vob file still netted me an error message. After futzing quite a while with it, I gave up and after closing a few windows, noticed that the DVD was represented as an icon on my desktop. Opting to play the movie in Kaffeine by right-clicking on this icon got everything running smoothly. I'm not sure why I would get an error when trying any other way, but as long as it works somehow, I'm happy.

---

### Post by rutterhj on 2006-04-10
Hi, I am also having the same issues.I tried to run the dvd with kaffeine but it gave me this message:

There were no decoders found to handle the stream, you might need to install the corresponding plugins

What does that mean? I'm sorry but I am a very new user to Linux so where do I go?

---

