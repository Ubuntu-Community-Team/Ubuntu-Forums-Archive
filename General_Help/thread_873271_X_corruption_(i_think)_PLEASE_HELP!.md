---
title: "X corruption (i think) PLEASE HELP!"
date: 2008-07-28
forum: General Help
---

### Post by em4g.3ht on 2008-07-28
I have a problem when I try to play a games in wine (It has happened other times too with programs that take full screen focus that's why I am not posting in wine section)

when it happens it looks like this

[http://i138.photobucket.com/albums/q251/Em4g_3hT/P1010184.jpg](http://i138.photobucket.com/albums/q251/Em4g_3hT/P1010184.jpg)

when i log out and back in the problem is gone. I have no idea what is happening, and this problem is recent too.

specs:
hd 2900xt
Hardy
running compiz (but switch to metacity for games)

this is all i can think that you will need, but if there is anything else I am happy to share



oh and on a side note, i am not sure if this is related, but when i watch any video with compiz enabled, the video flickers (I am not sure if it is supposed to do that) even when video playback is enabled in the settings manager. flash videos and other videos from the browser (firefox 3) don't have this problem.



THANK YOU ALL FOR YOUR HELP!!!!!

---

### Post by dark_harmonics on 2008-07-28
what kind of video card do you have? Could you post the results of the following commands?

glxinfo|grep vendor     (lists your graphics vendor)
glxinfo|grep direct     (indicates whether you have direct rendering)

Do you use ubuntu's drivers or proprietary drivers from the manufacturer. I actually dont have to replace compiz with metacity to get games to run smoothly on my laptop and desktop anymore. That mostly happened to me when i used ATI graphics.

---

### Post by em4g.3ht on 2008-07-28
sorry i should have been more clear. I have an Ati hd 2900xt using the 8.6 drivers from their website. And I am using direct rendering.

It's stranged, etqw works fine with compiz, and no corruption issues. I think the last time I had this error I seleted full screen on firefox for a video I was watching.

it's only videos that have flickering uner compiz

man, this is really frustraiting.

---

### Post by dark_harmonics on 2008-07-28
After some searches i found this but it doesnt seem promising to me for your gaming issue: [http://agentneuron.wordpress.com/2008/06/16/compiz-flickering-video-ati-fix-fglrx/](http://agentneuron.wordpress.com/2008/06/16/compiz-flickering-video-ati-fix-fglrx/)

I'll do some digging for you as i remember my ATI pain. I would recommend NVIDIA for your future ubuntu computers as they seem to have cleaner support (at least in my meager experience).

---

### Post by dark_harmonics on 2008-07-28
Check this out too! [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Half way down it says:

  ```
  * If you have flickering video when Compiz is enabled, using the latest driver, do: 

$ sudo gedit /etc/X11/xorg.conf

add this line to your xorg.conf:

Option "TexturedVideo" "off"

after

Driver "fglrx"

now restart your computer. 
```

You might also want to research previous drivers to see if they provide more stable support as sometimes the latest and greatest have issues.

---

### Post by em4g.3ht on 2008-07-28
that code solved the video flicker!!! thank you!!!

one problem solved. now for the graphic curruption... i don't think that it's just a wine issue, but it may be??

-ati is getting better for opensource, i have high hopes for them. I recently switched from windows only about a month of linux for me (that's y i have ati cards), i love it an never want to return. I liked Ati because they were usually a better bang for buck company... so i hope they can compete in the opensource world too... compitition is always better for everyone!

---

### Post by em4g.3ht on 2008-07-28
here are some forums containing more information, for anyone who stumbles aross this

[http://bbs.archlinux.org/viewtopic.php?id=51577](http://bbs.archlinux.org/viewtopic.php?id=51577)

[http://www.phoronix.com/forums/showthread.php?t=10940&page=5](http://www.phoronix.com/forums/showthread.php?t=10940&page=5)

it seams the only way to solve this is to revert to 8.5 drivers, or wait for an upgrade... which there is, so I will try that and get back to you.

---

### Post by dark_harmonics on 2008-07-29
You should rename the thread heading to be a little more specific to your problem (currently it is Re: X corruption (i think) PLEASE HELP!). Maybe somebody will pick this up like you said and then be solved like you were :)

---

