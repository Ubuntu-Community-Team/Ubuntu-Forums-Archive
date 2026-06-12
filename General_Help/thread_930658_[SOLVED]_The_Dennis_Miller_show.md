---
title: "[SOLVED] The Dennis Miller show?"
date: 2008-09-26
forum: General Help
---

### Post by ManyBeers on 2008-09-26
When I go to this site...[http://www.dennismillerradio.com/](http://www.dennismillerradio.com/) and click Listen Live Free a new window opens but nothing plays. It is an Audio only broadcast. The window is opened with Totem plugin viewer 2.22.1. Firefox browser 3.o.2 flash 10. Thanks in advance.

---

### Post by Sef on 2008-09-26
1) What version of Ubuntu do you have?

2) Do you have this problem with any other streams?

3) It does work on Intrepid Ibex, which has totem 2.24 and 0.10.24.   However, Ibex is still alpha, so not recomended for production machines.  It will be released 30 Oct. 08.

---

### Post by kokkus on 2008-09-26
Hi. Have you installed the FlashPlugin-Nonfree ?
sudo apt-get flashplugin-nonfree

or you can install all the plugins and codecs you need at once:
sudo apt-get install ubuntu-restricted-extras

You should also install the Media Player Connectivity plugin for Firefox so you can manually choose which media player you would like to listen with.
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Forexample: the default media player for firefox is mplayer, but I use VLC to play all live streaming media. Cause it's more stabile.

---

### Post by ManyBeers on 2008-09-26
> **Sef said:**
> 1) What version of Ubuntu do you have?

2) Do you have this problem with any other streams?

3) It does work on Intrepid Ibex, which has totem 2.24 and 0.10.24.   However, Ibex is still alpha, so not recomended for production machines.  It will be released 30 Oct. 08.

8.04 Totem 2.22.1 Gstreamer 0.10.18

---

### Post by ManyBeers on 2008-09-26
> **kokkus said:**
> Hi. Have you installed the FlashPlugin-Nonfree ?
sudo apt-get flashplugin-nonfree

or you can install all the plugins and codecs you need at once:
sudo apt-get install ubuntu-restricted-extras

You should also install the Media Player Connectivity plugin for Firefox so you can manually choose which media player you would like to listen with.
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Forexample: the default media player for firefox is mplayer, but I use VLC to play all live streaming media. Cause it's more stabile.

I am using Flash10rc. It seems to work better than the flash-plugun-nonfree.  I have not installed the Ubuntu -Restricted-Extras. I have installed Fash10 and Java individually.  I will check that link out.

---

### Post by kokkus on 2008-09-26
Here's the streaming url
[http://noxsol.wl.miisolutions.net/live/noxsol_ww1-east](http://noxsol.wl.miisolutions.net/live/noxsol_ww1-east)
Open it in a media player. (Suggest VLC Player)

Keep the link and u won't need the webpage.

Btw, I though the page was flash but it's not so never mind about what I said about that erlier.
Where do u live in the world? Maybe that could be the reason why you can't access the site.

---

### Post by ManyBeers on 2008-09-26
> **kokkus said:**
> Here's the streaming url
[http://noxsol.wl.miisolutions.net/live/noxsol_ww1-east](http://noxsol.wl.miisolutions.net/live/noxsol_ww1-east)
Open it in a media player. (Suggest VLC Player)

Keep the link and u won't need the webpage.

Btw, I though the page was flash but it's not so never mind about what I said about that erlier.
Where do u live in the world? Maybe that could be the reason why you can't access the site.

Salt Lake City. Why would that matter?

---

### Post by wolfen69 on 2008-09-26
it works for me, but was slow to load. i remove totem-mozilla and install mozilla-mplayer.

---

### Post by kokkus on 2008-09-26
Never mind. You live in USA so that is not the problem.
Well, you got the link now.
Enjoy the show:)

---

### Post by ManyBeers on 2008-09-26
> **wolfen69 said:**
> it works for me, but was slow to load. i remove totem-mozilla and install mozilla-mplayer.
That might be a good idea because I don't think Totem has worked  
yet.Wher do you get mplayer?

---

### Post by ManyBeers on 2008-09-26
> **kokkus said:**
> Never mind. You live in USA so that is not the problem.
Well, you got the link now.
Enjoy the show:)

It is working now. I copied the URL and opened Rhythmbox  clicked
"add new Internet  Radio Station" so it did and when I pressed the play button it popped up an eroor message that I needed to get the Gstreamer FFmpeg plugin. I did instal it but it doesn't play in
Rhythmbox! but plays in Firefox using Totem. Just like it is supposed to. Thanks

---

