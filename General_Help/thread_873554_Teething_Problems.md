---
title: "Teething Problems"
date: 2008-07-29
forum: General Help
---

### Post by johnthemong on 2008-07-29
I recently built a low energy via based PC and decided to use Xubuntu 8.04 as the sole OS. I'm pretty happy with it but there are a few things I just can't figure out coming from Ubuntu 8.04. I was wondering if someone could give me some clues. 

1st How do I create application launchers for the bar at the top. I want to make launchers for Rythmbox, Thunderbird, Abiword, Pan Newsreader and Ark. With ubuntu you just dragged them from the menu and all was well but that trick doesn't work here so I'm a bit stumped. 

2nd I cant figure out how to adjust the system volumes which means I currently have to turn my TV (which is used as the display) all the way up to hear anything. This is really annoying my wife. When I go to the settings manager all I get is a bunch of tick boxes with no bits to drag up and down. 

3rd I have never been sure about the best pluggins to play media in Firefox (eg youtube and so on). Can someone recommend the best way to make this thing web2.0 compatible. 

4th And this is just a little non critical one. Is there anyway to make certain apps like pidgin, skype and rythmbox start when the computer is turned on?
Many thanks. 

John

---

### Post by aomlives on 2008-07-30
Seeing as I'm using the same version of Xubuntu I think I can answer the most of your questions:

I might not know the exact terms because my Xubuntu is mostly in Dutch but I'll try anyway:

1) Rightclick anywhere on the panel -> Add new item -> Add Launcher (first option) -> then in the "command" box type the terminal command for the program e.g. "thunderbird". 

2) I see what you mean. I think the easiest way is to add the "Sound item" (or something like that :)) to your panel. Simply do as above to add a new item, but instead of a new launcher, choose the sound related item that's already on the list (I don't know the exact English name). Then a microphone icon will apear on your panel, which you can click to open up an extensive sound mixer applet. I think this is actually the gui form of the "alsamixer", which is another way to quick access your volume control. To do this, open up a terminal and type ```
alsamixer
``` and the exact same thing will apear in terminal view.

3) I'm not sure what you mean here, I'm not a Web 2.0 specialist, but what exactly do you want? YouTube and that sort of stuff seem to work great on my machine, so what other plugins do you want or are not working?

4) Go to Applications -> Settings -> Settings Manager -> Autostarted apps and then add new applications to the list by e.g. by typing "pidgin" in the command box (through Add button). These apps will autostart next session!

I hope this answers the most of your questions, please ask if something's not clear or incomplete :D

---

### Post by johnthemong on 2008-08-06
Thanks, that was really helpful. I now have control over sound and have things launching at start up. Many thanks.

---

