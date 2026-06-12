---
title: "audio ?"
date: 2008-09-12
forum: General Help
---

### Post by Mickey Joe on 2008-09-12
just installed xubuntu, but trying to put my favourite song(mp3) on "Decibel Audio Player", but ntohing happens, so i download "MPlayer" it says "No Audio Device found" .. what to do ?

---

### Post by BlackLLama on 2008-09-12
i think you need to install drivers

---

### Post by mali2297 on 2008-09-12
See this guide:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Open a terminal and copy/paste the following commands
```

aplay -l
lspci -v | grep -A 5 [Aa]udio

```
Post the output.

---

### Post by ichundu on 2008-09-12
ubuntu doesn't come with codec for mp3 files, so you have to manually install them (so did i). it is easy. just open an mp3 file with the media player (maybe you should open it with the default player of the OS, not sure). you should be asked then to "search for a suitable codec", you need internet connection for this.

anyway that's what i did on my ubuntu, i have never used xubuntu, but it should be done the same way.

good luck

---

