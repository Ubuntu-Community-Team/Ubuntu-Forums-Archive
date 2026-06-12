---
title: "Simple clipboard text-to-speech"
date: 2008-10-03
forum: General Help
---

### Post by yang on 2008-10-03
Is there a program that can read what's on the clipboard (perhaps once I hit a global hotkey, or even as soon as I make the copy)?

I tried Orca, but that reads darn near everything - I'm not looking for accessibility, just to have news articles in my browser read to me.

I'm also aware of the KDE tools like KTTS, but I'm running Gnome.

(As far as I've checked, festival, espeak, etc. are just backends and don't support clipboard-monitoring functionality.)

---

### Post by .zolder on 2008-12-06
Install festival and esound-clients. To do so, follow this tutorial:
[https://help.ubuntu.com/community/TextToSpeech](https://help.ubuntu.com/community/TextToSpeech)

Install xsel:
```
sudo apt-get install xsel
```

Create new file in your home folder, call it "clipboardtospeech.sh" or something, edit it and paste the following line:
```
xsel --clipboard | festival --tts
```
Save and exit. Rightclick the file, properties, rights (is it called rights? i'm on a dutch system). Make the file executable

make a hotkey that launches the shell script:
```
/home/username/clipboardtospeech.sh
```

Other more or less usefull scripts:

Time
```
echo "It's $(date '+%-M') past $(date '+%-l')" | festival --tts
```

Info about track playing in Banshee (can be adapted to rhythmbox, just hit rhythmbox --help in the terminal)
```
banshee --query-artist | festival --tts && banshee --query-album | festival --tts && banshee --query-title | festival --tts
```

---

### Post by tgalati4 on 2008-12-06
echo "cool" | festival --tts

---

