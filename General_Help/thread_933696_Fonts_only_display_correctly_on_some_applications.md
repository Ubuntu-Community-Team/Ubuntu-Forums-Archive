---
title: "Fonts only display correctly on some applications"
date: 2008-09-29
forum: General Help
---

### Post by kung fu buntu on 2008-09-29
I have downloaded a file from amule, whose filename is in chinese. The problem is that:
- the filename looks 100% OK in amule
- the filename only looks 90% OK (this means there are 4 characters that display incorrectly) in konqueror, konsole, opera, etc

- in fontmatrix the filename (copy-pasted from amule) shows correctly in the Playground text box, but not in the "render panel". With tkfont, the text always displays fine for every font I had selected.

- weirdness in opera: the filename display bad here (in ubuntu text box where I'm writing this), but displays fine in [http://babelfish.yahoo.com/](http://babelfish.yahoo.com/) in the "translate block of text" but not in the same webpage "search" text box.

- weirdness in kde: I have set in kcontrol all my fonts to "sans serif 10", but in amarok the song title will display ok in the playlist, but not in amarok's window title bar (the bar with the mini/max-mize and close buttons)

Some of the troublesome characters: &#19987;&#36753; (I copy-pasted them since I can't see them here)


How can I fix this? Which fonts should I select for my system?
I write/read in english, japanese and I also deal with chinese as well. (for what is worth, I use UIM to write in japanese)

Another thing is, how will fonts behave when I record files into a cd or dvd?

Thank you.

---

### Post by seshomaru samma on 2008-09-30
I think the problem is that Ubuntu displays Chinese using Japanese characters (i.e Kanji) when you are running a Chinese locale alongside a Japanese locale .&#19987;&#36753;  doesn't exist in Japanese (it does but written in a slightly different way) so Ubuntu can't find it. The first thing I would do is try to install more fonts. Just go ```
sudo apt-cache search chinese
``` and install all the fonts 
 There is a way to solve it (detailed [here]("http://ubuntuforums.org/showthread.php?t=582424")) but it will set the font locale to zh_CN (Chinese) if you are interested mainly in Japanese it might not be the proper way.

Mind you , I'm running Gnome Gutsy and rarely have a problem displaying Chinese or Japanese, my system is optimized for Chinese but I installed all the possible fonts from both the Hong Kong and the Japanese repositories

---

### Post by kung fu buntu on 2008-09-30
I'm using en_US.UTF-8 as my locale, only. No additional jp or zh.

I'm on Debian, so there is no fontconfig-voodoo command.
However, my fontconfig package (which includes fc-* commands) seems to have created a .fonts.conf file.
Maybe if I tweak this file properly my font problems will be solved.

Regarding installed fonts, the ideal for me would be to have as few as possible.
I have so many fonts installed on my system already... I wouldn't be surprised to have lots of redundant fonts or low-quality fonts which are being used as default.

---

### Post by seshomaru samma on 2008-10-01
debian? in that case i don't know, i thought it was a specific ubuntu bug that it uses kanji to display chinese. i never had problems with japanese/chinese on etch ,but again i was running gnome.
i would guess it has to do with either the font.conf file or the font setting on a particular application. for example if a japanese font is the default on an application it might not display chinese properly

---

### Post by kung fu buntu on 2008-10-01
Could you post your .font.conf?

BTW, how relevant is .font.conf? I mean do all the applications (console, X11, kde, gnome, etc) take into account this file?

---

### Post by seshomaru samma on 2008-10-01
I don't know the answer to your question ,I'm running Gutsy as my main machine now and I tweaked it so much I can't even remember what I did , when I was running etch it was also heavily tweaked , I think both didn't display  CJK well when I first installed them 
Here is my font.conf -hope it helps (had to compress it cause ubuntu forums wouldn't upload a text file for some reason), remember that my locale is set for chinese

---

### Post by kung fu buntu on 2008-10-05
This is weird...
I don't remember exactly but I think I installed or upgrade a set of fonts... and on my next reboot the filenames were fine :o

The info on the .font.conf is very interesting.
When I have the time I will try to tune it and choose the best possible set of fonts.

Thank you for your inputs.

---

### Post by seshomaru samma on 2008-10-06
ha ha . this is exactly what happened to me...

---

