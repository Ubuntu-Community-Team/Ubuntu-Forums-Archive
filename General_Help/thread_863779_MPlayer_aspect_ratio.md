---
title: "MPlayer aspect ratio"
date: 2008-07-18
forum: General Help
---

### Post by Shunsuke_01 on 2008-07-18
When I try to change the aspect ratio of a video in MPlayer I am given four options. They are: Original, 4:3, 16:9 & 2.35:1.

Is there anyway I can force a video to play in 16:10? VLC has this option but I'm wondering whether this is possible with MPayer. I have a widescreen monitor, and I would like to play a video that is stretched to fill the whole screen.

---

### Post by y-lee on 2008-07-18
maybe starting mplayer 

```
mplayer -monitoraspect 16:10 pathtofilename
```

---

### Post by Shunsuke_01 on 2008-07-18
> **y-lee said:**
> maybe starting mplayer 

```
mplayer -monitoraspect 16:10 pathtofilename
```

Thanks for the reply. 

If I had a video on my desktop named "video.mp4", how would I go about playing it using this method?

I tried mplayer -monitoraspect 16:10 /home/chris/desktop/video.mp4

Is this correct? It opens MPlayer, but the video is stuck on the default resolution and it doesn't even play.

---

### Post by y-lee on 2008-07-18
> **Shunsuke_01 said:**
> 

I tried mplayer -monitoraspect 16:10 /home/chris/desktop/video.mp4

Is this correct? It opens MPlayer, but the video is stuck on the default resolution and it doesn't even play.

That should work I am not sure why it is not working for you. I didn't even know about that option but found it in mplayers man page.

maybe try 

```
mplayer -monitoraspect 1.6 /home/chris/desktop/video.mp4
```

That also works for me. If these don't work for you then I don't know. sorry.

---

### Post by Shunsuke_01 on 2008-07-18
Nope, still not working. :(

Doesn't matter, I can still watch videos in their default resolutions which is fine anyway. :)

---

### Post by Bachstelze on 2008-07-18
> **Shunsuke_01 said:**
> If I had a video on my desktop named "video.mp4", how would I go about playing it using this method?

Add a line like this to your mplayer config file (~/.mplayer/config) :

```
monitoraspect=16:10
```

Then it will use that option by default and you won't have to worry about it anymore.

---

### Post by Shunsuke_01 on 2008-07-18
> **HymnToLife said:**
> Add a line like this to your mplayer config file (~/.mplayer/config) :

```
monitoraspect=16:10
```

Then it will use that option by default and you won't have to worry about it anymore.

Thanks for the info, but it still doesn't have any affect on the video. :(

Can you explain exactly how the config file should look life in order to play a video as 16:10?

---

### Post by Bachstelze on 2008-07-18
> **Shunsuke_01 said:**
> Can you explain exactly how the config file should look life in order to play a video as 16:10?

Just like that ;) How are you playing the video ? Are you just double-clicking on it, or running mplayer from the command line ?

---

### Post by Shunsuke_01 on 2008-07-18
> **HymnToLife said:**
> Just like that ;) How are you playing the video ? Are you just double-clicking on it, or running mplayer from the command line ?

Right click > Open with MPlayer

I've got my default player set as VLC, but I don't think that would make a difference.

---

### Post by Shunsuke_01 on 2008-07-19
Wait a sec, if I add "monitoraspect=4:3" to the config file, it automatically plays said video fullscreen. This is video is native 4:3, so I'm assuming that because I'm setting my monitor's aspect ratio to 4:3, the video should take up the whole screen?

I'm confused about how this works, but somehow it does. If anyone can properly explain what is going on I'll mark this thread as solved. :)

---

### Post by IanW on 2008-07-19
The monitoraspect=x:y config tells mplayer what shape your monitor *really* is, so it can make the video files you play look _right_. If that means they don't fill the screen, then they don't fill the screen.

Without this, if you play 4:3 video on a 16:9 or 16:10 screen, everyone gains about 20Kg, or if you play 16:9 or higher video on a 4:3 screen, everyone looks 3m tall. 

For a better explanation of aspect ratios try this [Wikipedia](http://en.wikipedia.org/wiki/Aspect_ratio_(image)) page.

---

### Post by Sutur on 2009-11-12
> **IanW said:**
> The monitoraspect=x:y config tells mplayer what shape your monitor *really* is, so it can make the video files you play look _right_. If that means they don't fill the screen, then they don't fill the screen.

Without this, if you play 4:3 video on a 16:9 or 16:10 screen, everyone gains about 20Kg, or if you play 16:9 or higher video on a 4:3 screen, everyone looks 3m tall. 

For a better explanation of aspect ratios try this [Wikipedia](http://en.wikipedia.org/wiki/Aspect_ratio_(image)) page.

I know exactly what you're talking about, but consider this:
If I pay $2000 for a big screen 16:9 TV, and I watch a 4:3 video (no distortion) then that's roughly 1/3 of the screen not being used, and therefore roughly $700 down the drain!

I'd rather have distortion, so is there a way to force 16:9 in an mplayer config file regardless of the video's encoded aspect ratio?

---

### Post by Sutur on 2009-11-16
Found a way to **force** aspect ratio in MPlayer (this will distort some videos):

Add the following to

```
~/.mplayer/config
```

```
aspect=16.9
```

"monitoraspect=16:9" doesn't work.

---

### Post by SuperSonic4 on 2009-11-16
There is the Smplayer frontend that has 16:10 as an option

---

### Post by Vaphell on 2009-11-16
seriously there are people willing to watch distorted image just because they paid 2k for their shiny display? o.O
4:3 scaled to 16:9 = everything is multiplied horizontally by 1.33 which is huge distortion in my book, next to unwatchable. 16:10 will be slightly less stretched but nowhere near the usability zone.

What's funnier - somehow nobody has any problems with watching 16:9 videos on 4:3 displays (empty stripes on top and bottom)

---

### Post by SuperSonic4 on 2009-11-16
> **Vaphell said:**
> seriously there are people willing to watch distorted image just because they paid 2k for their shiny display? o.O
4:3 scaled to 16:9 = everything is multiplied horizontally by 1.33 which is huge distortion in my book, next to unwatchable. 16:10 will be slightly less stretched but nowhere near the usability zone.

What's funnier - somehow nobody has any problems with watching 16:9 videos on 4:3 displays (empty stripes on top and bottom)

What about 16:9 scaled to 16:10?

---

### Post by linuxyogi on 2011-01-11
> **Sutur said:**
> Found a way to **force** aspect ratio in MPlayer (this will distort some videos):

Add the following to

```
~/.mplayer/config
```

```
aspect=16.9
```

"monitoraspect=16:9" doesn't work.

I tried your solution. Gnome Mplayer is responding to this tweak but not Smplayer. 

Smplayer still selects the default AR for every single file in the playlist. Suppose, if there are 10 files in Smplayer's playlist I have to reselect the AR all 10 times.

---

### Post by firekage on 2012-05-13
> **linuxyogi said:**
> I tried your solution. Gnome Mplayer is responding to this tweak but not Smplayer. 

Smplayer still selects the default AR for every single file in the playlist. Suppose, if there are 10 files in Smplayer's playlist I have to reselect the AR all 10 times.

I had similar problem but in my case it works.

---

