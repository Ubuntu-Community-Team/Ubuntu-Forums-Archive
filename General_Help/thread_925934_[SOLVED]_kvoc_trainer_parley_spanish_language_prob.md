---
title: "[SOLVED] kvoc trainer parley spanish language problems"
date: 2008-09-21
forum: General Help
---

### Post by be4truth on 2008-09-21
I am wondering if somebody uses Kvoc Train or Parley to learn Spanish. I have a problem to emphasise letters like the ó in "dónde" . Can somebody help me with the configuration?

:)Thx

---

### Post by Icebear on 2008-09-21
Hi

I use Kvoc trainer to learn Russian. What I have done is modified my Russian keyboard and added a &#769;  which can work on any letter like o&#769;.

What I did was back up a copy of ru in /usr/share/X11/xkb/symbols

then I sudo gedit ru

and and added to a key , U0301 (which is the utf8 code for &#769; )

so it looked like this
	<LatM> {   [     Cyrillic_em,     Cyrillic_EM,	U0301	]	};

also at the top of that section I changed the key.type[group1]="TWO_LEVEL_ALPHABETIC";   
to
key.type[group1]="FOUR_LEVEL_ALPHABETIC";

you should be able to do the same with a spanish keyboard.

You also need to got System>Prefernces>Keyboard

goto the layout tab and hit the **layout options** button and then click 
**third lever chooser** and then pick what option you want and hopefully when you hold the third lever button and the key you choose you will get &#769;

---

### Post by be4truth on 2008-09-21
Thx for the reply.
I have a &#769;  and a ó in writer for example. The keyboard switches most of the time from English to Spanish, the Third level chooser and the compose key both work most of the times although I find the whole set-up a bit buggy. In writer all is fine. In Kvoc Train all the other Spanish special letters work so far but no luck with ó.

---

### Post by Icebear on 2008-09-24
So the keyboard does not keep changing goto 
System>Preferences>keyboard> 

then hit the layout tap and unmark separate layout for each window

and maybe you could change the code to U00F3 and get ó as a whole unit.

Sorry I not sure what else you can do.:(

---

### Post by be4truth on 2008-09-28
I found the solution to the problem. The layout of the Spanish keyboard has at least 3 different "'". I was using the wrong one. The one that is next to the enter key gives the "'" on a,e,u,o,i in all applications.
Thx for all your time

---

