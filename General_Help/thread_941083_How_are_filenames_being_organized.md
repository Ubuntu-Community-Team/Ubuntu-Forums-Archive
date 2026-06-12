---
title: "How are filenames being organized?"
date: 2008-10-07
forum: General Help
---

### Post by ATSC on 2008-10-07
I have a truckload of mp3's that I want to archive on cd/dvd and play them with my dvd-player. I have to create discs without folders as the player is just connected to my stereo and doesn't show the folders on the tiny display. Beside other problems, the player mixed up the order (begins with the last song) of the songs of many (not all) albums. When I put the disc into the computer, the order is being displayed correctly, the media players play them as I want them to have (and as I burned them), too.
I then installed a programm for catalogueing collections, imported the filenames from the disc, exported them as a csv-file and imported them in open office. OO showed the songs the way the dvd-player plays them.

Here an excerpt:
```

Ac-Dc - Back In Black - 01 -Hells Bells.mp3
Ac-Dc - Back In Black - 02 -Shoot To Thrill.mp3
Ac-Dc - Back In Black - 03 -What Do You Do For Money Honey.mp3
Ac-Dc - Back In Black - 04 -Given The Dog A Bone.mp3
Ac-Dc - Back In Black - 05 -Let Me Put My Love Into You.mp3
Ac-Dc - Back In Black - 06 -Back In Black.mp3
Ac-Dc - Back In Black - 07 -You Shook Me All Night Long.mp3
Ac-Dc - Back In Black - 08 -Have A Drink On Me.mp3
Ac-Dc - Back In Black - 09 -Shake A Leg.mp3
Ac-Dc - Back In Black - 10 -Rock And Roll Ain't Noise Pollution.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  09 -Squealer.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  08 -Ride On.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  07 -Ain't No Fun.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  06 -There's Gonna Be Some Rockin'.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  05 -Problem Child.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  04 -Rocker.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  03 -Big Balls.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  02 -Love At First Feel.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  01 -Dirty Deeds Done Dirt Cheap.mp3 
```

Note that the files of the second album are ordered in the undesired order.

and that's how the filenames looked when I extracted them via the console (with the "ls"-command):

```
Ac-Dc - Back In Black - 01 -Hells Bells.mp3
Ac-Dc - Back In Black - 02 -Shoot To Thrill.mp3
Ac-Dc - Back In Black - 03 -What Do You Do For Money Honey.mp3
Ac-Dc - Back In Black - 04 -Given The Dog A Bone.mp3
Ac-Dc - Back In Black - 05 -Let Me Put My Love Into You.mp3
Ac-Dc - Back In Black - 06 -Back In Black.mp3
Ac-Dc - Back In Black - 07 -You Shook Me All Night Long.mp3
Ac-Dc - Back In Black - 08 -Have A Drink On Me.mp3
Ac-Dc - Back In Black - 09 -Shake A Leg.mp3
Ac-Dc - Back In Black - 10 -Rock And Roll Ain't Noise Pollution.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  01 -Dirty Deeds Done Dirt Cheap.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  02 -Love At First Feel.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  03 -Big Balls.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  04 -Rocker.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  05 -Problem Child.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  06 -There's Gonna Be Some Rockin'.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  07 -Ain't No Fun.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  08 -Ride On.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap -  09 -Squealer.mp3
```

I then made a 

```
ls -U
```


which shows them as the player plays them (and as I don't want to have them), here another example:

.
.
.
```
The Jimi Hendrix Experience - Axis; Bold As Love - 13 - Bold As Love.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 12 - Little Miss Lover.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 11 - One Rainy Wish.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 10 - She's So Fine.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 09 - Castles Made Of Sand.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 08 - You Got Me Floatin'.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 07 - If 6 Was 9.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 06 - Little Wing.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 05 - Ain't No Telling.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 04 - Wait Until Tomorrow.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 03 - Spanish Castle Magic.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 02 - Up From The Skies.mp3
The Jimi Hendrix Experience - Axis; Bold As Love - 01 - EXP.mp3
The Jimi Hendrix Experience - Are You Experienced - 17 Red House.mp3
The Jimi Hendrix Experience - Are You Experienced - 16 Remember.mp3
The Jimi Hendrix Experience - Are You Experienced - 15 Can You See Me.mp3
The Jimi Hendrix Experience - Are You Experienced - 14 Highway Child.mp3
The Jimi Hendrix Experience - Are You Experienced - 13 51st Aniversary.mp3
The Jimi Hendrix Experience - Are You Experienced - 12 Stone Free.mp3
The Jimi Hendrix Experience - Are You Experienced - 11 Are You Experienced.mp3
The Jimi Hendrix Experience - Are You Experienced - 10 Foxy Lady.mp3
The Jimi Hendrix Experience - Are You Experienced - 08 Fire.mp3
The Jimi Hendrix Experience - Are You Experienced - 07 The Wind Cries Mary.mp3
The Jimi Hendrix Experience - Are You Experienced - 06 I Don't Live To Day.mp3
The Jimi Hendrix Experience - Are You Experienced - 05 May This Be Love.mp3
The Jimi Hendrix Experience - Are You Experienced - 04 Love Or Confusion.mp3
The Jimi Hendrix Experience - Are You Experienced - 03 Hey Joe.mp3
The Jimi Hendrix Experience - Are You Experienced - 02 Manic Depression.mp3
The Jimi Hendrix Experience - Are You Experienced - 01 Purple Haze.mp3
```

All albums and artists are in the correct (alphabetical order), except Axis - Bold as Love. The songs however are almost always not. :?

I've copied the two ac/dc albums back onto the computer and tried to add numbers/letters as a prefix but they appear to be completely mixed up then (with "ls-U"). (on a sidenote: when I do the "ls -U" on the DVD, the two ac/dc albums are not being displayed at all).
I've then copied each song individually (beginning with track #1) from the disc to my pc (I thought that the order depends on the creation date of the file and that with copying them these files would get the current, new creation date), the result was a similar mess: 

```
Ac-Dc - Back In Black - 08 -Have A Drink On Me.mp3
Ac-Dc - Back In Black - 05 -Let Me Put My Love Into You.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap - 05 -Problem Child.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap - 07 -Ain't No Fun.mp3
Ac-Dc - Back In Black - 07 -You Shook Me All Night Long.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap - 04 -Rocker.mp3
Ac-Dc - Back In Black - 06 -Back In Black.mp3
Ac-Dc - Back In Black - 10 -Rock And Roll Ain't Noise Pollution.mp3
Ac-Dc - Back In Black - 04 -Given The Dog A Bone.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap - 02 -Love At First Feel.mp3
Ac-Dc - Back In Black - 09 -Shake A Leg.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap - 09 -Squealer.mp3
Ac-Dc - Back In Black - 02 -Shoot To Thrill.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap - 03 -Big Balls.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap - 06 -There's Gonna Be Some Rockin'.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap - 01 -Dirty Deeds Done Dirt Cheap.mp3
Ac-Dc - Dirty Deeds Done Dirt Cheap - 08 -Ride On.mp3
Ac-Dc - Back In Black - 03 -What Do You Do For Money Honey.mp3
Ac-Dc - Back In Black - 01 -Hells Bells.mp3
```

:?

How do I get them burned (and subsequently played on my dvd-player) in the correct order? I'd hate to have to rip all the albums again.

---

