---
title: "How to download decoder and play MP3..."
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by imranz on 2006-01-05
I just installed Ubuntu 5.10 yesterday, but when i want to play MP3 and VCD, i have problem to play them. It's said that i don't have appropriate decoder. May i know, where can i get the decoder and where can i download XMMS for this linux?ok..thanks..

---

### Post by ardchoille on 2006-01-05
[QUOTE=imranz]I just installed Ubuntu 5.10 yesterday, but when i want to play MP3 and VCD, i have problem to play them. It's said that i don't have appropriate decoder. May i know, where can i get the decoder and where can i download XMMS for this linux?ok..thanks..[/QUOTE]
I installed xmms from the repos and it plays mp3 files just fine. I didn't have to do anything special.

---

### Post by kaamos on 2006-01-05
Look here: [https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970)

---

### Post by byen on 2006-01-05
For a simple solution i would try automatix
here is the link:
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

PS- dont forget to thank arneyboy for that. It has made life so easy.

---

### Post by jeffyb on 2006-10-28
i'm a complete noob when it comes to ubuntu can anyone give me a more encompassing method of how to install an mp3 player with having a decoder

---

### Post by Johnsie on 2006-10-28
Instructions taken from get automatix.com

Go into the terminal

Edit your sources.list by typing:

> sudo gedit /etc/apt/sources.list



Add the following to the bottom of the file:



> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) breezy main

Save the file and exit gedit

Next, type this into the terminal

> wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -


Type this in the terminal to finish off:

> sudo apt-get update
sudo apt-get install automatix


When you run automatix you will need to select Audio/Video codecs along with any other cool programs you want to install.

---

### Post by imranz on 2008-04-27
Thank you guys for all ur help :)

---

