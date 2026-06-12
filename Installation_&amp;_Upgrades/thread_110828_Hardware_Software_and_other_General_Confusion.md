---
title: "Hardware Software and other General Confusion"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by jackdirt on 2005-12-31
So I have done some general searching on the forums and found alot of very useful answers. This forum is an invaluable resource. With that being said I am going to lay out my laundry list of what I am trying to do and see if anyone can help. Let me start with my major but simple questions.  

I know how to CHMOD but when I wanted to add a folder to Filesystem I was denied along with when I later tried to add icons to  /usr/share/pixmaps/  but was denied. I am sure there is a way to do it but I don't know how. 

Next Dilemma I have an NVidia 6800 GT and want to desperately run dual monitors. Last time i tried to follow some instructions it reset the system resolution to something to high for my monitors to read and I had to reformat. Why reformat I don't knwo a thing about terminal. While I was very advanced in windows I am a nube in linux land.

[LIST]
[*]Is there a way I can install my pc fonts? I really need them.
[*]What about windows media player ? I also had a ton of video codecs installed from the kazaa Codec pack. Is there an equivalent?
[*] How do I install Macromedia flash player in firefox?
[*] How do I install Quicktime on linux?
[*] How do I install my wacom tablet drivers?
[*]Also want Java and azureus...
[/LIST]


I am a graphic and web designer. I used to do all my work on pc using the standard adobe and macromedia suites. So running those is of great importance to me actually just adobe suite and Flash MX 2004 I figure there is a good open source alternative for Dreamweaver.  

I tried using crossover office and I successfully installed illutrator CS but i could never figure out how to run it. 

I have alot of stuff I need to do to this system and so I am a little overwhelmed by everything I took for granted. Like the windows .host file little registry hacks to make the system run smoother. I really know nothing about linux and everything I learned I found out here. 

I do have to say I am completely amazed with all teh features ubuntu has like how customizeable the aesthetics are and even simple things like the default cursor set. I really want this to be my kiss of death to windows even if it means alot of work to get everything I want working.

So thank you to everyone in advance. :KS

---

### Post by jackdirt on 2005-12-31
I also forgot now I only have a maximum resolution of 1024 x768 and I can't figure out how to add more sizes.

Thanks Again

---

### Post by Sef on 2005-12-31
Video Card - I don't believe it is possible to add sizes to your video card

Flash, Java, and Azureus :  System ----> Administration ---------> Synaptic Package Manager.  Then just click on Search and type in what you want, click on it twice, the apply button highlights, and click on it.  There are also some codecs too.

Do a search in these pages for downloading codecs, and the requests that you have  listed.

Note: To get some packages, in Synaptic Package Manager go to (on the menu bar) Settings ------> Respositories --------> Add and check Community Mainatained (Universe) and Non-Free (Multiverse.)   That is so Flash and Java can be installed.

---

### Post by jackdirt on 2006-01-01
thank you that helped greatly.

After I used synaptic I got this message 

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

so i opened up terminal and did that and I got
dpkg: requested operation requires superuser privilege


now I don't know what to do. 

Seriously though learning how to enable multiverse and universe was great!

---

### Post by jackdirt on 2006-01-01
wow that was brilliantly simple to fix the previous error...

I am really liking this OS

---

### Post by Jeff12088 on 2006-01-01
Don't know if you're being sarcastic or not and sorry to be so basic, but all you have to do it add sudo.

I advise you checking out this 3rd-party package:
[http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23](http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23)

---

### Post by jackdirt on 2006-01-01
No sarcasm I am actually being quite serious. 

Thanks I will check out that application

---

### Post by kaamos on 2006-01-01
Hello! You can find most answers in here [http://www.makuchaku.info/amnesty/](http://www.makuchaku.info/amnesty/)

[quote=jackdirt]    * Is there a way I can install my pc fonts? I really need them.[/quote]
```
sudo apt-get install msttcorefonts
sudo fc-cache -f -v
```
[quote=jackdirt]    * What about windows media player ? I also had a ton of video codecs installed from the kazaa Codec pack. Is there an equivalent?[/quote]
[http://www.makuchaku.info/amnesty/#codecs](http://www.makuchaku.info/amnesty/#codecs)
[quote=jackdirt]    * How do I install Macromedia flash player in firefox?[/quote]
```
sudo apt-get install flashplayer-mozilla
```
[quote=jackdirt]    * Also want Java and azureus...[/quote]
[http://www.makuchaku.info/amnesty/#jre](http://www.makuchaku.info/amnesty/#jre)
[http://www.makuchaku.info/amnesty/#azureus](http://www.makuchaku.info/amnesty/#azureus)

---

