---
title: "Unable to find file"
date: 2005-12-01
forum: General Help
---

### Post by johnmd on 2005-12-01
Yesterday I had a question re KDE/Gnome.
I was told how to download KDE.
I have to live with a dialup connection so that download took 10 hours.
I just let it run all night.
It looked like on the last file but I'm not 100% sure of that I got the following message.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kd](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kd) emultimedia-kio-plugins_3.4.3-0ubuntu1_i386.deb  Error reading from server - rea d (104 Connection reset by peer)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis sing?

Two questions.
How can I get the missing file/files/ without going through that 10 hour download again?
If I can't do that where will I find the 100 mb's of files that were downloaded so that I can delete them?

Thanks
John:( :(

---

### Post by Xian on 2005-12-01
Everything that you downloaded is cached on your system. You can issue the install command again and it will only need to try and retrieve the file(s) that it was unable to get initially. The files are stored in /var/cache/apt/archives.

Here is a link to the missing file: [kdemultimedia-kio-plugins_3.4.3](http://archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kdemultimedia-kio-plugins_3.4.3-0ubuntu1_i386.deb).

---

### Post by akiro.yamamoto on 2005-12-01
On the dated [http://www.ubuntuguide.org](http://www.ubuntuguide.org) site there was a reference so that you can backup your apt cache and also restore them...

---

### Post by linbetwin on 2005-12-01
John, I'm not very sure about this, but I think that if you try to install KDE or kubuntu-desktop again it will only download the files it didn't get the first time.

If it doesn't work, you can delete the files by emtying the cache in Synaptic. I'm not at my U machine right now, but it must be somewhere in the Preferences.

---

### Post by johnmd on 2005-12-01
Thanks guys. I just ran "sudo apt-get install kubuntu-desktop" again and it brought that missing file in.
KDE is being setup as we speak.

John  :p :p :p

---

### Post by johnmd on 2005-12-01
Just to let everyone know KDE is now running. Thanks for the help.

John  :)

---

