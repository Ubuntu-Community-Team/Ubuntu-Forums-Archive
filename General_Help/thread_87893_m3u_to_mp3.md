---
title: "m3u to mp3"
date: 2005-11-09
forum: General Help
---

### Post by christian on 2005-11-09
Hi, I downloaded some songs from Limewire and they've been saved as file type- m3u.

I have had no problem using xmms to play them, but now I'd like to burn them as audio to CD. Graveman does not recognise the m3u format- how can I change it to mp3? (I tried Serpentine and Gnomebaker but there were more difficult issues to solve before this so I'm sticking to Graveman)

thanks!

---

### Post by Manny C on 2005-11-09
m3u is a playlist file format. It just contains file metadata. For [example]("http://hanna.pyxidis.org/tech/m3u.html"):
```

#EXTM3U
#EXTINF:111,3rd Bass - Al z A-B-Cee z
mp3/3rd Bass/3rd bass - Al z A-B-Cee z.mp3
#EXTINF:462,Apoptygma Berzerk - Kathy&#180;s song (VNV Nation rmx)
mp3/Apoptygma Berzerk/Apoptygma Berzerk - Kathy's Song (Victoria Mix by VNV Nation).mp3
#EXTINF:394,Apoptygma Berzerk - Kathy's Song
mp3/Apoptygma Berzerk/Apoptygma Berzerk - Kathy's Song.mp3
#EXTINF:307,Apoptygma Bezerk - Starsign
mp3/Apoptygma Berzerk/Apoptygma Berzerk - Starsign.mp3
#EXTINF:282,Various_Artists - Butthole Surfers: They Came In
mp3/Butthole_Surfers-They_Came_In.mp3
```

---

### Post by christian on 2005-11-09
so how do I get Graveman to recognise the m3u file? and be able to burn it as audio?

thanks for quick reply!

---

### Post by Pablo_Escobar on 2005-11-09
m3u is not an mp3 file :(
m3u is just a playlist, You've probably downloaded the wrong files.

---

### Post by Who on 2005-11-09
The M3U is like an MP3 shopping list...it just says where a bunch of songs are kept....
Depending on how many files there are in the playlist, you could open it with a text editor, say gedit, and then just look at the text in it in order to establish which files are in it. Then you can add these to the CD (by finding the MP3s on your disk.

Now, I looked for it a while ago in K3B (A linux CD burner) and couldn't find any way to directly import an M3U (I.E it using the file to add the mp3s)...but that still doesn't mean it isn't there now. If it isn't, there are some workaround solutions....

Here is a suggestion that may work:
Open Rthymbox (An itunes-esque jukebox) or similar application (I'm thining of amarok specifically, but that won'e be installed if you have Gnome only) and then open the M3U file. If the songs referenced in it are on your disk, it should add them to the playlist. You should then be able to drag and drop this playlist onto a burning app (making sure you have selected 'Audio CD') Rthymbox MAY have a menu option somewhere to burn the playslist to CD...

I know that this process works with Amarok and K3b, but  haven't tried it with only Gnome apps.

HTH

Who

---

### Post by christian on 2005-11-09
ahah! I found the original files!

 thanks-o!

---

