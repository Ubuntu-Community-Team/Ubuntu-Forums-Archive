---
title: "samsung yepp yp-p2"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by tich on 2008-02-10
i am thinking of purchasing the Samsung Yepp YP-P2.  it is a cute little portable media player.  before i commit to it though i just want to make sure that it (should) work well with ubuntu.

here are a couple links that give the specs:

[http://en.wikipedia.org/wiki/Samsung_P2](http://en.wikipedia.org/wiki/Samsung_P2)
[http://www.samsung.com/my/products/audio/mp3player/yp_p2ab.asp](http://www.samsung.com/my/products/audio/mp3player/yp_p2ab.asp)
[http://www.engadget.com/2007/08/14/samsungs-yepp-yp-p2-touchscreen-dap-with-bluetooth/](http://www.engadget.com/2007/08/14/samsungs-yepp-yp-p2-touchscreen-dap-with-bluetooth/)

thanks in advance!!

---

### Post by Mean-Machine on 2008-02-20
I'm also planning to get the Samsung P2 :)

You might want to have a look here -> [http://www.anythingbutipod.com/forum/forumdisplay.php?f=117](http://www.anythingbutipod.com/forum/forumdisplay.php?f=117)

plenty useful info there

:guitar:

---

### Post by seismicmike on 2008-03-07
I have the Samsung Yepp YP-U3... don't know if that makes a difference, but I can tell you that I'm having some problems with it. I don't know why this happens, but I cannot write to the device through nautilus or amarok or any other GUI. I have write access, and am not told that I lack permission to the device. It simply doesn't write the the device. The progress dialogue comes up, but stays at 0% indefinitely with the 'transfer rate' saying 'Stalled' and the estimated time left indefinitely increasing. And, once I get to this point, the only way I can do anything on my computer is to physically yank the device. (I often have to reboot).

I'm hoping to get this issue resolved, and don't know if it'll be a problem for you, but it's something you should consider.

PS. If you can get past this problem though, I do recommend the player. It's a nice little player that works well - has pretty good battery life - and isn't too big. I just have to add files to it from my windows PC :bleh:

---

### Post by Bealer on 2008-03-12
Just ordered mine. Will post how things go. Been reading how to change it to UMS. Hope it works ok in Rhythmbox. Loving the Ogg support (I hope it has from what I've read).

---

### Post by marcus2004 on 2008-03-21
I have a samsung P2 and love it. I changed it to UMS so it works to just drag and drop songs. 

seismicmike I am not sure if this would help, but have you tried to chmod and chown it?

```
 sudo chmod 777 -R /path/to/P2

sudo chown yourusername:yourusername /path/toP2
```

If you want to find the path I just went to main menu/system/administration/Partition editor
and you should see your P2 and the path something like /dev/sdsomething (it will be 7.5 gb or so)
I know that there is a command to look it up as well but I forget off hand. 

Hope that helps

---

### Post by Bealer on 2008-03-30
I downgraded and upgraded mine to change it from MTP to UMS. 

I used this guide (I found it to be the best)
[http://www.anythingbutipod.com/forum/showthread.php?t=25784](http://www.anythingbutipod.com/forum/showthread.php?t=25784)

I've got it recognised in Rythmbox by adding a hidden file to its root, and can drag and drop music to it, but all the music goes in the root directory rather than in the Music folder sat inside the root directory. I'm not sure how to get rhythmbox to handle this.

Any ideas.

---

### Post by kilted_runner on 2008-04-15
im having almost the same problem. converted to UMS and got all the music in wma ogg and mp3 on it. the ogg files woludnt drag in the folder so had to create a new folder in 'music'. theres also album art problems. the only ones that show are the ones i added myself in wmp so was wondering if theres any album art tagger or any way round this in general? ive tried amarok and i dont mean to be blasphemous but i didnt find it that great at all :p. new convert from windows and (after a lot of tweaking and learning) im loving the whole Ubuntu thing :)

---

### Post by Bealer on 2008-04-22
I've also got mine encoding videos, by simply right-clicking and selecting "Send to YP-P2".

I used mencoder, and set it up as a Nautilus Action.

I've detailed it on my blog here:
[http://www.robertbeal.info/archives/18](http://www.robertbeal.info/archives/18)

---

### Post by Bealer on 2008-05-12
I've got Rhythmbox correctly copying music to my YP-P2 which is set as a UMS device. I can plug it in, open up Rhythmbox, drag music in Rhythmbox across to the device showing in the left hand pane, and it'll copy the Music to the correct folder.

On the root of my YP-P2 I created a file called:
```
.is_audio_player
```

And then put the following inside the file:

```

audio_folders=Music/

```

---

