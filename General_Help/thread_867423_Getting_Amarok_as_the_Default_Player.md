---
title: "Getting Amarok as the Default Player"
date: 2008-07-22
forum: General Help
---

### Post by Unanimated on 2008-07-22
Not too long ago, I installed Amarok, and I noticed that when I put in an Audio CD, it comes up at the top saying "Rip With Rythmbox..." I went into preferred applications, and I saw Rhythmbox as the default player. I was just wondering what command I have to put in the box below it to make Amarok the default player.

---

### Post by iaculallad on 2008-07-22
> **Unanimated said:**
> Not too long ago, I installed Amarok, and I noticed that when I put in an Audio CD, it comes up at the top saying "Rip With Rythmbox..." I went into preferred applications, and I saw Rhythmbox as the default player. I was just wondering what command I have to put in the box below it to make Amarok the default player.

That would simply be:

> amarok

---

### Post by mc4man on 2008-07-23
Assuming your using gutsy(7.10) what you want as a command is
```
amarok -cdplay %d
``` This will allow amarok to start up, load the cd and start playing. (the first time per session may take 15-20 secs, i usually just start up amarok right after booting up and leave it sleeping in panel till used)

If you have two drives, while Amarok works off of a default device setting, making it the default (autoplay) choice will allow that setting to be dynamically changed to the device the audio cd is inserted in and amarok will stay with that setting till an audio cd is inserted in the other drive, ect. etc.

if you have hardy you can basically forget about it.
If you have kubuntu 8.04 you can autoplay from one drive only (last time i ck.'ed)







0

---

### Post by bryncoles on 2008-07-23
if you're running hardy, you can right click the audio cd (i assume.... because this works with other media files) and select open with application, then choose amarok from the list and that'll set it as default. if that doesnt work, open a folder (doesnt matter what for) and click edit, preferences, media and sort it out there!

hope that works...

---

### Post by Unanimated on 2008-07-24
Thanks everyone. Is there a plugin available that lets Amarok rip CDs as well?

---

### Post by mc4man on 2008-07-25
> if you have hardy you can basically forget about it. Actually I have a way now to have amarok autoplay cd's  upon insertion (one cd/dvd drive only.) While it's easy to add amarok to the default choice drop down it won't work right, if at all. 

The main issue in hardy in terms of autoplay is the app is given /home/<user name>/.gvfs as the location to access the cd. Amarok uses that location as the default device which is a disaster to say the least.

I haven't found a way to either change the command or create the script to work with 2 drives so the drive is specified and set to the /dev/cdrom link of the drive to be used. ( ie. /dev/cdrom or /dev/cdrom1 in most cases)
I don't know much about scripts so maybe it could be modified for 2 drives. 

Edit: thanks to Ziri who wrote a script you can auto play from 2 drive, the script below reflects the changes. Note that this assumes scdx for your drives. (pretty everyone will be using that now.
 All you need to do is copy below into an empty text file, *drop it into home folder* and give it a name ( for here we'll name it play1

```
#!/bin/bash
CD=/dev/`echo $1|sed -e "s/.*\(scd[0-9]\).*/\\1/"`
amarok --cdplay //$CD 
```

For a one drive system

```
#!/bin/bash
amarok --cdplay /dev/[COLOR="Red"]cdrom
[/COLOR]
```

Adjust red if different (cdrom1

Then then in a terminal run
```
chmod +x play1
```

Now browse to home dir. -> .local -> share and see if there is a folder named applications and if so, is there a file - mimeapps.list inside. If so good, **if not** you can create the **folder **if needed


```
mkdir ~/.local/share/applications
```

then run

```
cp /usr/share/applications/kde/amarok.desktop ~/.local/share/applications/amarok-cd.desktop
```
Then run

```
gedit ~/.local/share/applications/mimeapps.list

```
If **it's empty **then paste this in


```
[Added Associations]
x-content/audio-cdda=rhythmbox.desktop;amarok-cd.desktop;

```

If **it's no**t then paste just this line in

```
x-content/audio-cdda=rhythmbox.desktop;amarok-cd.desktop;

```

if the **line exist**s then just add to end of line
```
amarok-cd.desktop;
```

Be careful to keep formatting - no space between entries and end with a ;

then

```
gedit ~/.local/share/applications/amarok-cd.desktop
```

Find the line - Exec=amarok %U and change to ```
Exec=./play1
```


Find the  line - Name=Amarok and change to Name=Amarok cd player (**must do**

Save and exit out

Now go to preferences ->file management -> media -> CD Audio  and Amarok cd player should be listed

Edit: you may need to reboot before the script for 2 drives works

---

