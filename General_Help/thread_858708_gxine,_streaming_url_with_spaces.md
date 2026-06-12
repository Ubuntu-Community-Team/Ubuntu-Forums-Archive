---
title: "gxine, streaming url with spaces?"
date: 2008-07-13
forum: General Help
---

### Post by 3djake on 2008-07-13
For some reason xine or gxine will not stream a url video with spaces, took me for ever to figure out why certain streams wont play. After a while i figured out the streams that will not play share 1 thing in common, the url's have spaces 
for example "mms://194.116.83.15/Hard and Heavy" from [http://www.rocktelevision.com/](http://www.rocktelevision.com/)

I have tried using hex %20 instead of spaces as well as using the command quoting the url gxine "mms://194.116.83.15/Hard and Heavy"
but nothing i try works,
Its not just that website, streams with spaces from other sites wont work either.
Any help or suggestions will be great thanks.

---

### Post by drs305 on 2008-07-13
I tried several combinations and couldn't get any to work. Finally, while experimenting, just putting this in the 'Open MRL' window started working - no quotes, \ or anything:

mms://194.116.83.15/Hard and Heavy

Edit: Well, I got about 20 seconds of play - don't know how long it was supposed to be. But it didn't work at all for the first dozen attempts with various symbols.

---

### Post by 3djake on 2008-07-13
yeah it plays the intro video thats plays when you first connect to the stream but fails to play the stream after that, works fine for my brother but he is using the devils OS (windows). Seems like something i need to report to the gxine team, i also think it has to do with the intro video's that almost every station has these days. other ones like mms://194.116.83.15/90s play the intro video then go on to play the stream just fine

---

