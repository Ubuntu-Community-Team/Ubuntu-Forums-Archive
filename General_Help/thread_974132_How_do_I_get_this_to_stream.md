---
title: "How do I get this to stream?"
date: 2008-11-07
forum: General Help
---

### Post by jras20 on 2008-11-07
This is a Windows media plug in player that loads into the browser.  It works with Windows XP I have Windows Media 11 I think on it.  I'm wanting it to stream on my Ubuntu Laptop.  Is there a code I can put in to get it to stream?  From the Terminal?
Thanks

Here is the link I have the stream turned off, but when it is on, all the player will do is stay on stop.  If I press play it will just go back to stop.

[http://djnrjenz.listen2myradio.com/](http://djnrjenz.listen2myradio.com/)

---

### Post by kostkon on 2008-11-07
> **jras20 said:**
> This is a Windows media plug in player that loads into the browser.  It works with Windows XP I have Windows Media 11 I think on it.  I'm wanting it to stream on my Ubuntu Laptop.  Is there a code I can put in to get it to stream?  From the Terminal?
Thanks

Here is the link I have the stream turned off, but when it is on, all the player will do is stay on stop.  If I press play it will just go back to stop.

[http://djnrjenz.listen2myradio.com/](http://djnrjenz.listen2myradio.com/)
First of all, you could install the *ubuntu-restricted-extras* package to make sure that you have all the *GStreamer* plugins.

Then, you could install the Windows codecs package, called *w32codecs*, that is offered by the [*Medibuntu* repository]("http://medibuntu.org/").

You'll have to add this repository to your software sources list. Instructions on how to do it are [here]("http://help.ubuntu.com/community/Medibuntu"). After adding it, go to *Synaptic*, search for the *w32codecs* package and install it.

You'll also have to install the *totem* firefox plugin. In *Synaptic* search for the *totem-mozilla* package and install it.

Also make sure that the *gstreamer0.10-pitfdll* package is installed.

Hope that helps.

---

### Post by jras20 on 2008-11-07
I tried that, turned on the stream and it still did the same thing.  I can play windows media with the Movie player.  I just cant stream with it over firefox.

---

### Post by Romanos on 2009-01-07
when you open the site. Press (control + u) to see the source code of the page. Thes pres (contro + f) to find the word "value='http".
You will see something like this 
> <param name='url' value='http://xx.xxx.xxx.xxx:62576' />

Copy the part [http://xx.xxx.xxx.xxx:62576](http://xx.xxx.xxx.xxx:62576) and add /listen.pls

Now just open a new tab and enter [http://XX.XXX.XXX.XXX:62576/listen.pls](http://XX.XXX.XXX.XXX:62576/listen.pls)

You will download one pls file that you can open with vlc, totem, etc... 
To listen your friends radio.

A little tip for listen2myradio.com. So you don't need to listen from firefox.

Hope I help with my way! :P

romanos

---

### Post by Yashiro on 2009-01-07
Install Audacious and use it to open the stream/pls links from the browser popups.

---

